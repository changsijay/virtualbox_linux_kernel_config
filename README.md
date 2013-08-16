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

basic
-----

* boot into linux system and successfully login.
* choose as few kernel options as possible.

Result:

    - kernel size: 1.1M
    - memory used: 31M


stage1
------

Enabled below items:

* swap
* kernel modules
* ACPI
* High Precision Event Timer
* executable script (or many init scripts will failed to execute)
* network card driver (e1000)
* tcp/ip

Result:

    - kernel size: 1.3M
    - memory used: 38M
    
Moreover, remove vbox related package that not need:

``apt-get remove --purge virtualbox-guest-dkms virtualbox-guest-utils virtualbox-guest-x11 virtualbox-ose-guest-x11``

Build steps:

```bash
make bzImage modules && \
rm -rf /lib/modules/3.10.7.vbox-stage1 && \
make modules_install && \
cp arch/x86/boot/bzImage /boot/bzImage-3.10.7-stage1
```

stage2
------

remove some not need packages



