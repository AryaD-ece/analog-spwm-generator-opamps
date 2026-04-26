# Design Calculations

## 1. Wien Bridge Oscillator (50 Hz Sine Wave)

**Target frequency:** 50 Hz  

### Formula
f = 1 / (2πRC)

### Component Selection
- C = 100 nF  
- R = 1 / (2π × 50 × 100 × 10⁻⁹)  
- R ≈ 31.83 kΩ  

**Selected standard value:**  
- R = 33 kΩ  

---

### Gain Condition

For sustained oscillations:

Av ≥ 3  
Av = 1 + (Rf / Ri)

Setting:
- Av = 3 → Rf = 2Ri  

**Implemented using:**
- R5 = 24 kΩ  
- R4 = 10 kΩ  

---

### Amplitude Stabilization

- Diodes are used in the feedback path  
- Prevent:
  - Oscillation decay  
  - Output clipping  
- Maintain stable sine wave amplitude  

---

## 2. Triangular Wave Generator (~10 kHz Carrier)

**Target frequency:** ~10 kHz  

### Formula
f = R2 / (4 × R3 × R1 × C1)

### Selected Components
- R1 = 2.2 kΩ  
- R2 = 10 kΩ  
- R3 = 10 kΩ  
- C1 = 10 nF  

### Calculated Frequency
f ≈ 11.36 kHz  

---

## 3. Comparator (SPWM Generation)

### Operating Condition

- If Vsine > Vtri → Vout = HIGH  
- If Vsine < Vtri → Vout = LOW  

### Output Characteristics

- PWM frequency ≈ carrier frequency  
- Duty cycle follows sinusoidal reference  

---

## Practical Considerations

Observed carrier frequency (~5–10 kHz) differs from the calculated value due to:

- Component tolerances  
- Op-amp non-idealities  
- PCB parasitic effects  

This deviation highlights real-world non-ideal effects such as op-amp bandwidth limitations and practical circuit constraints.
