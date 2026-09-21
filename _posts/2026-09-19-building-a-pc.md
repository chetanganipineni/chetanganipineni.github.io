---
title: "Building a PC"
date: 2026-09-19
tags: [computing, hardware]
---

I recently built a new PC which will ideally be used for hosting a local LLM. This post will detail the steps I took to assemble the PC and install Arch Linux on it.

## Assembling the PC

### Parts

Here is the list of parts I used for the build:

| Type | Part |
|---|---|
| GPU | RTX 4080 Super Founders Edition |
| CPU | AMD Ryzen 7 9700X |
| Motherboard | Gigabyte B650 Gaming X AX V2 |
| RAM | 32GB DDR5-6000 RAM |
| SSD | Samsung 990 Pro 2TB |
| CPU Cooler | Thermalright Phantom Spirit 120 SE Black |
| Case | NZXT H6 Flow Black |
| PSU | Thermaltake Toughpower GT 1000W |

Pictures of the parts:

<figure style="text-align:center; margin: 1.5rem 0;">
  <img src="/assets/images/pc_parts/part_gpu.png" alt="GPU photo" width="320">
  <figcaption>
    GPU: RTX 4080 Super Founders Edition
  </figcaption>
</figure>

<figure style="text-align:center; margin: 1.5rem 0;">
  <img src="/assets/images/pc_parts/part_cpu_box.png" alt="CPU photo" width="320">
  <figcaption>
    CPU: AMD Ryzen 7 9700X (Just the box)
  </figcaption>
</figure>

<figure style="text-align:center; margin: 1.5rem 0;">
  <img src="/assets/images/pc_parts/part_motherboard_opened.png" alt="Motherboard photo" width="320">
  <figcaption>
    Motherboard: Gigabyte B650 Gaming X AX V2
  </figcaption>
</figure>

<figure style="text-align:center; margin: 1.5rem 0;">
  <img src="/assets/images/pc_parts/part_ram_sticks.png" alt="RAM photo" width="320">
  <figcaption>
    RAM: 32GB DDR5-6000
  </figcaption>
</figure>

<figure style="text-align:center; margin: 1.5rem 0;">
  <img src="/assets/images/pc_parts/part_ssd_box.png" alt="SSD photo" width="320">
  <figcaption>
    SSD: Samsung 990 Pro 2TB
  </figcaption>
</figure>

<figure style="text-align:center; margin: 1.5rem 0;">
  <img src="/assets/images/pc_parts/part_cpu_fans_with_hooks_attached.png" alt="CPU cooler photo" width="320">
  <figcaption>
    CPU cooler: Thermalright Phantom Spirit 120 SE Black (hooks already attached)
  </figcaption>
</figure>

<figure style="text-align:center; margin: 1.5rem 0;">
  <img src="/assets/images/pc_parts/part_empty_case.png" alt="Case photo" width="320">
  <figcaption>
    Case: NZXT H6 Flow Black
  </figcaption>
</figure>

<figure style="text-align:center; margin: 1.5rem 0;">
  <img src="/assets/images/pc_parts/part_psu_and_cables.png" alt="PSU photo" width="320">
  <figcaption>
    PSU: Thermaltake Toughpower GT 1000W
  </figcaption>
</figure>

### Assembly

I started with the motherboard first by installing the CPU, CPU Fans, RAM, and the SSD.

<figure style="text-align:center; margin: 1.5rem 0;">
  <img src="/assets/images/pc_parts/install_cpu_to_motherboard_1.png" alt="cpu_motherboard" width="320">
  <figcaption>
    CPU installed into the Motherboard
  </figcaption>
</figure>

I first installed the CPU into the motherboard. There is a gold triangle on the CPU and that should line up with the carved-in triangle on the AM5 socket.

<figure style="text-align:center; margin: 1.5rem 0;">
  <img src="/assets/images/pc_parts/install_ram_to_motherboard.png" alt="ram_motherboard" width="320">
  <figcaption>
    RAM sticks installed into the Motherboard
  </figcaption>
</figure>

I then installed the RAM sticks onto the motherboard's A2 + B2 slots (the second and fourth slots away from the CPU). The RAM should just click in.

