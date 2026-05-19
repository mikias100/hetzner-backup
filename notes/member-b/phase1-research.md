# Phase 1 – Research (Pre-study)

## Information Gathering
Research was conducted on how to create portable backups from Hetzner Cloud servers, which normally only allow internal snapshot restoration.

Sources and concepts explored:
- Hetzner snapshot limitations (vendor-locked backups)
- Raw disk imaging using Linux tools (dd, gzip)
- Disk conversion utilities (qemu-img)
- Virtualization platforms (VMware Workstation)
- Boot recovery concepts (GRUB, initramfs)
- Network reconfiguration (Netplan)

## Tools Selected
The following tools were selected for the project workflow:
- qemu-img (disk conversion)
- gzip (compression handling)
- SSH (remote server access)
- VMware Workstation (local virtualization)

## Planning Approach
The planned workflow is:
1. Create raw disk image from Hetzner server
2. Compress and transfer image locally
3. Convert image into VMware-compatible format (.vmdk)
4. Create virtual machine and attach disk
5. Boot system locally and troubleshoot issues
6. Reconfigure networking and WordPress settings

## Challenges Identified
- Hetzner backups cannot be exported directly
- Bootloader (GRUB) issues expected after migration
- Network configuration differences between cloud and local VM
- Large disk image handling and conversion complexity

## Solutions Strategy
- Use raw disk imaging for portability
- Convert disk using qemu-img for VMware compatibility
- Adjust bootloader and networking after migration
- Test incrementally inside VM environment
