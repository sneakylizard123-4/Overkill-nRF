# Overkill nRF Board

A modular RF communication board designed for the **Overkill system**, built around the **nRF24L01+ radio module** instead of a bare RF IC + Amplifier. This makes the design easier to assemble, debug, and iterate while keeping it fully modular inside the Overkill ecosystem.

---

## Overview

The Overkill nRF Board handles wireless communication for the system using **nRF24L01+ modules**.

It is designed to be:

- Easy to assemble (no RF IC routing complexity)
- Modular (plugs into Overkill ecosystem)
- Hackable (all signals exposed)
- Repairable (no fine-pitch RF ICs)
- Hand-solderable (mostly 0805 components)

### Operating Modes

- **Standalone mode** → acts like a standard nRF24 breakout module
- **Integrated mode** → RF subsystem inside Overkill system

---

## Key Changes from Previous Revision

- Removed discrete nRF24 RF IC design
- Switched to **nRF24L01+ module-based design**
- Simplified RF routing significantly
- Improved reliability and build speed
- Reduced RF design complexity

---

## Hardware

### Radio

- nRF24L01+ module (SPI interface)
- Optional PA+LNA module support (with proper power handling)

### Components

- Mostly **0805 footprint components**
  - Easier soldering
  - Better availability
  - More forgiving for hand assembly

### Interface

Connection to Overkill system via **JST-PH connector**:

- 3.3V power
- Data signals

---

## Design Philosophy

This board prioritizes:

- Simplicity over compact size
- Modularity over integration
- Debuggability over RF perfection

The goal is fast iteration for RF experimentation inside the Overkill platform.

---

## Power Notes

- Requires stable **3.3V supply** or **USB power** with proper regulation
- nRF24 modules are 5V tolerant, but the esp32 is not, so 3.3V is used for the logic part of the board
- Add decoupling capacitors close to module
- PA+LNA modules may require higher current bursts during transmission, so ensure power supply can handle it

---

## PCB Design Notes

- Designed around **0805 components**
- Maintain solid ground plane under RF section
- Keep antenna area free of copper and components
- use external antennas if possible for better performance

---

## Images

All pictures and screenshots should be in the `images/` folder.

### PCB Layout

![PCB Layout](images/pcb.png)

---

### 3D Renders

Top-side render (ray-traced KiCad):
![Top Render](images/rend1.png)

Bottom-side render (ray-traced KiCad):
![Bottom Render](images/rend2.png)

---

### Schematics

schematic sheet 1:
![Schematic 1](images/sch1.png)

schematic sheet 2:
![Schematic 2](images/sch2.png)

---

### Manufacturing / Sourcing

AliExpress cart:
![AliExpress Cart](images/aliexpress.png)

LCSC sourcing carts:
![LCSC Cart 1](images/lcsc1.png)
![LCSC Cart 2](images/lcsc2.png)
![LCSC Cart 3](images/lcsc3.png)

JLCPCB cart:
![JLCPCB Cart](images/jlcpcb1.png)
![JLCPCB Specs](images/jlcpcb2.png)
or maybe PCBWay if they sponsor this project too!

---

## System Integration

The board connects into the Overkill system via JST-PH and is designed to interface with:

- Core controller board (SPI master)
- Power distribution board
- Other modular subsystems

Other parts of the system are being developed separately.

---

## Assembley and Programming
- The board can be programmed using USB
- Use PlatformIO or Arduino IDE with the appropriate settings for the ESP32 microcontroller
- Make sure to select the correct COM/TTY port when flashing
- Refer to the firmware/ directory for example code and libraries to get started with the board
- Use flux when soldering for better results, especially around the nRF24L01+ module and small components

## Bill of Materials (BOM)

A full BOM is included in the repository.

It includes:

- Component references
- Values / part numbers
- Quantities
- LCSC number

---

## Repository Structure

- bom/ - Bill of Materials (BOM) files
- blender/ - 3D models and renders
- cad/ - STEP files
- firmware/ - code for project (platformio)
- images/ - pictures and screenshots
- kicad/ - KiCad project files
- zine/ - zine page for hack club

---

## Status

- Breadboard Prototype complete
- PCB routed in KiCad
- 3D assembly done
- Ready for fabrication

---

## Notes

This revision prioritizes usability and fast iteration over RF optimization complexity. The goal is to make RF experimentation inside the Overkill system fast, modular, and actually enjoyable to play with.
