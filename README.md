# ATmega328-P USB-C Devboard

An Arduino-style ATmega328-P development board with USB-C, CH340G USB serial, onboard 5 V regulation, and exposed 2.54 mm headers.


## Key Features

- **ATmega328-P** microcontroller in a DIP-28 package
- **USB-C** connector for USB 2.0 connectivity and board power
- **CH340G USB-to-UART** converter for serial upload and debugging
- **16 MHz crystal** for the ATmega328-P clock
- **12 MHz crystal** for the CH340G clock
- **L7805 5 V regulator** for external `VIN` input
- **Reset push button** with CH340G `DTR` auto-reset support
- **Arduino-style digital header** exposing pins `0-13`
- **Analog header** exposing `A0-A5`
- **Power header** with `GND`, `5V`, `3V3`, and `VIN`
- **Through-hole friendly layout** for easy soldering and debugging
- **Custom bottom silkscreen artwork** and board signature

## PCB

Designed in KiCad as a 2-layer development board. The layout keeps the USB-C and CH340G serial section near the connector, the ATmega328-P in a DIP package for easy replacement, and the power/input headers along the board edge.

### Front

<img src="assets/pcb_front.png" alt="PCB front render" width="800">

### Back

<img src="assets/pcb_back.png" alt="PCB back render" width="800">

### Source Files

| File | Description |
| --- | --- |
| `Devboard.kicad_pro` | KiCad project file |
| `Devboard.kicad_sch` | Schematic |
| `Devboard.kicad_pcb` | PCB layout |
| `BOM.csv` | Bill of materials |

## Pinout

### Digital Header `J1`

| Board Pin | ATmega328-P Pin |
| --- | --- |
| `0 / TX` | `PD0` |
| `1 / RX` | `PD1` |
| `2` | `PD2` |
| `3` | `PD3` |
| `4` | `PD4` |
| `5` | `PD5` |
| `6` | `PD6` |
| `7` | `PD7` |
| `8` | `PB0` |
| `9` | `PB1` |
| `10` | `PB2` |
| `11` | `PB3` |
| `12` | `PB4` |
| `13` | `PB5` |

### Analog Header `J2`

| Board Pin | ATmega328-P Pin |
| --- | --- |
| `A0` | `PC0` |
| `A1` | `PC1` |
| `A2` | `PC2` |
| `A3` | `PC3` |
| `A4` | `PC4` |
| `A5` | `PC5` |

### Power Header `J3`

| Board Pin | Notes |
| --- | --- |
| `GND` | Ground |
| `GND` | Ground |
| `5V` | Regulated 5 V rail |
| `5V` | Regulated 5 V rail |
| `3V3` | 3.3 V output from CH340G `V3` |
| `VIN` | External regulator input |

The board silkscreen notes that `VIN` supports `7-35 V`, with `7-12 V` recommended.

## USB Serial

The USB-C connector routes USB 2.0 data to the CH340G. The CH340G connects to the ATmega328-P hardware UART:

| CH340G | ATmega328-P |
| --- | --- |
| `TXD` | `PD0 / RX` |
| `RXD` | `PD1 / TX` |
| `DTR` | Reset circuit |

Install a CH340/CH341 driver if your operating system does not detect the USB serial port automatically.

## BOM

The full bill of materials is in [`BOM.csv`](BOM.csv).

| Ref | Qty | Value |
| --- | ---: | --- |
| `U1` | 1 | ATmega328-P |
| `U2` | 1 | CH340G |
| `U3` | 1 | L7805 |
| `P1` | 1 | USB-C receptacle |
| `SW1` | 1 | Reset push button |
| `Y1` | 1 | 12 MHz crystal |
| `Y2` | 1 | 16 MHz crystal |
| `J1` | 1 | Digital header, `0-13` |
| `J2` | 1 | Analog header, `A0-A5` |
| `J3` | 1 | Power header |

## Programming

After an Arduino-compatible bootloader is installed, the board can be programmed through USB serial.

Typical Arduino IDE settings:

- **Board:** Arduino Uno
- **Processor:** ATmega328P
- **Clock:** 16 MHz
- **Port:** CH340 serial port

If the ATmega328-P is blank, burn the bootloader first using an ISP programmer connected to the SPI pins.

## Power

- USB-C can power the board from a USB host or charger.
- `VIN` feeds the L7805 regulator for external input power.
- `7-12 V` on `VIN` is recommended by the silkscreen note.
- Avoid powering the board from USB and `VIN` at the same time unless the power path has been reviewed.

## Credits

This project uses:

- [KiCad](https://www.kicad.org/) for schematic capture, PCB layout, and 3D board preview
- ATmega328-P by [Microchip](https://www.microchip.com/)
- CH340G USB serial converter by WCH

Board by Apish Rana.

## License

TBD
