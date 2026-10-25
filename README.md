# RP2040 Development Board

I designed my own small microcontroller board from scratch. It's built around the **RP2040**, the same chip used in the Raspberry Pi Pico. I drew the circuit and laid out the circuit board in **Altium Designer**, then had it manufactured and assembled by **JLCPCB**.

📄 **[View the schematic (PDF)](RP2040_Dev_Board.pdf)**

## What's on the board

| Part | What it does |
|---|---|
| **RP2040 chip** | The "brain." A dual-core processor that runs the code you program onto the board. |
| **16 MB flash memory** (W25Q128) | Stores the program. The RP2040 has no built-in storage, so it needs this external memory chip. |
| **12 MHz crystal** | Gives the chip a steady, accurate clock signal, like a metronome that keeps everything in time. |
| **USB-C port** | Powers the board and lets you plug it into a computer to upload code. |
| **ESD protection chip** (USBLC6) | Protects the board from static electricity shocks that come in through the USB port. |
| **Fuse** (500 mA) | Cuts power if too much current flows, so a short circuit doesn't damage the board or your computer. |
| **3.3 V voltage regulator** (AP2112K) | USB supplies 5 V, but the chip runs on 3.3 V. This steps the voltage down. |
| **BOOT and RESET buttons** | RESET restarts the board. Holding BOOT while plugging in puts it in upload mode, so it shows up on your computer like a USB drive. |
| **SWD header** | A debugging port. It lets you pause the code and inspect it while it runs. |
| **2 LEDs** | Simple status lights. |

**Board size:** 25 × 55 mm, **4 layers**. Four copper layers instead of two give room for a solid ground layer, which keeps signals cleaner and makes routing easier on a small board.

## How I designed it

1. **Schematic.** I drew the circuit: which parts connect to which. I followed Raspberry Pi's official guide, *Hardware design with RP2040*, for the parts the chip needs around it to work.
2. **Parts.** I picked parts JLCPCB stocks, so they could assemble the board for me. I added their LCSC part numbers to the parts list (BOM).
3. **PCB layout.** I placed the parts and routed the copper traces between them. A few things needed extra care:
   - **Small capacitors right next to the chip's power pins.** They act like tiny local batteries that smooth out the power supply.
   - **The USB data lines** run as a matched pair of equal length, so the signals arrive at the same time.
   - **The flash memory** sits close to the chip, with short traces, because it runs fast.
4. **Design rules.** I set rules in Altium (minimum trace width, spacing, and so on) to match what JLCPCB can manufacture, then ran the rule check to catch errors.
5. **Ordering.** I exported the files JLCPCB needs and placed the order.

## What's in this repo

```
RP2040_Dev_Board.PrjPcb   Altium project file (opens everything below)
RP2040_Dev_Board.SchDoc   Schematic (the circuit diagram)
RP2040_Dev_Board.PcbDoc   PCB layout (the physical board design)
RP2040_Dev_Board.pdf      Schematic as a PDF, so you can view it without Altium
RP2040_rules.RUL          Design rules
Library/                  Part symbols and footprints I used
fabrication/              The exact files I sent to JLCPCB
```

### Files sent to the manufacturer (`fabrication/`)

- **Gerbers** (`.zip`): the board "blueprints," one image per layer, used to make the bare circuit board.
- **BOM** (`.xlsx`): the bill of materials, a shopping list of every part.
- **CPL** (`.csv`): the pick-and-place file. It tells the assembly machine where each part goes and how it's rotated.

## Tools

Altium Designer · JLCPCB (manufacturing and assembly)

## Author

Brandon Kakimoto, Computer Engineering, Cal Poly Pomona
