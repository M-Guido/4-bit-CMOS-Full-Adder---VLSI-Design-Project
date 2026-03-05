# 4-bit-CMOS-Full-Adder---VLSI-Design-Project
This project features a fully custom 4-Bit CMOS Ripple-Carry Adder designed for the TSMC 180nm process. The architecture is built using a NAND-only logic implementation for optimized gate density and reliability
Project Description:
The design implements a 4-bit addition operation using a NAND-only logic gate approach. It is engineered to meet professional semiconductor manufacturing standards, including high-drive output capability and robust electrical protection.
Technical Specifications
Process: TSMC 180nm CMOS (1 lambda = 0.1 um).
Operating Frequency: 30MHz target at 25pF load.
Output Drive: >=15mA DC current via tapered buffers.
Supply Voltage: 1.8V+-10%.
Protection: Diode-based ESD protection at all signal pads and latch-up prevention via substrate/well taps.
File Structure & Cells
The project is organized into modular .mag files for easy maintenance and hierarchical integration:
Logic & Corenand.mag: Standard 2-input NAND gate cell.
sumator_1_bit.mag: 1-bit Full Adder block using nine NAND gates.
sumator_4_bit.mag: Final top-level assembly of the 4-bit adder.
Buffers & Drive 
bufor_nmos.mag & bufor_pmos.mag: Large-scale output transistors for high current drive.
bufor_nmos_maly.mag & bufor_pmos_maly.mag: Intermediate stages for the tapered buffer chain.
bufor.mag: Complete buffer assembly combining all stages.
I/O & Protection
pad.mag: Signal I/O pad with integrated ESD diodes and a multi-metal stack.
pad_VDD.mag & pad_VSS.mag: Specialized pads for power supply and ground ring connections.

Prerequisites
Magic VLSI (configured for SCMOS technology).
use this command to run magic with the library installed (u have to be in the locaction where your files are)
magic -T SCN6M_SUBM.10.MIM
open file sumator_4_bit.mag to see full project.
