# Archsible
[![Travis Build Status](https://travis-ci.org/DasFranck/Archsible.svg?branch=master)](https://travis-ci.org/DasFranck/Archsible)

This is an ansible deployment playbook used for setup my archlinux workstations.  
This playbook is tested via Travis-CI using a docker container without aur flagged steps, the Dockerfile is in the travis folder.

If you are looking for my dotfiles, [it's here](https://github.com/DasFranck/DasDotFiles).

### Some example commands
- Launch ansible playbook for laptop  
`ansible-playbook -v ./playbook.yml -i ./localhost`

- Launch ansible playbook for desktop  
`ansible-playbook -v ./playbook.yml -i ./localhost --skip-tags "laptop"`

- Launch ansible playbook for desktop without aur  
`ansible-playbook -v ./playbook.yml -i ./localhost --skip-tags "laptop,aur"` 

### Quick start up ArchLinux
The following procedure is intended for a VM but can be easily adapted for any plateform
```sh
# Insert Arch ISO and boot on it

cfdisk /dev/sda

parted /dev/sda set 1 bios_grub on

mkfs.ext4 /dev/sda1
mkfs.ext4 /dev/sda2

mount /dev/sda2 /mnt
mkdir /mnt/boot && mount /dev/sda1 /mnt/boot

pacstap /mnt base git ansible
arch-chroot /mnt
    ansible-galaxy install kewlfft.aur
    git clone https://github.com/dasfranck/archsible
    cd archsible
    ansible-playbook -v ./playbook.yml -i ./localhost
```
