# RP2040 Development Board

A custom, compact development board built around the Raspberry Pi **RP2040** microcontroller. Designed from scratch in **Altium Designer** (schematic, 4-layer PCB layout, custom libraries) and fabricated and assembled by **JLCPCB**.

📄 **[View the schematic (PDF)](RP2040_Dev_Board.pdf)**

## Specs

| | |
|---|---|
| MCU | RP2040 — dual-core Arm Cortex-M0+ @ up to 133 MHz, 264 KB SRAM |
| Flash | 16 MB QSPI (Winbond W25Q128JVSIQ) |
| Clock | 12 MHz crystal (Abracon ABM8-272-T3) |
| USB | USB-C (HRO TYPE-C-31-M-12), USB 2.0 full-speed, 5.1 kΩ CC pull-downs |
| Protection | USBLC6-2SC6 ESD protection on D+/D−, 500 mA resettable PTC fuse on VBUS |
| Power | AP2112K-3.3 LDO (5 V → 3.3 V, 600 mA); RP2040 internal 1.1 V core regulator |
| Controls | BOOTSEL and RESET tactile buttons |
| Debug | SWD header (SWCLK / SWDIO / GND) |
| Indicators | 2 status LEDs |
| PCB | 25 × 55 mm, 4-layer |

## Design highlights

- Followed Raspberry Pi's *Hardware design with RP2040* guidelines for decoupling, crystal load capacitance, and QSPI flash routing.
- Series termination resistors and length-matched routing on the USB differential pair.
- Custom design rules (`RP2040_rules.RUL`) matched to JLCPCB's 4-layer capabilities.
- Assembly-ready: BOM with LCSC part numbers and pick-and-place file included.

## Repository layout

```
RP2040_Dev_Board.PrjPcb   Altium project
RP2040_Dev_Board.SchDoc   Schematic
RP2040_Dev_Board.PcbDoc   PCB layout
RP2040_Dev_Board.pdf      Schematic (PDF, viewable without Altium)
RP2040_rules.RUL          PCB design rules
Library/                  Integrated component libraries used in the design
fabrication/              Files sent to JLCPCB: Gerbers, BOM, pick-and-place (CPL)
```

## Fabrication

The `fabrication/` folder contains exactly what was submitted to JLCPCB for PCB fabrication and SMT assembly:

- `RP2040_Dev_Board_Gerbers.zip` — Gerber and drill files
- `RP2040_Dev_Board_BOM.xlsx` — bill of materials with LCSC part numbers
- `RP2040_Dev_Board_CPL.csv` — component placement list

## Tools

Altium Designer · JLCPCB fabrication and assembly

## Author

Brandon Kakimoto — Computer Engineering, Cal Poly Pomona
