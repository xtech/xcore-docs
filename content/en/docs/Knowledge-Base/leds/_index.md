---
title: "Meaning of the LEDs"
linkTitle: "Meaning of the LEDs"
resources:
- src: "**.jpg"

---

{{< imgproc leds Resize 800x />}}

The meaning of the Raspberry Pi LEDs are publicly known. For details about those LEDs, refer to the Raspberry Pi documentation or your preferred search engine.

Following a list of the currently known/implemented xCore LED meanings:

| Left "Info" LED         | Right "Heartbeat" LED                 | Meaning |
|:-----------------------:|:-------------------------------------:|---------|
| Anything                |                                       | Controlled by the application firmware, check firmware documentation |
|                         | 2 blue quick flashes<br>(continuous)  | Bootloader mode |
|                         | 2 green quick flashes<br>(continuous) | Firmware running normally |
|                         | Off or permanently on                 | Firmware/system crashed or stuck |
|                         | Red                                   | Severe error / something went seriously wrong |
