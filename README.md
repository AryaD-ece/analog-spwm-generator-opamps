# Analog SPWM Generator using Op-Amps

Analog SPWM generator using Op-Amps with LTspice simulation and hardware validation.

---

## Overview

This project implements a Sinusoidal Pulse Width Modulation (SPWM) generator using analog circuits.

Unlike digital implementations, this design uses only Op-Amps to generate PWM signals.

---

## Output (Hardware Verification)

![SPWM Output](images/spwm_dso_output.png)

---

## System Architecture

![Block Diagram](images/block_diagram.png)

### Blocks:
- Wien Bridge Oscillator → 50 Hz sine
- Triangular Generator → ~10 kHz carrier
- Comparator → SPWM output

---

## Simulation

![LTspice Simulation](images/ltspice_waveform.png)

- Designed and verified in LTspice
- `.asc` file available in `/simulation`

---

## Hardware Implementation

![Hardware](hardware/pcb_implementation.jpg)

- Built on zero PCB
- Powered using ±12V / ±15V
- Verified using DSO

---

## Results

- Stable SPWM waveform observed
- Duty cycle follows sine envelope
- Carrier frequency close to design (~10 kHz, with tolerances)

---

## Calculations

See:
👉 `/calculations/design_calculations.md`

---

## Repository Structure
/simulation
/hardware
/images
/docs
/calculations


---

## Author

Arya Dinesh  
ECE Undergraduate
