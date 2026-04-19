# Overkill nRF Board

A modular RF communication board designed for the **Overkill system**, built around the **nRF24L01+ radio module** instead of a bare nRF24 chip for easier assembly, debugging, and reliability.

---

## Overview

This board handles the wireless communication layer of the Overkill platform using **nRF24L01+ modules**. It is designed to be:

- Easy to assemble (no RF chip-level routing pain)
- Modular (plug into the larger Overkill ecosystem)
- Hackable (all signals broken out cleanly)
- Repairable (no BGA / fine-pitch RF ICs)

It can operate:
- **Standalone** (like a typical nRF24 breakout / nRFBOX-style module)
- **Integrated** into the Overkill system as a dedicated RF subsystem

---

## Key Changes from Previous Revision

- Removed discrete nRF24 RF IC design
- Switched to **nRF24L01+ module socket/header**
- Simplified RF routing massively
- Improved reliability and development speed

---

## Hardware

### Radio
- nRF24L01+ module (standard SPI interface)
- Optional PA+LNA modules supported (with proper power design)

### Passive Components
- Mostly **0805 footprint components**
  - Easier soldering
  - Better availability
  - Good balance between size and hand-assembly friendliness

### Interface Pins
Typical SPI-based interface:

- MOSI
- MISO
- SCK
- CSN
- CE
- IRQ (optional)

Power:
- 3.3V regulated supply (IMPORTANT: nRF24 is not 5V tolerant)

---

## Design Philosophy

This board is intentionally:

- **Simple over compact**
- **Modular over integrated**
- **Debuggable over optimized**

The goal is fast iteration for RF experiments inside the Overkill platform.

---

## Power Notes

- Clean 3.3V rail is required
- Add bulk + decoupling capacitors near module
- If using PA+LNA modules:
  - Ensure stable current supply (peaks can spike hard)
  - Consider separate regulator or heavy decoupling

---

## PCB Notes

- Designed primarily for **0805 components**
- Keep RF trace from MCU → module as short as possible
- Ground plane is critical for stable RF performance
- Keep antenna area clear of copper and components

---

## Overkill Integration

This board is part of the larger **Overkill modular hardware system**.

It is designed to interface with:
- Core controller board (SPI master)
- Power distribution board
- Other sensor / compute modules

---

## Future Ideas

- Multi-radio support (multiple nRF24 modules)
- Packet sniffing mode
- Mesh networking experiments
- PA/LNA switching board variant
- Onboard RF diagnostics LEDs

---

## Status

In active development  
Prototype stage  (Working breadboard prototype!)
RF subsystem functional (module-based)
