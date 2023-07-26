[![CI](https://github.com/SolidC0re/coreos-kernel-hardened/actions/workflows/kernel-hardened.yml/badge.svg)](https://github.com/SolidC0re/coreos-kernel-hardened/actions/workflows/kernel-hardened.yml)

[![Copr build status](https://copr.fedorainfracloud.org/coprs/solidcore/coreos-kernel-hardened/package/coreos-kernel-hardened/status_image/last_build.png)](https://copr.fedorainfracloud.org/coprs/solidcore/coreos-kernel-hardened/package/coreos-kernel-hardened/)

# coreos-kernel-hardened

## About
This repository tracks the hardened Linux kernel from the Arch Linux repositories ([link](https://archlinux.org/packages/extra/x86_64/linux-hardened)). This is performed using GitHub's continuous integration, where the `ci-kernel-hardened.py` script is run every 24 hours to check for new updates. If there are any, then the `kernel-hardened.spec` file is automatically updated, triggering the SolidCore COPR repository ([link](https://copr.fedorainfracloud.org/coprs/solidcore/coreos-kernel-hardened/)) to automatically start the build process for the latest version of Fedora Linux.

*N.B: This repo exists as the original creator doesn't want to continue the project. This Copr exists in a bid to keep SolidCore's packages under one banner.*


## Instructions
### To install on Fedora CoreOS/Silverblue/Kinoite/etc.

`rpm-ostree override replace --experimental --from repo=copr:copr.fedorainfracloud.org:solidcore:coreos-kernel-hardened`


### To install on Fedora Server/Workstation:

Enable the Hard Hat Copr repository: `dnf copr enable solidcore/coreos-kernel-hardened`

Update the cache: `dnf update`

Install the package: `dnf install coreos-kernel-hardened`


## Known Issues
- If you boot into the hardened kernel at least once then the next time you boot into the vanilla Fedora kernel you will have to wait for SELinux to perform a full system relabel. Once the relabel is complete the system will reboot one last time, so make sure you choose the vanilla kernel again to avoid having to go through this process.
