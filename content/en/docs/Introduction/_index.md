---
title: "Introduction"
linkTitle: "Introduction"
weight: 1
description: General information about the xCore development platform.
---

![core-1.1.3-diag.png](core-1.1.3-diag.png)

{{% alert title="Important" color="warning" %}}
- **Ongoing Development**: The xCore board is still in development.
- **Evolving Documentation**: This documentation is continuously being improved. There may be errors or missing steps. If you have questions, **ask on Discord**.
  {{% /alert %}}


The xCore board was born out of the [OpenMower project](https://github.com/ClemensElflein/OpenMower). The first version of the OpenMower PCB only worked with a few mower models from a single manufacturer. It quickly became clear that a more flexible solution was needed—a board that could bring together common components and make it easier to adapt the project to other mower models.

xCore does exactly this by combining all the key components you need onto a single board, making it easy to integrate low-level hardware into any robotics project. It features a high-performance STM32H723 microcontroller, a gigabit Ethernet switch, 128 MBit flash storage, an Inertial Measurement Unit (IMU), and a dedicated slot for the Raspberry Pi Compute Module 4 (CM4). All of this is packed into a compact board with a SODIMM connector, ready to fit into any custom project or robotics system.

xCore and [xbot-framework](https://github.com/clemenselflein/xbot_framework) make a great team, offering everything you need to kickstart your robotics projects with less hassle and more focus on what matters most.


## Key Features

1. **High-Performance Microcontroller**: The STM32H723 MCU brings high computing power, real-time control, and low-level interfacing capabilities, making it ideal for complex robotics applications.

2. **Raspberry Pi CM4 Compatibility**: The dedicated CM4 mount combines the power of the Raspberry Pi ecosystem with the flexibility of xCore, enabling rich processing capabilities, Linux-based software development, and access to an extensive library of drivers and tools.

3. **Easy Integration with SODIMM Connector**: The SODIMM connector allows xCore to be effortlessly connected to custom carrier boards with cheap off-the shelf connectors. This brings all the benefits of the platform directly into your project.

4. **Seamless Networking**: The integrated gigabit Ethernet switch ensures fast and reliable communication between components, supporting advanced networking requirements and distributed control architectures.

5. **IMU Integration**: An integrated IMU delivers precise motion sensing and orientation tracking, essential for navigation, stabilization, and control in robotics.

6. **Flash Storage**: An integrated 128 Mbit flash storage allows you to store configuration data or sound files directly on the board. 


## Get Started with xCore

Getting started with xCore is easy. Explore the documentation, connect the board to your custom project, and experience how xCore can streamline your robotics development. Whether you're building autonomous mowers, or any other advanced robotics application, xCore provides the foundation you need to succeed.
