# hetzner-backup

Alienable backup procedure for Hetzner Cloud Servers — group Project



\# Hetzner Cloud Server — Alienable Backup Project



A group project to bypass Hetzner Cloud's vendor lock-in by extracting a running Linux instance as a downloadable disk image and restoring it on a local VirtualBox VM.



\*\*Target server:\*\* wordpress.multinomial.se (Ubuntu 24.04, WordPress)

\*\*Success criteria:\*\* Boot the system locally with only minimal adjustments (IP configuration, WordPress site URL).



\## Team



| Member | Role |

|---|---|

| Amadeus (Group Leader) | Lead Server Architect \& Integration Engineer |

| Member B | Environment Specialist \& Video Producer |

| Mikias (Member A) | Git Manager \& Lead Documenter |



\## Repository structure



\- `docs/` — Phase documentation in English

\- `scripts/` — Backup and conversion scripts

\- `screenshots/` — Verification screenshots



\## Project phases



1\. \*\*Phase 1 — Research:\*\* Evaluate P2V methods, define toolchain (dd, gzip, VBoxManage)

2\. \*\*Phase 2 — Implementation:\*\* Live SSH disk imaging, compressed transfer, raw-to-VDI conversion

3\. \*\*Phase 3 — Completion:\*\* Local VM boot, GRUB/Netplan fixes, WordPress URL rebinding

4\. \*\*Phase 4 — Summary \& Video:\*\* Problems-and-solutions matrix, project conclusion, English video (≥4 min)



\## Git workflow



\- Commit messages in English, imperative mood ("Add backup script", not "Added")

\- Frequent, atomic commits — one logical change per commit

\- Each phase ends with a checkpoint commit



\## Status



Phase 1 — In progress

