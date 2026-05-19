\# Phase 1 — Research



\*\*Project:\*\* Hetzner Cloud Server Alienable Backup

\*\*Target server:\*\* `wordpress.multinomial.se` (Ubuntu 24.04, WordPress, root via SSH)

\*\*Goal:\*\* Produce a downloadable backup of a Hetzner Cloud Server that can be restored on a local VirtualBox VM with only minor post-restore configuration adjustments.



\---



\## 1. Problem statement



Hetzner Cloud offers two built-in backup mechanisms — automated daily \*\*Backups\*\* and on-demand \*\*Snapshots\*\* — but both are locked to the Hetzner platform. There is no official way to export a snapshot as a downloadable file, which creates vendor lock-in for disaster recovery and migration scenarios.



The task is to design a procedure that:



1\. Runs from the running server's root account (no Hetzner web-console snapshot required).

2\. Produces a single downloadable artifact (image file, archive, or rescue ISO + data).

3\. Can be restored on a Linux VM outside Hetzner — primary target: VirtualBox on a laptop.

4\. After restore, the hosted software (WordPress + LAMP stack) must still work after only minor adjustments (UUIDs, hostnames, network interface names, possibly domain/TLS).



\## 2. Why Hetzner's built-in backups are not enough



\- Hetzner Backups and Snapshots can only be restored to a \*\*new Hetzner Cloud Server in the same project\*\*. They are not exposed as downloadable files via API or console.

\- Community evidence confirms this is a long-standing limitation users have tried to work around (Hannes Enjoys blog, Reddit r/hetzner thread).

\- Hetzner's konsoleH product has a separate Backup feature for shared hosting, but it does not apply to Cloud Servers and still does not expose downloadable images.



\## 3. Solution landscape — three viable approaches



\### Approach A — Block-level disk image with `dd` (+ compression) over SSH



The classic "copy the whole disk byte by byte" method, documented in the Hannes Enjoys blog post referenced in the task brief:ssh root@SERVERIP "dd if=/dev/sda bs=32M status=progress | gzip -" | dd of=server.img.gz bs=32M



Then convert the raw image to VirtualBox format:gunzip server.img.gz

qemu-img convert -f raw -O vdi server.img server.vdi



\*\*Pros\*\*

\- No extra software needed beyond `dd`, `gzip`/`pigz`, and `ssh` — all present in Ubuntu 24.04.

\- Captures everything: bootloader, partition table, all filesystems. Easiest to make bootable.

\- Easy to demonstrate end-to-end on video.



\*\*Cons\*\*

\- Must image the \*\*entire device\*\* (`/dev/sda`), not just `/dev/sda1`. The Hannes blog comments explicitly warn: imaging only the partition will not boot in VirtualBox.

\- Should be done with the filesystem \*\*quiesced\*\* — either with the WordPress stack stopped or, ideally, from the \*\*Hetzner Rescue System\*\* so the disk is not mounted live.

\- File size equals full disk size even if only part is used.



\### Approach B — Filesystem-level backup with `rsync`/`tar` + fresh VM



Install a clean Ubuntu 24.04 in VirtualBox, then `rsync` the rootfs from the Hetzner server into it. Fix `/etc/fstab`, regenerate initramfs, reinstall GRUB.



\*\*Pros\*\*

\- Smaller backup (only actual files).

\- Decoupled from disk layout — flexible target disk size.



\*\*Cons\*\*

\- More manual work on the restore side.

\- Requires careful exclusion of `/dev`, `/proc`, `/sys`, `/tmp` and a `mysqldump` for the database.



\### Approach C — Relax-and-Recover (ReaR)



ReaR is the de-facto standard Linux bare-metal disaster recovery framework. It produces a \*\*bootable rescue ISO\*\* and a separate \*\*data archive\*\*. Recovery: boot the ISO on the target, run `rear recover`, ReaR recreates the partition layout, restores data, and reinstalls the bootloader.



\*\*Pros\*\*

\- Built specifically for migration to different hardware.

\- Available as an Ubuntu package: `apt install rear`.



\*\*Cons\*\*

\- More configuration up-front than `dd`.

\- Known limitations when migrating between hypervisors — may need extra kernel modules in the rescue image.



\### Side-by-side comparison



| Criterion | A: dd image | B: rsync rebuild | C: ReaR |

|---|---|---|---|

| Effort to set up | Low | Medium | Medium |

| Effort to restore | Low | High | Low |

| Image size | Full disk | Used data only | Used data + ISO |

| Risk on live server | High (use rescue mode) | Medium | Low |

| Bootability on VirtualBox | Good | Manual GRUB work | Designed for this |

| Suitable for demo video | Excellent | Good | Excellent |



\## 4. Recommended path



\*\*Primary method:\*\* Approach A (`dd` over SSH from Hetzner Rescue Mode).



\*\*Reasoning:\*\*

\- Approach A is the most direct demonstration of the principle and easy to explain step-by-step on video.

\- Running it from Hetzner Rescue Mode removes the consistency problem.

\- It matches the existing community references provided in the task brief.



\## 5. Tools selected



| Tool | Role | Reason |

|---|---|---|

| Hetzner Rescue System (Linux64) | Boot environment during backup | Quiesces the disk, gives clean dd source, free, official Hetzner feature |

| dd | Block-level disk reader | Universal, in coreutils, simple |

| pigz | Compression on the server | \~2x faster than gzip on multi-core CPUs |

| ssh + key auth | Transport | Encrypted, retryable with rsync if SSH drops |

| qemu-img (locally) | Format conversion raw to VDI | Standard tool, cross-platform |

| VBoxManage (locally) | Alternative converter + VM creation | Ships with VirtualBox |

| VirtualBox 7.x | Restore target | Required by task brief |



\## 6. Known risks and mitigations



| Risk | Mitigation |

|---|---|

| Live dd on running MySQL produces inconsistent image | Use Hetzner Rescue Mode before imaging |

| /etc/fstab UUIDs do not match after restore | qemu-img convert preserves UUIDs in most cases. If GRUB fails, boot Ubuntu Live ISO in VirtualBox, chroot, run update-grub and update-initramfs -u |

| GRUB fails to boot in VirtualBox | Boot Live ISO, chroot, grub-install /dev/sda + update-grub |

| Network interface renamed (eth0 to enp0s3) | Edit netplan config in /etc/netplan/ to use the new interface name |

| Image too large to download | pigz for compression; resume with rsync --partial if SSH drops |

| WordPress site URL hardcoded to wordpress.multinomial.se | Two options: edit wp\_options table, or add hosts-file entry on host pointing at VM IP |

| TLS certificates will not validate in VM | Acceptable for demo. Use plain HTTP, or regenerate self-signed cert |



\## 7. Phase-1 deliverables checklist



\- \[x] Problem statement and Hetzner limitation documented

\- \[x] Three candidate approaches identified and compared

\- \[x] Primary method selected with reasoning

\- \[x] Tool list with justification

\- \[x] Risk register with mitigations

\- \[ ] \*(Phase 2)\* Backup script for Approach A

\- \[ ] \*(Phase 3)\* Restore procedure document for VirtualBox



\---



\*\*Next step → Phase 2 (Implementation):\*\* Amadeus and Member B will execute the backup procedure against `wordpress.multinomial.se` and produce the downloaded artifact.

