---
title: "Building STM32 Firmware"
linkTitle: "Building STM32 Firmware"
description: Tutorial for building the STM32 microcontroller firmware.
---

The firmware can be build on any host PC (but yet only tested on Linux machine).

### Step 1: Clone 'fw-openmower-v2' firmware repository

It's important to clone the 'fw-openmower-v2' repository including it's submodules:
```bash
sudo apt install git docker
git clone --recurse-submodules https://github.com/xtech/fw-openmower-v2.git
```

### Step 2: Compile Firmware

```bash
cd fw-openmower-v2
./build-binary.sh
```

### Step 3: Copy Compiled Firmware to Mower

Copy the compiled firmware binary (.elf format) to your (V2) mower:
```bash
scp out/openmower.elf openmower@openmower.local:"
```
The firmware should be copied to your mower where it could be uploaded to the STM32 microcontroller,
see [Flashing STM32 From CM4]({{< ref "flashing-stm32-from-cm4" >}} "Flashing STM32 From CM4").
