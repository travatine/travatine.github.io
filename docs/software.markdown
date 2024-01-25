---
layout: default
title: Software
permalink: /software/
---

## Proxmox setup notes

The following are a summary of [https://www.proxmox.com/en/proxmox-virtual-environment/get-started](https://www.proxmox.com/en/proxmox-virtual-environment/get-started) .

### Get the Proxmox VE ISO Installer

Go to [https://www.proxmox.com/en/downloads/proxmox-virtual-environment/iso](https://www.proxmox.com/en/downloads/proxmox-virtual-environment/iso)

Download the latest version of the ISO using the HTTP download option, for example

    wget https://enterprise.proxmox.com/iso/proxmox-ve_8.1-1.iso

### Make a bootable USB from the ISO

Copy the ISO to USB using a tool such as "dd" or if on Chrome OS the "Chromebook Recovery Utility" can be used.

#### Copying with 'dd'

    sudo dd if=./proxmox-ve_8.1-1.iso of=/dev/sdb  bs=8M status=progress 
    eject /dev/sdb

#### Copying with Chromebook Recovery Utility

On chrome os, linux containers do not have direct access to usb devices, so instead the Chromebook recovery utility can be used.

Firstly rename the iso file - appending ".bin" to the file name, i.e. 

    proxmox-ve_8.1-1.iso.bin

- Open Chrome
- Choose Extentions > Chromebook Recovery utility
- Click "Cog" > Use Local Image
- Select the iso file that was renamed above, and write to the usb drive

### Target System Requirements

- Two SSDs of the same capacity
  - A mixture of SATA / PCI NVME is ok but will result in worse performance
- CPU must be x86_64 and support VT-d / VT-x or equivilent
- RAM as must as the system supports , for example 64 GB or more is good

### Setting up the Target System

- Ensure any existing data is removed from the system.
- Poweroff the target system
- Enter the UEFI / BIOS & Enable Secure Boot.
- Ensure PXE boot is turned off
- Ensure turbo boost & VT-D  & CT-X are enabled.
- If applicable, set the onboard graphics memory allocation to the maximum value allowed.
- Ensure all the expected RAM and storage devices are detected in BIOS / UEFI
- Save Changes and power off

### DNS / IP Address Requirements

TODO

### Boot from the USB

- Insert the Proxmox Installer USB
- Power on the machine
- If needed, press the required Keyboard key to enter the uefi boot menu
- Boot from the USB

### Install Proxmox

The ket part is to set the installation disk to ZFS Raid1 to ensure that the install & VMs are mirrored, so loss of one drive is less likely to result in system failure.

### Setting up valid SSL Certificates
