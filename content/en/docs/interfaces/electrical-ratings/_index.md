---
title: "Electrical Ratings"
linkTitle: "Electrical Ratings"
weight: 20
description: >
  Electrical Ratings.
---
## Electrical Ratings

The xCore board is designed be powered easily.
Below are the detailed electrical specifications based on the power and logic requirements of these components.

### Power Supply

- **Input Voltage**: 5V DC  
  A 5V power supply with a minimum current rating of 3A is recommended to ensure smooth operation, even under load.
- **Power Consumption**:
    - **Idle**: 600mA @ 5V
    - **Under Load**: Up to 3A @ 5V (depending on connected peripherals and CM4 load)
- **Logic Level (I/O Pins)**: 3.3V  
  The xCore board's logic operates at 3.3V.
- **3.3V Rail Maximum Current**: 500mA  
  The 3.3V rail is suitable for low-power peripherals and provides up to 500mA.

### Electrical Ratings Table

| **Parameter**                     | **Value**   | **Unit**        | **Notes**                                                                 |
|------------------------------------|-------------|-----------------|--------------------------------------------------------------------------|
| **Input Voltage Range**            | 4.75 - 5.25 | V               | Consistent with Raspberry Pi CM4 requirements                            |
| **Recommended Power Supply**       | 5           | V               | 3A minimum current rating                                                |
| **Idle Power Consumption**         | 600         | mA @ 5V         |                                                                          |
| **Max Power Consumption**          | 3           | A @ 5V          | Under load                                                               |
| **Logic Level (I/O Pins)**         | 3.3         | V               | STM32H723 microcontroller logic level                                    |
| **Max Current per GPIO Pin**       | 8 (20 max)  | mA              | 8mA standard, 20mA max                                                   |
| **Max Current (3.3V Rail)**        | 500         | mA              |                                                                          |

