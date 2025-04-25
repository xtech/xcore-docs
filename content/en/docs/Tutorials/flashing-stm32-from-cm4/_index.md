---
title: "Flashing STM32 From CM4"
linkTitle: "Flashing STM32 From CM4"
description: Tutorial for flashing the STM32 microcontroller from the Raspberry Pi CM4.
---

In order to use the Raspberry Pi CM4 to upload firmware to the STM32, we need a custom version of OpenOCD which can use
the CM4's GPIOs to connect to the STM32's SWD interface.

### Step 1: Building OpenOCD
Execute the following commands in order to install the dependencies, build and install OpenOCD:
```bash
sudo apt install autoconf automake build-essential curl libftdi-dev libtool libusb-1.0-0-dev git pkg-config rpi.gpio-common texinfo
git clone https://github.com/raspberrypi/openocd.git --recursive
cd openocd
./bootstrap
./configure --enable-ftdi --enable-sysfsgpio --enable-bcm2835gpio
make -j$(nproc)
sudo make install
```

### Step 2: Get the OpenOCD Configuration
Fetch the configuration and install it globally for OpenOCD to find it:
```bash
sudo curl -o /usr/local/share/openocd/scripts/interface/xcore.cfg https://core.x-tech.online/downloads/openocd-xcore.cfg
```

### Step 3: Upload a binary
Get a binary (.elf format) and upload it to the STM32 like this:
```bash
openocd -f interface/xcore.cfg -f target/stm32h7x.cfg -c "program your-binary.elf verify reset exit"
```
The firmware should be uploaded and the program should be running.


### Debugging via remote GDB
In order to debug the program on your xCore board, run the following command:
```bash
openocd -f interface/xcore.cfg -f target/stm32h7x.cfg -c "bindto 0.0.0.0"
```

Then connect your favorite IDE to port 3333 to upload and debug using GDB
