# Analog SPWM Generator using Op-Amps

Fully analog implementation of Sinusoidal PWM (SPWM) using operational amplifiers — validated through LTspice simulation and real hardware measurements.

---

## Output (Hardware Verified)

![SPWM Output](images/spwm_dso_output.png)

---

## Overview

This project implements SPWM generation using purely analog circuits, without any microcontrollers.

A low-frequency sinusoidal reference is compared with a high-frequency triangular carrier to produce a PWM signal whose duty cycle follows the sine waveform.

This technique is widely used in power electronics for applications such as inverters, motor drives, and audio amplification.

---

## System Architecture

![Block Diagram](images/block_diagram.png)

### Functional Blocks

- **Wien Bridge Oscillator**
  - Generates 50 Hz sine wave  
  - Diode-based stabilization maintains amplitude  

- **Triangular Wave Generator**
  - Integrator + Schmitt trigger  
  - Generates ~10 kHz carrier  

- **Comparator**
  - Compares sine and triangular signals  
  - Produces SPWM output  

---

## Working Principle

- If \( V_{sine} > V_{tri} \) → Output HIGH  
- If \( V_{sine} < V_{tri} \) → Output LOW  

This produces PWM where:

- Duty cycle varies with sine amplitude  
- Wide pulses at peaks  
- Narrow pulses near zero crossings  

---

## Simulation (LTspice)

### Circuit Schematic

![LTspice Schematic](images/ltspice_schematic.png)

> Complete LTspice schematic showing Wien Bridge oscillator, triangular generator, and comparator stages.

### Waveform Output

![LTspice Simulation](images/ltspice_waveform.png)

- Complete circuit simulated in LTspice  
- Verified:
  - 50 Hz sine generation  
  - ~10 kHz carrier waveform  
  - SPWM duty cycle modulation  

**Simulation file:**


simulation/spwm_generator.asc


---

## Hardware Implementation

![Hardware](hardware/pcb_implementation.jpg)

- Built on zero PCB  
- Op-Amps: LM741 / LM324  
- Supply: ±12V / ±15V  
- Output verified using Digital Storage Oscilloscope (DSO)

---

## Results

- Stable SPWM waveform successfully generated  
- Duty cycle accurately follows sinusoidal envelope  
- Carrier frequency observed in ~5–10 kHz range  
- Minor deviation due to component tolerances and non-ideal op-amp behavior  

> Observed frequency deviation highlights real-world non-ideal effects such as op-amp bandwidth limitations and practical circuit constraints.

---

## Design Snapshot (Key Calculations)

- Wien Bridge Oscillator:
  - \( f = \frac{1}{2\pi RC} \)
  - Designed for **50 Hz sine wave**

- Triangular Wave Generator:
  - Target: **~10 kHz carrier**
  - Calculated: ~11.36 kHz  
  - Observed: ~5–10 kHz  

- Comparator:
  - \( V_{sine} > V_{tri} \) → HIGH  
  - \( V_{sine} < V_{tri} \) → LOW  

📄 Full derivations:  
👉 [View Detailed Calculations](calculations/design_calculations.md)

---

## Handwritten Calculations (Original Work)

![Handwritten Calculations](calculations/design_calculations_handwritten.png)

> Initial design calculations were performed manually before simulation and hardware implementation.

---

## Applications

- Power inverters  
- Motor drives  
- Class-D amplifiers  

---

## Key Learnings

- Analog circuits require precise stability control  
- Component tolerances directly impact frequency accuracy  
- Diode stabilization is critical in oscillator design  
- Analog SPWM reveals real-world non-ideal behavior  

---

## Future Improvements

- Use high-speed op-amps for better switching performance  
- Add output filtering (low-pass)  
- Integrate with inverter stage  
- Optimize PCB layout to reduce noise  

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
B.Tech Electronics & Communication Engineering
