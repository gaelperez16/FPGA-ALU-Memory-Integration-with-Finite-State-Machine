# 🖥️ FPGA ALU-Memory Integration with 7-State FSM

![VHDL](https://img.shields.io/badge/VHDL-FPGA-blue)
![DE10-Lite](https://img.shields.io/badge/Board-DE10--Lite-green)
![Status](https://img.shields.io/badge/Project-Completed-success)

## 🧠 Overview

This project implements a custom Arithmetic Logic Unit (ALU) integrated with a synchronous memory module on the DE10-Lite FPGA board. The system is written in **VHDL** and supports **16 distinct 4-bit opcodes**, including arithmetic, logic, shift, and comparison operations.

A **7-state Finite State Machine (FSM)** ensures reliable sequential execution of read-compute-write cycles using a **single button press**. Real-time results are shown on the **7-segment HEX displays**, and operation flags are output to **LEDs** for visual feedback.

---

## 🛠️ Features

- ✅ 16 ALU operations (Add, Sub, INC, DEC, Logical/Arithmetic Shifts, Bitwise Ops, Compare, etc.)
- ✅ 8-bit output with signed decimal display on HEX3-HEX0
- ✅ 7-state FSM controlling memory reads, ALU computation, and writes
- ✅ Memory with 4 addresses (2-bit), 8-bit wide
- ✅ Real-time flag output on LEDs: Carry, Parity, Overflow, Positive, Zero, Negative
- ✅ DE10-Lite board input via switches (SW), pushbutton (BTN), and output via HEX and LEDR
- ✅ Custom NEGATE opcode (Two’s complement)
- ✅ Fully synthesizable and tested on actual hardware

---

## 📦 Project Structure

```plaintext
.
├── ALU.vhd          # VHDL source code for the Arithmetic Logic Unit
├── Memory.vhd       # VHDL code for 4x8-bit synchronous memory
├── Top.vhd          # Top-level FSM controller and display logic
├── Project4.pdf     # Full project report with design, testing, and results
└── README.md        # Project documentation
```
## Usage
🖥 Requirements
Intel Quartus Prime Lite (https://www.intel.com/content/www/us/en/software/programmable/quartus-prime/download.html)

DE10-Lite FPGA Board (https://www.terasic.com.tw/cgi-bin/page/archive.pl?Language=English&CategoryNo=139&No=1046)

USB Blaster cable for FPGA programming

---
## Switch Mapping

| Signal | Description          | SW Mapping |
| ------ | -------------------- | ---------- |
| A Addr | Memory read A        | SW9-SW8    |
| B Addr | Memory read B        | SW7-SW6    |
| Opcode | ALU operation select | SW5-SW2    |
| W Addr | Memory write address | SW1-SW0    |
-BTN: Executes one full operation cycle.
-HEX0–HEX3: Shows signed decimal output.
-LEDR[9:2]: Status flags (C, P, O, Pos, Zero, Neg).
-LEDR[0]: Write enable indicator.

## Example Operation Table
| BTN Press | A Addr | B Addr | Opcode | Write Addr | Description              | HEX Result |
|-----------|--------|--------|--------|-------------|---------------------------|-------------|
| 1         | 01     | XX     | 0010   | 01          | INC memory[01] to 1       | 0001        |
| 2         | 01     | XX     | 0010   | 01          | INC memory[01] to 2       | 0002        |
| 3         | 01     | 00     | 0110   | 10          | PASS A to memory[10]      | 0002        |
| 4         | 10     | XX     | 0010   | 10          | INC memory[10] to 3       | 0003        |
| 5         | 01     | 10     | 0000   | 00          | ADD 2 + 3 = 5             | 0005        |

🧠 Learning Outcomes
  Digital system design using VHDL
  FSM implementation and timing management
  Memory-ALU interfacing
  Hardware testing/debugging using real-time indicators
  Efficient use of DE10-Lite's limited I/O resources

## Resources and References
  IEEE Std 1076™-2008: VHDL Language Reference Manual
  Intel Quartus Prime Documentation
  DATASHEET: https://ftp.intel.com/Public/Pub/fpgaup/pub/Intel_Material/Boards/DE10-Lite/DE10_Lite_User_Manual.pdf

🤝 Let me know if you'd like this bundled into a downloadable file or want me to help build the GitHub repo structure locally or online.

