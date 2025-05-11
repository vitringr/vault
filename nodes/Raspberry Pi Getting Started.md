---
tags:
  - "article"
context:
  - "[[Raspberry Pi]]"
---

# Raspberry Pi Getting Started

Reference: [Getting Started - Raspberry Pi](https://www.raspberrypi.com/documentation/computers/getting-started.html#setting-up-your-raspberry-pi)

Article about getting started with a new Raspberry Pi.

---

## Getting Started

### Prerequisites

To get started, you need the following:

- Raspberry Pi
- Power supply
- Boot media (microSD card)

Additional accessories for direct usage:

- Display & cable for it
- Keyboard

### Power Supply

| Model                          | Recommended power supply (voltage/current) | Raspberry Pi power supply    |
| ------------------------------ | ------------------------------------------ | ---------------------------- |
| Raspberry Pi 5                 | 5V/5A, 5V/3A limits peripherals to 600mA   | 27W USB-C power supply       |
| Raspberry Pi 4 Model B         | 5V/3A                                      | 15W USB-C power supply       |
| Raspberry Pi 3 (all models)    | 5V/2.5A                                    | 12.5W Micro USB power supply |
| Raspberry Pi 2 (all models)    | 5V/2.5A                                    | 12.5W Micro USB power supply |
| Raspberry Pi 1 (all models)    | 5V/2.5A                                    | 12.5W Micro USB power supply |
| Raspberry Pi Zero (all models) | 5V/2.5A                                    | 12.5W Micro USB power supply |

Plug in the power supply into the port marked "POWER IN", "PWR IN", or "PWR".

### Boot Media

**No Storage**: Raspberry Pi models lack onboard storage, so you have to supply it.

**External Storage & OS**: You can install an operating system image on an external storage device, most commonly a microSD card.

**MicroSD**: The microSD card is always supported, and the Raspberry Pi automatically boots from it when the slot contains a card.

> [!Tip] Recommended SD Card Capacity
>
> **Minimum**: Should probably have at least `32GB` of storage for Raspberry Pi OS installations, and at least `16GB` for OS Lite.
>
> **Maximum**: The SD card should be less than `2TB`. Capacities above that may not be supported.

### Keyboard & Mouse

Use any of the USB ports to connect a keyboard or mouse.

### Display

| Model                          | Display outputs                                            |
| ------------------------------ | ---------------------------------------------------------- |
| Raspberry Pi 5                 | 2× micro HDMI                                              |
| Raspberry Pi 4 (all models)    | 2× micro HDMI, audio and composite out via 3.5mm TRRS jack |
| Raspberry Pi 3 (all models)    | HDMI, audio and composite out via 3.5mm TRRS jack          |
| Raspberry Pi 2 (all models)    | HDMI, audio and composite out via 3.5mm TRRS jack          |
| Raspberry Pi 1 Model B+        | HDMI, audio and composite out via 3.5mm TRRS jack          |
| Raspberry Pi 1 Model A+        | HDMI, audio and composite out via 3.5mm TRRS jack          |
| Raspberry Pi Zero (all models) | mini HDMI                                                  |

> [!WARNING]
> No Raspberry Pi models support video over USB-C (DisplayPort alt mode).

If your Raspberry Pi has more than one HDMI port, plug your primary monitor into the port marked `HDMI0`.

**Mini HDMI Adaptation**: Many displays don't have micro or mini HDMI ports. Use a HDMI-to-micro-HDMI cable, or some adapter for it.

### Audio

Raspberry Pi supports the following audio output:

- HDMI
- Micro HDMI
- USB
- Bluetooth

### Networking

Flagship Raspberry Pi models come with Wi-Fi and Bluetooth connectivity.

There is also an Ethernet slot.

### Install an Operating System

To use Raspberry Pi you need an operting system.

By default, Raspberry Pis check for an operating system on any SD card inserted in the SD card slot.

**Raspberry Pi Imager**: The easiest way to install an OS on an external device is to use the Raspberry Pi Imager software tool.

### Setup Your Raspberry Pi

First, unplug everything to ensure the Raspberry Pi is powered down while connecting peripherals.

Plug in the operating system container (microSD usually).

Then plug any other peripherals, such as mouse, keyboard, and monitor.

Finally, connect the power supply to the Raspberry Pi.

You should see the status LED light up when your Pi powers on.

If the Pi is connected to a display, you should see the boot screen within minutes.

### Configuration on First Boot

If you used the Raspberry Pi OS imager utility, you should be walked through a first-time setup program.

Otherwise, you can manually configure the OS settings.

That should be it for a basic start.
