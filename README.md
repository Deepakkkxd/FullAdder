# Verilog Digital Logic: Hierarchical Full Adder

A modular, hardware-oriented implementation of a **1-Bit Full Adder** built hierarchically using **Half Adders** and an **OR gate** in Verilog, designed and verified using Icarus Verilog and EPWave.

---

## 🏗️ Design Architecture

Following the principles of scalable digital design, this project avoids monolithic equations by utilizing a **structural approach** (Lego-brick methodology):
1. **Half Adder Module (`halfAdder`):** Combines an XOR gate for the sum and an AND gate for the carry-out.
2. **Full Adder Module (`fullAdder`):** Instantiates two Half Adders and an OR gate to process three inputs (`a`, `b`, and `cin`), producing the final `sum` and `cout`.

---

## 📊 Verification & Results

The design was exhaustively tested using an automated testbench featuring a loop counter and bit concatenation (`{a, b, cin} = i`) to cycle through all 8 binary input combinations (`000` to `111`).

### 1. Console Simulation Log
The automated testbench prints out a clean truth table verifying every combination of inputs against expected arithmetic outputs[cite: 2]:

![Console Output Log](docs/console_log.png)[cite: 2]

### 2. EPWave Waveform Simulation
The waveform below illustrates the timing and transitions across all 8 states, confirming zero propagation errors and correct carry-ripple behavior[cite: 1]:

![EPWave Waveform](docs/waveform.png)[cite: 1]

---

## 🚀 How to Run Locally

If you have Icarus Verilog (`iverilog`) and `vvp` installed, you can compile and run the simulation from your terminal:

```bash
iverilog -Wall -g2012 design.sv testbench.sv
./a.out
