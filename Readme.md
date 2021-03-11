Device Tree Blob Overlay Configuration File System Kernel Module Debian Package
====================================================================================

Overview
------------------------------------------------------------------------------------

### Introduction

This is a repository for making dtbocfg kernel module debian package.

dtbocfg is Device Tree Blob Overlay ConFiGuration file system.

For details of dtbocfg, please refer to following URL.

  * https://github.com/ikwzm/dtbocfg


Build Debian Package
------------------------------------------------------------------------------------

### Download repository

```console
shell$ git clone --recursive --depth=1 -b v0.0.9 git://github.com/ikwzm/dtbocfg-kmod-dpkg
shell$ cd dtbocfg-kmod-dpkg
```

### Cross Compile

#### Parameters

| Parameter Name | Description              | Default Value                                                    |
|----------------|--------------------------|------------------------------------------------------------------|
| kernel_release | Kernel Release Name      | $(shell uname -r)                                                |
| arch           | Architecture Name        | $(shell uname -m \| sed -e s/arm.\*/arm/ -e s/aarch64.\*/arm64/) |
| deb_arch       | Debian Architecture Name | $(shell dpkg --print-architecture)                               |
| kernel_src_dir | Kernel Source Directory  | /lib/modules/$(kernel_release)/build                             |


```console
shell$ sudo debian/rules arch=arm deb_arch=armhf kernel_release=5.4.59-armv7-fpga kernel_src_dir=/usr/src/linux-5.4.59-armv7-fpga binary
    :
    :
    :
shell$ file ../dtbocfg-5.4.59-armv7-fpga_0.0.9-1_armhf.deb
../dtbocfg-5.4.59-armv7-fpga_0.0.9-1_armhf.deb: Debian binary package (format 2.0)
```

### Self Compile

```console
shell$ sudo debian/rules binary
    :
    :
    :
shell$ file ../dtbocfg-5.4.59-armv7-fpga_0.0.9-1_armhf.deb
../dtbocfg-5.4.59-armv7-fpga_0.0.9-1_armhf.deb: Debian binary package (format 2.0)
```

