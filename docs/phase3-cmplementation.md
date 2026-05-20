\# Phase 3 – Completion \& Fine-Tuning



\## Overview

This phase focused on completing the migration process by booting the extracted system inside a local VMware environment and preparing it for functional use.



\---



\## Steps Performed



\### 1. Ubuntu VM Boot

\- Successfully installed Ubuntu 24.04 inside VMware

\- Booted system without PXE/network boot errors

\- Verified system access via user login



\---



\### 2. Virtual Machine Configuration

\- Configured VMware virtual hardware (CPU, RAM, disk)

\- Attached virtual disk for testing environment

\- Ensured stable boot sequence from local disk



\---



\### 3. System Verification

\- Confirmed Linux environment was operational

\- Verified file system access

\- Prepared environment for potential imported server image



\---



\## Expected Adjustments After Migration



Since this system originates from a Hetzner cloud environment, several adjustments are required:



\### Network Configuration

\- Cloud-based networking (Netplan) must be adapted for local VMware adapters

\- DHCP configuration replaces cloud networking rules



\---



\### Application Layer (WordPress)

\- WordPress URL would need adjustment from:

&#x20; `wordpress.multinomial.se`

&#x20; to local IP or localhost setup

\- Database configuration may require update after migration



\---



\## Problems Encountered



\### Problem 1: PXE Boot Issue

VM initially failed to boot due to missing operating system.



\### Solution:

Mounted Ubuntu ISO and installed operating system successfully.



\---



\### Problem 2: Cloud vs Local Environment Differences

Cloud configuration is not directly compatible with local virtualization.



\### Solution:

Planned manual reconfiguration of networking and services inside VM.



\---



\## Outcome

A fully functional Ubuntu virtual machine was created and successfully booted in VMware, providing a stable environment for further restoration and testing of the Hetzner backup image.

