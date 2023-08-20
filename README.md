[![CI](https://github.com/solidc0re/rpm-kernel-hardened/actions/workflows/rpm-kernel-hardened.yml/badge.svg)](https://github.com/solidc0re/rpm-kernel-hardened/actions/workflows/rpm-kernel-hardened.yml)

[![Copr build status](https://copr.fedorainfracloud.org/coprs/solidcore/coreos-kernel-hardened/package/coreos-kernel-hardened/status_image/last_build.png)](https://copr.fedorainfracloud.org/coprs/solidcore/coreos-kernel-hardened/package/coreos-kernel-hardened/)

# rpm-kernel-hardened

## About
This repository tracks the hardened Linux kernel from the [Arch Linux repositories](https://archlinux.org/packages/extra/x86_64/linux-hardened). This is performed using GitHub's continuous integration, where the `ci-kernel-hardened.py` script is run every 24 hours to check for new updates. If there are any, then the `kernel-hardened.spec` file is automatically updated, triggering the [SolidCore copr repository](https://copr.fedorainfracloud.org/coprs/solidcore/coreos-kernel-hardened/) to automatically start the build process for the latest version of Fedora Linux.


## Instructions
### To install on Fedora CoreOS/Silverblue/Kinoite/etc.

`rpm-ostree override replace --experimental --from repo=copr:copr.fedorainfracloud.org:solidcore:coreos-kernel-hardened`


### To install on Fedora Server/Workstation:

Enable the Hard Hat Copr repository: `dnf copr enable solidcore/coreos-kernel-hardened`

Update the cache: `dnf update`

Install the package: `dnf install coreos-kernel-hardened`


## Known Issues
- If you boot into the hardened kernel at least once then the next time you boot into the vanilla Fedora kernel you will have to wait for SELinux to perform a full system relabel. Once the relabel is complete the system will reboot one last time, so make sure you choose the vanilla kernel again to avoid having to go through this process.
- Flatpaks dont work: ([Arch Wiki entry](https://wiki.archlinux.org/title/Flatpak#Troubleshooting)). The linux-hardened kernel sets `kernel.unprivileged_userns_clone` to 0, so only privileged users can create new user namespaces. One method to fix this is to install `bubblewrap-suid`. This package provides a version of `bwrap(1)` with the setuid bit enabled, allowing bubblewrap elevate itself and create new namespaces. 

## Acknowledgements
Thanks to the team at [GrapheneOS](https://github.com/GrapheneOS/linux-hardened) for starting this project and the team at Arch Linux for [building on and maintaining it](https://github.com/anthraxx/linux-hardened). Huge thanks to the developer of [HardHatOS](https://github.com/HardHatOS) for creating the original repo and python scripts for creating the RPM builds, and for [d4rklynk](https://github.com/d4rklynk) for keeping it going.
