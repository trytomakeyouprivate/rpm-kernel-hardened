[![CI](https://github.com/d4rklynk/kernel-hardened/actions/workflows/kernel-hardened.yml/badge.svg)](https://github.com/d4rklynk/kernel-hardened/actions/workflows/kernel-hardened.yml)

[![Copr build status](https://copr.fedorainfracloud.org/coprs/samsepi0l/HardHatOS/package/kernel-hardened/status_image/last_build.png)](https://copr.fedorainfracloud.org/coprs/samsepi0l/HardHatOS/package/kernel-hardened/)

# kernel-hardened

## About
This repository tracks the hardened Linux kernel from the Arch Linux repositories ([link](https://archlinux.org/packages/extra/x86_64/linux-hardened)). This is performed using GitHub's continuous integration, where the `ci-kernel-hardened.py` script is ran every 24 hours to check for new updates. If there are any, then the `kernel-hardened.spec` file is automatically updated, triggering the SolidCore COPR repository ([link](https://copr.fedorainfracloud.org/coprs/samsepi0l/HardHatOS)) to automatically start the build process for the latest version of Fedora Linux.

*N.B: This repo exists as the original maintainer doesn't want to continue the project. This Copr exists in a bid to keep SolidCore's packages under one banner.*

## Instructions
All commands will need to be entered with high privileges (`sudo -i`).

1. Enable the SolidCore Copr repository: `dnf copr enable samsepi0l/HardHatOS`
  
2. Update the cache: `dnf update`
  
3. Install the package: `dnf install coreos-kernel-hardened`

## Known Issues
- If you boot into the hardened kernel at least once then the next time you boot into the vanilla Fedora kernel you will have to wait for SELinux to perform a full system relabel. Once the relabel is complete the system will reboot one last time, so make sure you choose the vanilla kernel again to avoid having to go through this process.
