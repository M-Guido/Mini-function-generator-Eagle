# Mini Function Generator — PCB Project
 
**Author:** Mikołaj Gałązka   
**Tool:** Autodesk EAGLE  

---

## Overview

A compact sequential signal generator PCB designed in Autodesk EAGLE. The circuit uses a tunable **NE555** timer as a clock source driving a **CD4052** analog multiplexer, with **BC547** NPN transistors acting as output current amplifiers. The output frequency is continuously adjustable via a trimmer potentiometer.

The board is suitable for controlling cyclic processes, LED chaser effects, or general low-frequency signal generation tasks on an electronics workbench.

---

## How It Works

1. The **NE555** (IC1) operates in astable mode, generating a square wave clock signal at a frequency set by the RC network and trimmer potentiometer (R14).
2. The **CD4052** dual 4-channel analog multiplexer (IC2) receives the clock pulses and sequentially switches between outputs, creating a traveling wave effect.
3. Two **BC547** NPN transistors (T1, T2) buffer the outputs to safely drive real loads.
4. A **1N4004** diode (D1) provides reverse-polarity protection on the power input.

---

## Key Components

| Part | Value / Type | Description |
|------|-------------|-------------|
| IC1 | NE555 (LINEAR_555N) | Astable timer / clock generator |
| IC2 | CD4052 (4052N) | Dual 4-channel analog multiplexer |
| T1, T2 | BC547 | NPN transistors — output drivers |
| D1 | 1N4004 | Reverse polarity protection diode |
| R14 | 47kΩ trimmer | Frequency adjustment potentiometer |
| C10 | 100µF / 25V | Power supply filter capacitor |
| X1, X2 | WAGO 237 | 2-pin screw terminal connectors |
| JP1 | 2-pin jumper | Configuration jumper |


## PCB Details

- **Package standard:** SMD resistors/capacitors in 1206, ICs in DIP packages
- **Custom library:** `GałązkaUkład.lbr` — standard footprints modified with enlarged solder pads for easier hand soldering
- **Supply voltage:** +5V DC
- **Board files:** schematic (`.sch`) and board layout (`.brd`) exported from EAGLE

---

## Repository Contents

```
├── GałązkaUkład.sch       # EAGLE schematic
├── GałązkaUkład.brd       # EAGLE board layout
├── GałązkaUkład.lbr       # Custom component library
├── .gpi and .pho gerbers/               # Gerber files ready for fabrication drills and pcb schema
└── README.md
```

---

## Commissioning & Measurement Plan

Before powering up, perform a visual inspection of solder joints and component polarity, and run a short-circuit test on the power connector.

**Test equipment needed:**
- Lab power supply (with current limiting set ~200mA)
- Digital multimeter (ammeter + voltmeter mode)
- 2-channel digital oscilloscope

**Parameters to measure:**

| Parameter | Method |
|-----------|--------|
| Supply current draw | Ammeter in series with V+ |
| NE555 output frequency & duty cycle | Oscilloscope on IC1 pin 3 |
| NE555 capacitor charging waveform | Oscilloscope on IC1 pin 2/6 |
| CD4052 output voltage levels | Voltmeter on IC2 outputs |
| Transistor operating points (V_CE, I_C) | Multimeter |

Adjust R14 (trimmer) across its full range and record the min/max output frequency of the NE555.

---

