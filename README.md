# Three-Port SiC DC/DC Converter for EV Auxiliary Power

Design of a **3.6 kW three-port bidirectional DC/DC converter** that supplies both the **48 V** and **12 V** auxiliary buses of an electric vehicle from the high-voltage traction battery, using a single transformer and a single low-voltage bridge.

> Course project: **ED5023 – Power Converter Design for Electrified Vehicles**, IIT Madras (Jul–Nov 2026)
> Instructor: Prof. Deepak Ronanki

📄 **Full report:** [ThreePort_DCDC_Converter_Report.pdf](ThreePort_DCDC_Converter_Report.pdf)

---

## Overview

Electric vehicles carry a high-voltage traction battery, but most on-board loads still run from low-voltage buses: 12 V for lights, infotainment and controllers, and increasingly 48 V for heavier loads such as electric power steering and compressors. This project designs an **auxiliary power module (APM)** based on a topology proposed by Toyota Central R&D Labs. It is a **dual active bridge (DAB)** whose low-voltage side forms the 48 V bus, with the centre tap of the transformer forming the 12 V bus. Power can flow between all three ports.

## Specifications

| Parameter | Value |
|---|---|
| HV port (traction battery) | 280–450 V (400 V nominal) |
| 48 V port | 2.4 kW |
| 12 V port | 1.2 kW |
| Total throughput | 3.6 kW |
| Switching frequency | 100 kHz |
| Modulation | Single-phase-shift (SPS) + fixed LV duty |
| Maximum phase shift at rated power | 60° |
| Devices | 650 V SiC MOSFETs, TO-247-4 |

## What was done

**Part (a): Analytical design**
- Transformer turns ratio **N = 8.5** (wound 1+1 : 17, centre-tapped).
- DAB inductance **L = 0.32 µH**, so that rated power is reached within the 60° phase-shift limit.
- Worst-case phase shift of **54.6° at 280 V**, checked against a PLECS model with losses.
- Split DC-link capacitor banks sized for unbalanced 12 V / 48 V loading.
- Transformer and coupled inductor designed with the area-product method on **TDK PC95 PQ65/54** ferrite cores.

**Part (b): Component selection**
- Datasheet-based selection of SiC MOSFETs (Infineon CoolSiC, TO-247-4), gate drivers, capacitors and magnetics.
- Conduction, switching and dead-time loss estimates, with thermal checks.

**Part (c): PCB design**
- Altium PCB layout of the low-voltage H-bridge with the centre-tapped split capacitor bank.

## Tools

`PLECS` · `MATLAB` · `Altium Designer` · Component datasheets (Mouser / DigiKey)

## Repository contents

| File | Description |
|---|---|
| `ThreePort_DCDC_Converter_Report.pdf` | Full project report: design equations, simulations, component selection, PCB |
| `README.md` | This file |

## Team

- Yellamelli Abhinav (ED26M012)
- Mahesh Nandakishor Gowd (ED22B006)
- Nituri Badrinath Reddy (ED26M030)

Department of Engineering Design, IIT Madras · Batch 8, Project 13
