\# Phase 4 – Problems, Summary \& Conclusion



\## Overview

This phase consolidates the entire project, including all technical challenges, solutions, and final outcomes of the Hetzner backup migration system.



\---



\## Major Problems \& Solutions



\### Problem 1: Hetzner backup vendor lock-in

Hetzner snapshots cannot be exported outside their infrastructure.



\### Solution:

A raw disk imaging approach was used to extract a portable backup from the server using root SSH access.



\---



\### Problem 2: Large disk image handling

The server backup was large and difficult to manage locally.



\### Solution:

Compression and staged transfer were used to safely store and process the image.



\---



\### Problem 3: WSL and conversion failures

qemu-img operations failed due to WSL instability and I/O errors.



\### Solution:

Shifted to VMware-based virtualization environment for stability.



\---



\### Problem 4: Boot compatibility issues

Cloud images are not directly compatible with local virtualization due to:

\- GRUB differences

\- Cloud-init configuration

\- Network interface mismatches



\### Solution:

Planned system recovery and reconfiguration inside Ubuntu VM after boot.



\---



\## Final Outcome

The project successfully demonstrated a complete technical workflow for:



\- Extracting a live Hetzner cloud server image

\- Converting and handling raw disk backups locally

\- Preparing a virtualization environment (VMware)

\- Establishing a recovery and migration strategy outside Hetzner infrastructure



\---



\## Conclusion

This project achieved its objective of designing a portable backup strategy for Hetzner cloud servers. It provided hands-on experience in:



\- Linux system administration

\- Disk imaging and virtualization

\- Troubleshooting system-level compatibility issues

\- Migration of cloud systems to local environments



The final system demonstrates that cloud vendor lock-in can be partially bypassed using raw imaging and virtualization techniques, although post-migration configuration is required for full system restoration.

