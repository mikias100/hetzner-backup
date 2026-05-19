# VMware Environment Setup

## Member Role
Environment Specialist & Video Producer

## Objective
Prepare a local VMware restoration environment capable of booting and validating a migrated Hetzner Ubuntu 24.04 server image.

## Local Environment
Host OS: Ubuntu Linux  
Virtualization Platform: VMware Workstation

## Installed Tools
- qemu-img
- gzip
- git
- wget
- curl
- SSH utilities

## Planned Workflow
1. Receive compressed raw backup image from Hetzner server
2. Decompress image using gunzip
3. Convert RAW disk image into VMware-compatible VMDK format
4. Create and configure VMware virtual machine
5. Attach converted virtual disk
6. Troubleshoot bootloader/network issues
7. Validate WordPress functionality locally

## Expected Technical Challenges
- GRUB bootloader mismatch
- Cloud-init configuration conflicts
- Netplan interface mismatch
- Storage controller incompatibility
- WordPress URL/database adjustments
