A custom 81-key mechanical keyboard designed from the ground up, featuring dual rotary encoders, an integrated status display, and fully custom PCB architecture.

![Keyboard Render](images/render.png)

---

## Overview

Project Atlas is a custom mechanical keyboard built to explore PCB design, embedded systems, firmware development, and industrial design.

Unlike off-the-shelf keyboards, every major component is designed specifically for this project, including:

- Custom PCB
- Custom matrix routing
- RP2040-based controller
- Dual rotary encoders
- Integrated display system
- Custom enclosure
- QMK/Vial firmware support

---

## Features

### 81-Key Layout
Compact productivity-focused layout that retains function keys and navigation controls while minimizing desk space.

### Dual Rotary Encoders
Two programmable rotary encoders for:

- Volume control
- Brightness adjustment
- Timeline scrubbing
- Application-specific shortcuts

### Integrated Display
Dedicated display module for:

- Time and date
- Layer indicators
- System information
- Media status
- Custom animations

### RP2040 Powered
Powered by the Raspberry Pi RP2040 microcontroller.

Features:
- Dual-core ARM Cortex-M0+
- USB-C connectivity
- High GPIO count
- QMK compatibility

---

## Hardware Specifications

| Component | Specification |
|------------|---------------|
| MCU | RP2040 |
| Layout | 81 Keys |
| Switch Type | MX Compatible |
| Encoders | 2 Rotary Encoders |
| Display | OLED/TFT |
| Connection | USB-C |
| PCB | Custom Designed |
| Firmware | QMK / Vial |

---

## PCB Architecture

### Matrix Design

The keyboard uses a diode-protected matrix architecture.

- 81 switches
- 81 diodes
- Row-column scanning
- N-Key Rollover support

### Electrical Features

- USB-C interface
- ESD protection
- Hardware reset circuit
- Encoder support
- Display interface
- Expansion headers

---

## Design Goals

### Engineering Goals

- Learn professional PCB design workflows
- Develop custom keyboard firmware
- Implement display integration
- Optimize matrix routing
- Create a manufacturable design

### User Experience Goals

- Clean industrial design
- Comfortable typing experience
- Fast access to media controls
- Useful secondary display
- Easy firmware customization

---

## Development Process

### Phase 1
- [x] Layout design
- [x] Industrial design concepts
- [x] Component selection

### Phase 2
- [ ] PCB schematic
- [ ] Matrix routing
- [ ] Display integration
- [ ] Encoder implementation

### Phase 3
- [ ] PCB manufacturing
- [ ] Assembly
- [ ] Firmware development

### Phase 4
- [ ] Testing
- [ ] Case manufacturing
- [ ] Final revisions

---

## Software

Planned firmware features:

- Multiple layers
- Macro support
- Encoder actions
- Display widgets
- Custom animations
- VIA/Vial compatibility

---

## Gallery

### Initial Concept

![Concept Render](images/concept.png)

---

## Future Improvements

- Wireless support
- Battery management system
- RGB implementation
- Hall-effect switch support
- Custom keycap set

---

## License

MIT License
