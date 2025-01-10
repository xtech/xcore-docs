---
title: "Meaning of the LEDs"
linkTitle: "Meaning of the LEDs"
resources:
- src: "**.jpg"

---

{{< imgproc leds Resize 800x />}}

The meaning of the Raspberry Pi LEDs are public known. If not, please ask your preferred search engine.

Following a list of the current known/implemented xCore LED meanings:

| Left "Info" LED             | Right "Heartbeat" LED                 | Meaning
|:---------------------------:|:-------------------------------------:|---------
| On                          |                                       | IP assigned?
| Blink<br>(~1Hz)             |                                       | TODO
| Quick flash<br>(>=10Hz)     |                                       | TODO
|                             | 2 blue quick flashes<br>(continuous)  | No App (OpenMower) firmware found?
|                             | 2 green quick flashes<br>(continuous) | App (OpenMower) firmware up and alive?
|                             | red                                   | TODO