<figure style="text-align:center; margin: 1.5rem 0;">
  <img src="/assets/images/pc_parts/install_cpu_fans_to_motherboard.png" alt="ram_motherboard" width="320">
  <figcaption>
    CPU Fans installed into the Motherboard
  </figcaption>
</figure>

I then installed the CPU fans on the motherboard. The steps are little more involved here:
1. first, I put a pea-sized drop of thermal paste on the CPU
2. screw on the cooler on the AM5 socket
3. hook on the fans to the cooler
4. then connect the two fan cables to the CPU_FAN slot on the motherboard

<figure style="text-align:center; margin: 1.5rem 0;">
  <img src="/assets/images/pc_parts/install_metal_plate_above_ssd.png" alt="ram_motherboard" width="320">
  <figcaption>
    Below this metal place is the SSD slot
  </figcaption>
</figure>

The final part to install on this motherboard is the SSD. The M.2 slot resides under this metal plate. All I did is push in the SSD into this slot and screwed it in.

The motherboard is now complete! Next is to connect these parts to the case.

<figure style="text-align:center; margin: 1.5rem 0;">
  <img src="/assets/images/pc_parts/install_motherboard_to_case.png" alt="ram_motherboard" width="320">
  <figcaption>
    Motherboard screwed into the case
  </figcaption>
</figure>

I took out the panels and the windows of the case and screwed in the motherboard.

<figure style="text-align:center; margin: 1.5rem 0;">
  <img src="/assets/images/pc_parts/install_psu_to_back_of_case.png" alt="ram_motherboard" width="320">
  <figcaption>
    PSU in the back of the case
  </figcaption>
</figure>

Then in the back side of the case, I slid in the PSU and screwed it in. I also connected the following cables from the PSU to the motherboard:
1. 24-pin ATX - the main motherboard power
2. CPU/EPS 8-pin - powers the CPU
3. F_PANEL - powers the power button
4. 4-pin fan connector - powers all of the case fans. All of them are "daisy-chained" so just need one connection
5. Black USB-C connector - connects to the motherboard USB-C header

<figure style="text-align:center; margin: 1.5rem 0;">
  <img src="/assets/images/pc_parts/install_gpu_to_motherboard_with_cable.png" alt="ram_motherboard" width="320">
  <figcaption>
    GPU screwed into the Motherboard
  </figcaption>
</figure>

For the GPU, I removed a couple panels on the side of the case and insert it into the big slot on the GPU. I then plugged in the 600W power cable from the PSU.

<figure style="text-align:center; margin: 1.5rem 0;">
  <img src="/assets/images/pc_parts/finished_pc.png" alt="ram_motherboard" width="320">
  <figcaption>
    Finished PC
  </figcaption>
</figure>

The PC assembly is done! I plugged in the charger, HDMI monitor, keyboard, and turned it on and saw the UEFI setup screen.

## Setting Up Arch Linux

