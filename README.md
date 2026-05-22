# ATmega328-P USB-C Devboard

Custom ATmega328-P-based development board for embedded systems, Arduino-style prototyping, and hardware debugging.

## Images

Add board renders or exported screenshots here when available.

### Front

![Front](image/front.png)

### Back

![Back](image/back.png)

### PCB

![PCB](image/pcb.png)


### Schematic


![Schematic](image/schema.png)

---

## Features

- ATmega328-P Microcontroller
- USB-C Support
- CH340G USB-to-UART Serial Interface
- Arduino-Style GPIO Breakout
- Digital Pins `0-13`
- Analog Pins `A0-A5`
- 5 V Regulation with L7805
- Reset Button with Auto-Reset Support
- Custom PCB Design in KiCad

---

## Repository Structure

```text
Devboard/
|
├── Devboard-backups/
├── grbr/
├── BOM.csv
├── Devboard.kicad_pcb
├── Devboard.kicad_prl
├── Devboard.kicad_pro
├── Devboard.kicad_sch
└── README.md
```

---

## Files

- `Devboard.kicad_pro` -> KiCad project file
- `Devboard.kicad_sch` -> Schematic design
- `Devboard.kicad_pcb` -> PCB layout
- `Devboard.kicad_prl` -> KiCad project local settings
- `BOM.csv` -> Bill of materials
- `grbr/` -> Gerber manufacturing files
- `grbr/Devboard.zip` -> Exported Gerber archive
- `Devboard-backups/` -> KiCad backup files

---

## Board Details

- Microcontroller: `ATmega328-P`
- USB Serial: `CH340G`
- Main Clock: `16 MHz`
- USB Serial Clock: `12 MHz`
- Input Power: USB-C or `VIN`
- Regulated Rail: `5 V`
- Recommended `VIN`: `7-12 V`

---

## Programming

After installing an Arduino-compatible bootloader, the board can be programmed through USB serial.

Typical Arduino IDE settings:

- Board: Arduino Uno
- Processor: ATmega328P
- Clock: 16 MHz
- Port: CH340 serial port

If the ATmega328-P is blank, burn the bootloader first using an ISP programmer.

---

## Author

Created by [AYUSH-pro-grammer](https://github.com/AYUSH-pro-grammer)
