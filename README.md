# 4-bit CMOS Full Adder - VLSI Design Project

This project features a fully custom **4-Bit CMOS Ripple-Carry Adder** designed for the **TSMC 180nm** process. The architecture is built using a NAND-only logic implementation for optimized gate density and reliability.

## Project Description
The design implements a 4-bit addition operation using a NAND-only logic gate approach. It is engineered to meet professional semiconductor manufacturing standards, including high-drive output capability and robust electrical protection.

## Technical Specifications
* **Process:** TSMC 180nm CMOS ($1 \lambda = 0.1 \mu m$).
* **Operating Frequency:** 30MHz target at 25pF load.
* **Output Drive:** $\ge 15mA$ DC current via tapered buffers.
* **Supply Voltage:** $1.8V \pm 10\%$.
* **Protection:** Diode-based ESD protection at all signal pads and latch-up prevention via substrate/well taps.

## Metal Stack & Interconnects
The design utilizes the full **6-metal layer stack** provided by the SCMOS process to handle high current requirements and complex signal routing:

* **Metal 1:** Used for local intra-cell connections and horizontal power/ground rails within logic gates.
* **Metal 2 & Metal 3:** Dedicated to signal "bridges" and long-distance routing between NAND gates to avoid intersections.
* **Metal 4, 5, & 6:** Primarily used in the PAD ring and power distribution network to minimize resistance and support the 15mA output drive.
* **Via Strategy:** PAD structures incorporate a vertical stack of all six metals, interconnected through dense via arrays (`m2contact` through `m6contact`) for high reliability and low impedance.
* **Power Distribution:** Wide power rings are implemented to satisfy electromigration rules (max $0.3 mA/\mu m$ for Metal 1).



## File Structure & Cells
The project is organized into modular `.mag` files for hierarchical integration:

### Logic & Core
* `nand.mag`: Standard 2-input NAND gate cell.
* `sumator_1_bit.mag`: 1-bit Full Adder block using nine NAND gates.
* `sumator_4_bit.mag`: Final top-level assembly of the 4-bit adder.

### Buffers & Drive
* `bufor_nmos.mag` & `bufor_pmos.mag`: Large-scale output transistors for high current drive.
* `bufor_nmos_maly.mag` & `bufor_pmos_maly.mag`: Intermediate stages for the tapered buffer chain.
* `bufor.mag`: Complete buffer assembly combining all stages.

### I/O & Protection
* `pad.mag`: Signal I/O pad with integrated ESD diodes and multi-metal stack.
* `pad_VDD.mag` & `pad_VSS.mag`: Specialized pads for power supply and ground ring connections.

## Prerequisites & Running
To view or edit the project, you need **Magic VLSI** configured for SCMOS technology.

1. Navigate to the project directory.
2. Run Magic with the specific technology file:
   ```bash
   magic -T SCN6M_SUBM.10.MIM