I mainly used the [Arch Installation Guide as my reference](https://wiki.archlinux.org/title/Installation_guide) which is really good for detailing all the commands for an easy setup. I won't list all the commands and explanations here to avoid repetition; only the ones that are tailored to my setup.

I already have set up my USB to hold the Arch ISO.

### Disk Partitioning and Formatting

Disk partitioning was slightly tricky. I wanted to keep it as simple as possible, but mutatable enough so I can add potential security features in the future:

1. [secure boot (signed UKI)](https://wiki.archlinux.org/title/Unified_Extensible_Firmware_Interface/Secure_Boot#) - only operating systems signed by a trusted private key can boot
2. [disk encryption using LUKS](https://wiki.archlinux.org/title/Data-at-rest_encryption) - provides data-at-rest encryption for storage
3. [read-only filesystem through DM-Verity](https://wiki.archlinux.org/title/Dm-verity) - storage drive integrity

For now, I just kept it simple for development purposes. Since I'm using a large drive, I can always repartition it in the future. Here is my partition layout:

*Table 1: Partition Layout*{: .table-caption}

| Mount point on the installed system | Partition | Partition type | Suggested size |
|---|---|---|---|
| `/boot` | `/dev/efi_system_partition` | EFI system partition | 1 GiB |
| `[SWAP]` | `/dev/swap_partition` | Linux swap | 16 GiB |
| `/` | `/dev/root_partition` | Linux x86-64 root (/) | Remainder of the device. ~1.8 TiB |

### Creating Partitioning

Then I used the `fdisk` utility to create these partitions:
- "n" creates new partition
- selected default partition number & initial starting sectors
- "+16G" to set the last sector in the swap partition, for example
- "+" to change the partition type (uefi, swap); note that type is just metadata and does not format partitions yet

### Formatting Partitions
```sh
mkfs.fat -F 32 /dev/nvme0n1p1
mkswap /dev/nvme0n1p2
mkfs.ext4 /dev/nvme0n1p3
```

### Mount the Filesystems

```sh
mount /dev/nvme0n1p3 /mnt
mount --mkdir /dev/nvme0n1p1 /mnt/boot
swapon /dev/nvme0n1p2

# to verify the layout
lsblk
```

### Installing the system packages

`pacstrap` is used to install Arch packages into a specified target directory, which in our case is /mnt.

![pacstrap installs packages from the Arch USB live environment into /mnt]({{ "/assets/images/pacstrap_diagram.svg" | relative_url }})
*Figure 1: After pacstrap, /mnt should be bootable*{: .table-caption}

```sh
pacstrap -K /mnt base linux linux-firmware amd-ucode network-manager sudo nano

# then to get file systems mounted at startup:
genfstab -U /mnt >> /mnt/etc/fstab
# then change root to the new system:
arch-chroot -S /mnt
```

### Additional Configurations

Not much explanation needed here.

```sh
# Set time zone to east coast
ln -sf /usr/share/zoneinfo/America/New_York /etc/localhost

# Set hardware clock on system time
hwclock --systohc

# Localization
nano /etc/locale.gen
- uncomment: en_US.UTF-8 UTF-8
locale-gen
echo "LANG=en_US.UTF-8" > /etc/locale.conf

# Network
systemctl enable NetworkManager
echo "ailabpc" > /etc/hostname

# Set Password
passwd

# Create My User
useradd -m -G wheel -S /bin/bash chetan
passwd chetan

# Enable sudo for wheel group
EDITOR=nano visudo
- uncomment: %wheel ALL=(ALL:ALL) ALL
```

### Initramfs

Initramfs stands for initial RAM file system; it's a small temporary filesystem that the linux kernel loads into RAM during boot before actual root file system is avaialable.

![Boot process: UEFI to systemd-boot to Linux Kernel to initramfs to mount real root to systemd to Arch Linux]({{ "/assets/images/boot_process_diagram.svg" | relative_url }})
*Figure 2: The Linux boot process from firmware to userspace. initramfs is the red box*{: .table-caption}

Why is it needed? it's needed to mount the root filesystem, kernel modules, user space tools, etc. The arch linux wiki also has some cool use cases such as disk decryption, and SSH server to do remote unlocking.

Literally, rootfs starts at ('/') which is ramfs. The kernel unpacks initramfs images in the order specified in boot loader

We don't have to do anything here, as initramfs already came with pacstrap. This is what we have now:

```sh
ls /boot

amd-ucode.img  EFI  initramfs-linux.img  loader  vmlinuz-linux
```

### Bootloader

Bootloader is a piece of software started by the firmware (UEFI or BIOS) for loading the kernel with wanted kernel parameters and initramfs images.
- bootmanager - presents menu of options (i.e. other efi executables)
- to successfully boot Arch, boot loader needs access to kernel & initramfs images which reside /boot

I'm using systemd-boot because it is easy to use and configure.

```sh
# install systemd-boot at the EFI system partition
bootctl install

# create loader config
nano /boot/loader/loader.conf
- default arch.conf
- timeout 5
- editor no

# create arch config
nano /boot/loader/entries/arch.conf
- title Arch Linux
- linux /vmlinuz-linux
- initrd /amd-ucode.img
- initrd /initramfs-linux.img
- options root=UUID=<ROOT_UUID> rw

# you can get the root UUID by running:
blkid /dev/nvme0n1p3
```

### Final Verification Steps

```sh
bootctl status
cat /boot/loader/loader.conf
cat /boot/loader/entries/arch.conf
cat /etc/fstab
systemcrl is-enabled NetworkManager
lsblk -f

# exit chroot
exit
umount -R /mnt
swapon -a
reboot
```

Installation should be complete!