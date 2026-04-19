# Overkill nRF Board

A modular RF communication board designed for the **Overkill system**, built around the **nRF24L01+ radio module** instead of a bare nRF24 chip for easier assembly, debugging, and reliability.

---

## Overview

This board handles the wireless communication layer of the Overkill platform using **nRF24L01+ modules**. It is designed to be:

- Easy to assemble (no RF chip-level routing pain)
- Modular (plug into the larger Overkill ecosystem)
- Hackable (all signals broken out cleanly)
- Repairable (no BGA / fine-pitch RF ICs)
- Hand-solderable (0805 components, some small parts)

It can operate:
- **Standalone** (like a typical nRF24 breakout / nRFBOX-style module)
- **Integrated** into the Overkill system as a dedicated RF subsystem

---

## Key Changes from Previous Revision

- Removed discrete nRF24 RF IC design
- Switched to **nRF24L01+ module**
- Simplified RF routing massively
- Improved reliability and development speed
- Less RF pain!

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
  - Less eye strain than 0603
  - Makes me happier to work on the board

### Interface Pins
  - JST-PH for connection to Overkill core board (data + power)
Power:
  - 3.3V regulated supply

---

## Design Philosophy

This board is intentionally:

- **Simple over compact**
- **Modular over integrated**
- **Debuggable over optimized**

The goal is fast iteration for RF experiments inside the Overkill platform.

---

## Power Notes

- Clean 3.3V rail is required for stable RF performance
- Add bulk + decoupling capacitors near module
- If using PA+LNA modules:
  - Ensure stable current supply
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
- Core controller board (SPI master/UART)
- Power distribution board
- Other sensor / compute modules

---

## Future Features

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
