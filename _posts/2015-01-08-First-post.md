---
layout: post
title: First post
---

# Compiling linux Red Pitaya

1) Download Xilinx linux sources, in a folder Xilinx

```sh
git clone git@github.com:Xilinx/linux-xlnx.git
git clone git@github.com:Xilinx/u-boot-xlnx.git
```

2) From the RedPitaya master folder, copy the file: 
`/OS/linux/config/rp_defconfig` and paste it in the folder `Xilinx/linux-xlnx/arch/arm/configs`

3) Install the following tools

```sh
sudo apt-get install u-boot-tools
sudo apt-get install libncurses5-dev
```

4) In command line, from `Xilinx/linux-xlnx/` type

```sh
make ARCH=arm rp_defconfig
make ARCH=arm menuconfig
make ARCH=arm CROSS_COMPILE=arm-linux-gnueabi- UIMAGE_LOADADDR=0x8000 uImage
```

5) To use bootgen

```sh
source /opt/Xilinx/14.7/ISE_DS/settings64.sh
bootgen -image boot.bif -o i boot.bin
```
