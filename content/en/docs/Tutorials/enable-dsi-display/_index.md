---
title: "Enable DSI Display"
linkTitle: "Enable DSI Display"
description: This guide shows you how to enable a display connected to the DSI port.
---

Connecting a display to the DSI port is easy, just follow these steps:

### Connecting the Official Raspberry Pi 7-inch Display

1. **Power off** the xCore and disconnect it from its power source.
2. Connect the official 7-inch display to the **DISP** port on the xCore board.
3. Power up the board.
4. Edit the `/boot/firmware/config.txt` file and add the following line:
   ```
   dtoverlay=vc4-kms-dsi-7inch
   ```
5. Reboot the system:
   ```bash
   sudo reboot
   ```

After rebooting, the display should be detected automatically and begin showing output. The touch function should be working as expected.
