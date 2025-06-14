# 🧪 i2s_tx_uvm_verification

A complete SystemVerilog/UVM-based verification environment for the `I2S_TX` module – a serial audio transmitter implementing the I2S bus protocol.  
This project validates the correctness of the I2S transmitter under multiple configurations and scenarios.

---

## 🎯 Project Goal

To verify an RTL module (`I2S_TX`) that transmits PCM audio streams using the I2S protocol with support for:
- 24-bit MSB-first audio format
- Single or dual channel modes
- Optional status word insertion
- AXI4-Stream–like handshake for data input

---

## 📚 Specification Summary

Based on:  
**I2S TX Specification** (29/05/2024) by Miriam Ash

Features:
- Data format: 24-bit, 2’s complement, MSB first
- WS signal: synchronized to SCK, WS = SCK/64
- Optional status word in LSBs
- Single channel selection (left/right)
- AXI-like streaming interface with `valid`, `ready`, `data`, `ch`

---

## 🧪 Verification Environment

This UVM-based testbench includes:
- **Top-level testbench** (`testbench.sv`)  
- **UVM test class** (`i2s_tx_test.sv`)
- **UVM environment** connecting all components
- **Agents** for PCM data, configuration, status, and I2S output
- **Drivers**, **monitors**, and **sequencers** per agent
- **Sequence library** (`i2s_tx_seq_lib.sv`) with basic and corner-case tests
- **Scoreboard** to validate output correctness

---

## ✅ Verified Features

- Dual vs. single channel transmission
- Left/right channel selection logic
- AXI-style valid/ready data flow
- Status word enable/disable modes
- Frame format and MSB delay compliance

---

## ▶️ Running the Simulation

You can run the testbench using any simulator that supports SystemVerilog and UVM (e.g., QuestaSim, VCS, Riviera):

1. Compile all source files
2. Run the top module `testbench.sv`
3. Use UVM’s built-in test runner:

```systemverilog
run_test("i2s_tx_test");
