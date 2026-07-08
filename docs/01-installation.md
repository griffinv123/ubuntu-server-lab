# Ubuntu Server Installation

## Goal

Install Ubuntu Server on my secondary laptop to serve as the foundation for my Linux administration homelab.

## Hardware

Laptop: Dell Latitude 5480

CPU: Intel(R) Core(TM) i5-7200U CPU @ 2.50GHz

RAM: 14Gi

Storage: 465.8G HDD

## Installation Media

Ubuntu Server 26.04 LTS

Bootable USB created using Rufus.

## Installation Process

1. Downloaded the Ubuntu Server ISO.
2. Used Rufus to create a bootable USB drive.
3. Entered BIOS and configured the laptop to boot from USB.
4. Installed Ubuntu Server as the primary operating system, replacing the original Windows 10 OS.
5. Created an administrator account.
6. Completed the installation and rebooted into Ubuntu Server.

## Verification

Verified successful installation by:

- Logging into the system
- Viewing the Ubuntu welcome message
- Confirming system information was displayed
- Reaching the command-line interface

## Screenshots

See the images in `/images/installation/`.

## Lessons Learned

Installing a server operating system differs from a desktop installation because server administration is usually performed through the command line.  Understanding the boot process and BIOS configuration is essential for deploying operating systems on physical hardware.