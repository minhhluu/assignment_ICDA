# assignment_ICDA
Intergrated Circuit Design Application

## Table of Contents

1. [I. CMOS Inverter Layout (Microwind)](#i-cmos-inverter-layout-microwind)
   - [1. Circuit Design](#1-circuit-design)
   - [2. Layout and Simulation](#2-layout-and-simulation)
   - [3. Polysilicon Layer Details](#3-polysilicon-layer-details)
   - [4. Metal Layer Details](#4-metal-layer-details)
2. [II. 2-bit Flash ADC Design (DSCH)](#ii-2-bit-flash-adc-design-dsch)
   - [1. Overview](#1-overview)
   - [2. Circuit Design](#2-circuit-design-1)
   - [3. Simulation Results](#3-simulation-results)
3. [III. Sequential Logic Circuit using D Flip-Flops (DSCH)](#iii-sequential-logic-circuit-using-d-flip-flops-dsch)
   - [1. Overview](#1-overview-1)
   - [2. Circuit Description](#2-circuit-description)
   - [3. Behavior Summary](#3-behavior-summary)
   - [4. Applications](#4-applications)
4. [Summary](#-summary)

## I. CMOS Inverter Layout (Microwind)

### 1. Circuit Design

The inverter circuit is designed using:
- **1 PMOS transistor** (connected to VDD)
- **1 NMOS transistor** (connected to GND)

Design Steps:
1. Connect input signal `A` to both gates of PMOS and NMOS.
2. Connect the drains of PMOS and NMOS together to form the output `Y`.
3. Connect PMOS source to `VDD`, NMOS source to `GND`.

### 2. Layout and Simulation

- Input `A` is given a **square waveform**.
- Output `Y` is observed to toggle as an **inverter**.
- Screenshots of the layout and waveform simulation:

![Layout Image](https://i.postimg.cc/QMgBnZtJ/Quest-1.png)

![Waveform Image](https://i.postimg.cc/Dzjm9Dmb/image.png)

**Working Principle**:

> - When `A = 0`: 
> &nbsp;&nbsp;&nbsp;&nbsp;PMOS = ON, NMOS = OFF → Output `Y = 1` (pulled up to VDD)
> - When `A = 1`: 
> &nbsp;&nbsp;&nbsp;&nbsp;PMOS = OFF, NMOS = ON → Output `Y = 0` (pulled down to GND)

### 3. Polysilicon Layer Details

<span style="color:red">**This layer is Polysilicon**</span>

- **Polysilicon as Gate**:
  + Acts as the control gate in both PMOS and NMOS transistors.
  + Handles high-temperature processes due to its thermal resilience.
  + Voltage applied to this gate determines ON/OFF state of the transistor.

### 4. Metal Layer Details

<span style="color:blue">**This layer is Metal**</span>

- **Connections**:
  + **PMOS source** → Metal → `VDD`
  + **NMOS source** → Metal → `GND`
  + **Drains of both** → Connected using metal → Output `Y`

![Metal Connection Image](https://i.postimg.cc/8zp03rL0/image.png)

---
## II. 2-bit Flash ADC Design (DSCH)

### 1. Overview

This design converts an analog signal (`Vin`) into a 2-bit binary output using:
- 3 Comparators (threshold-based)
- Logic gates for encoding the binary result

### 2. Circuit Design

- Reference voltages (e.g. `Vref0`, `Vref1`, `Vref2`) are compared against `Vin`
- Based on the comparison results, 2-bit digital output is generated:
  + `00`, `01`, `10`, or `11`

### 3. Simulation Results

- Simulate the circuit using **4 different analog levels**.
- Observe the binary output changing according to `Vin`.

![ADC Circuit](https://i.postimg.cc/dVyZrycX/Quest-2.png)

---
## III. Sequential Logic Circuit using D Flip-Flops (DSCH)

### 1. Overview

This circuit implements a **custom sequential logic** design using:
- **Combinational logic** (AND, OR, NOT gates)
- **2 D Flip-Flops**
- **2 input signals** (`in1`, `in8`)
- **Clock signals** (`clk6`, `clk7`)
- **1 output indicator** (LED `out1`)

### 2. Circuit Description

- **Inputs**:
  + `in8`: passed through a NOT gate to form a control signal
  + `in1`: connects to both D Flip-Flops (`D` inputs)

- **Sequential Storage**:
  + Two **D Flip-Flops** capture and store state on clock edges.
  + Both flip-flops share the same reset `RST` input from `in1`.

- **Logic Flow**:
  1. NOT gate inverts `in8`, generating control logic.
  2. Three 3-input **AND gates** are used to check specific input-output combinations.
  3. Outputs of the AND gates are passed to a 3-input **OR gate**, which activates the final **LED output** (`out1`).
  4. Flip-flop outputs (`Q`) feed back into the combinational logic loop to control future states.

- **Clock Control**:
  + `clk6` and `clk7` drive the flip-flops, determining when state updates occur.

![Quest_3](https://i.postimg.cc/15TN8K2w/Quest-3.png)

### 3. Behavior Summary

This circuit acts like a **finite state machine (FSM)**:
- The **output LED** (`out1`) only turns on when a **specific sequence** of input conditions and stored states is satisfied.
- Flip-flops retain internal state across clock cycles, influencing logic outcomes in the next cycle.

### 4. Applications

- Can be used in **pattern detection**, **sequence controllers**, or **basic state machines**.
- Forms the basis for more complex synchronous systems such as **counters**, **encoders**, or **protocol checkers**.

---

## Summary

| Project | Description |
|--------|-------------|
| CMOS Inverter | Manual transistor layout and simulation in Microwind |
| 2-bit Flash ADC | Analog-to-digital conversion using DSCH |
| Sequential Logic | Finite-state behavior with flip-flops and logic gates |

These three projects serve as a solid foundation in both **combinational** and **sequential digital design**.
