\# Phase 2 – Implementation (Genomförande)



\## Overview

This phase focused on extracting the Hetzner cloud server backup and preparing it for local virtualization. The goal was to convert a cloud-bound system into a portable disk image usable in VMware.



\---



\## Steps Performed



\### 1. SSH Access \& Backup Preparation

\- Connected to Hetzner server using provided SSH credentials

\- Verified root access to system

\- Identified system disk and storage layout



\### 2. Disk Imaging

\- Created raw disk image of the server

\- Compressed backup using gzip format

\- Downloaded image to local machine



\### 3. Local Environment Setup

\- Installed VMware Workstation

\- Created Ubuntu 24.04 virtual machine

\- Allocated 80GB virtual disk and sufficient RAM/CPU



\### 4. Image Handling Attempts

\- Attempted conversion of raw image using qemu-img

\- Investigated compatibility with VMware disk formats (VMDK)

\- Encountered performance and compatibility limitations



\---



\## Problems Encountered



\### Problem 1: Large disk image handling

\- Raw backup was extremely large (\~40GB)

\- Caused storage pressure and slow processing



\### Solution:

\- Used compressed format and local storage optimization



\---



\### Problem 2: WSL errors during conversion

\- qemu-img operations failed in WSL environment

\- Bus errors and I/O issues occurred



\### Solution:

\- Shifted workflow to VMware-based environment instead of WSL



\---



\### Problem 3: VMware compatibility issues

\- Direct conversion of raw disk not fully stable

\- Boot issues expected due to cloud-init and GRUB differences



\### Solution:

\- Planned post-boot repair strategy in Phase 3



\---



\## Outcome

A full raw disk image was successfully extracted and stored locally. The environment was prepared for virtualization testing in VMware.

