# Traffic Light Controller — Synchronous FSM Design in VHDL

## Overview
This project implements a **synchronous traffic light controller** using **VHDL**, designed and deployed on an **Altera DE2 FPGA board**. The system is built using a **finite state machine (FSM)**–based design methodology and follows a structured digital design flow from specification through hardware validation.

The controller manages an intersection between a **main street** and a **side street**, prioritizing main-street traffic while responding to real-time sensor input from the side street. The design emphasizes **deterministic behavior**, **timing correctness**, and **hardware-accurate RTL modeling**.

---

## Key Features
- Fully synchronous **FSM-based controller** (Moore or Mealy)
- **RTL-level VHDL design** with structural modeling
- No vendor IP cores or behavioral-only modeling
- Programmable timing using on-board switches
- Real-time response to asynchronous sensor input
- Tested on physical FPGA hardware (DE2 board)

---

## System Behavior
- Main street remains green by default
- Side street traffic is detected via a sensor input
- Light transitions follow realistic traffic sequencing:
  - Green → Yellow → Red
- Configurable timing for:
  - Main street green duration
  - Side street green duration
  - Yellow light intervals
- Automatic return to main-street priority when no side-street traffic is present

---

## Architecture Overview
The system is composed of the following major blocks:

- **FSM Controller**  
  Core decision-making logic implementing the traffic light state transitions

- **Main & Side Street Counters**  
  Programmable timers controlling green light durations

- **Comparator Logic**  
  Detects when programmable counters reach their configured limits

- **Clock Divider**  
  Reduces the system clock to human-observable timing

- **Debouncer**  
  Cleans asynchronous mechanical input from the side-street sensor

- **Timer Module**  
  Controls fixed-duration yellow light intervals

- **BCD Decoder (Bonus Feature)**  
  Displays live counter values on dual 7-segment displays

---

## FSM Design Methodology
The controller was developed using a formal FSM design process:

1. Problem specification and requirement analysis  
2. State diagram creation  
3. State table derivation  
4. State reduction and minimization  
5. State encoding and assignment  
6. Transition table synthesis  
7. Excitation and output equation derivation  
8. RTL circuit implementation

Both **Moore** and **Mealy** machine models were explored and implemented.

---

## Hardware Platform
- **FPGA Board:** Altera DE2 (Cyclone IV)
- **Inputs:**
  - Global clock and reset
  - Side street car sensor
  - Programmable timing via toggle switches
- **Outputs:**
  - Main and side street traffic lights (one-hot encoded LEDs)
  - Optional dual 7-segment BCD display

---

## Design Constraints
- VHDL-only implementation (no Verilog)
- RTL modeling required (no pure behavioral designs)
- No third-party or vendor IP cores
- Fully synchronous, globally resettable system
- Simulation verified against theoretical behavior
- Hardware validation required on FPGA

---

## Tools Used
- Quartus II
- ModelSim (simulation)
- Altera DE2 FPGA board

---

## What This Project Demonstrates
- Strong understanding of **digital logic and FSM design**
- Experience translating specifications into hardware
- RTL-level VHDL coding and simulation
- Hardware-software boundary awareness
- FPGA deployment and debugging
