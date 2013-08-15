Linux Kernel config for Virtualbox
==================================

My linux kernel config for virtualbox.

Target: Debian 7

* file system: ext4
* Motherboard: default "PIIX3"
* 1 CPU

![grub boot menu]
(https://github.com/changsijay/virtualbox_linux_config/blob/master/grub_boot_menu.png?raw=true)

Compiling Steps
---------------

* download kernel tar ball from https://www.kernel.org/, say `linux-3.10.7.tar.xz`
* # apt-get install build-essential bc libncurses5-dev
* # tar xf linux-3.10.7.tar.xz
* # cp config-3.7.10 linux-3.10.7/.config
* # cd linux-3.10.7 && make oldconfig
* # make bzImage
* # cp arch/x86/boot/bzImage /boot/bzImage-3.10.7
* modify `/etc/grub.d/40_custom` to correct filename
* update-grub2

00.basic
--------

* boot into linux system and successfully login.
* choose as few kernel options as possible.
    - kernel size: 1.1M
    - memory used: 31M




