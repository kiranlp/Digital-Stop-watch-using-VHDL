# ⏱️ Digital Stopwatch using VHDL (FPGA Implementation)

A fully functional digital stopwatch designed in **VHDL** and implemented on an **FPGA trainer kit** using **Xilinx ISE**. The design counts time and shows it on **7-segment displays**, with **Start / Stop / Reset** control.

![VHDL](https://img.shields.io/badge/Language-VHDL-blue)
![Xilinx ISE](https://img.shields.io/badge/Tool-Xilinx%20ISE-red)
![FPGA](https://img.shields.io/badge/Platform-FPGA%20Trainer%20Kit-green)

---

## 📌 Overview

This project implements a digital stopwatch entirely in hardware using VHDL. A high-frequency board clock is divided down to a slow timing tick, which drives cascaded BCD counters. The counter outputs are decoded and multiplexed onto 7-segment displays on the trainer kit.

## ✨ Features

- Start / Stop / Reset control using push buttons or switches on the trainer kit
- Cascaded BCD counters for seconds and minutes
- Clock divider to generate the timing tick from the on-board clock
- 7-segment decoder with display multiplexing
- Modular, synthesizable VHDL design
- Simulated and verified before hardware implementation

## 🛠️ Technologies Used

| Category | Details |
|---|---|
| HDL | VHDL |
| Tool | Xilinx ISE Design Suite |
| Hardware | FPGA Trainer Kit |
| Output | 7-Segment Display |
| Simulation | ISim (Xilinx ISE Simulator) |

## 🧩 System Architecture

```
            ┌───────────────┐
 Clock ───► │ Clock Divider │──► timing tick
            └───────────────┘        │
                                     ▼
 Start/Stop ──►┌──────────────────────────────┐
 Reset ───────►│  Control Logic + BCD Counter │
               └──────────────┬───────────────┘
                              │ BCD digits
                              ▼
                   ┌─────────────────────┐
                   │ 7-Segment Decoder / │──► 7-Segment Display
                   │ Display Multiplexer │
                   └─────────────────────┘
```

### Modules

| Module | Description |
|---|---|
| `clock_divider` | Divides the board clock to generate the counting tick |
| `control` | Handles start, stop, and reset logic |
| `counter` | BCD counter for seconds/minutes |
| `seven_seg_decoder` | Converts BCD to 7-segment pattern |
| `top` | Top-level module connecting all components |

> 📝 Rename the modules above to match the files in your repository.

## 📂 Project Structure

```
Digital-Stop-watch-using-VHDL/
├── src/
│   ├── clock_divider.vhd
│   ├── control.vhd
│   ├── counter.vhd
│   ├── seven_seg_decoder.vhd
│   └── top.vhd
├── sim/
│   └── tb_stopwatch.vhd
├── constraints/
│   └── stopwatch.ucf
├── images/
│   └── (simulation waveforms, hardware photos)
└── README.md
```

## ▶️ How to Run

### Simulation
1. Open **Xilinx ISE** and create a new project.
2. Add all `.vhd` files from the `src/` folder.
3. Add the testbench from `sim/` and set it as the simulation top module.
4. Run **ISim** and verify the waveforms for start, stop, and reset behavior.

### Hardware Implementation
1. Set `top.vhd` as the top module.
2. Add the `.ucf` constraints file to map pins to the trainer kit (clock, buttons, 7-segment pins).
3. Run **Synthesize → Implement Design → Generate Programming File**.
4. Connect the trainer kit and program it with the generated `.bit` file.

## 🎮 Operation

| Input | Action |
|---|---|
| Start | Begins counting |
| Stop | Pauses the count |
| Reset | Clears the display to `00:00` |

## 📊 Results

- Stopwatch counts correctly and displays time on the 7-segment display
- Start, stop, and reset functions verified in simulation and on hardware

_Add your simulation waveform screenshots and trainer kit photos here:_

```
![Simulation](images/simulation.png)
![Hardware](images/hardware.jpg)
```

## 🚀 Future Improvements

- Add lap/split time feature
- Extend to hours and millisecond resolution
- Add button debouncing for more reliable input
- Port the design to Xilinx Vivado

## 🎓 Learning Outcomes

- VHDL design: FSMs, counters, clock division
- FPGA design flow: synthesis, implementation, bitstream generation
- Interfacing 7-segment displays and I/O on an FPGA trainer kit

## 👤 Author

**Kiran Kumar**
Electronics & Communication Engineering | Embedded Systems & VLSI
Bapuji Institute of Engineering & Technology, 

- LinkedIn: [your-linkedin-url]
- Portfolio: [your-portfolio-url]

