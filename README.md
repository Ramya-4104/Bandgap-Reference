# Bandgap Voltage Reference 

A **temperature-compensated CMOS Bandgap Voltage Reference (BGR)** designed and simulated in **Cadence Virtuoso using 180nm CMOS technology**. The design combines **PTAT (Proportional-To-Absolute-Temperature)** and **CTAT (Complementary-To-Absolute-Temperature)** components to generate a stable reference voltage across temperature.

> **Project Status:** Completely understood the BGR operation, built the circuit, and tested the schematic using DC, AC, and transient analysis.

---

## 1. Project Overview

This project focuses on the design and simulation of a **CMOS Bandgap Voltage Reference** for generating a stable on-chip reference voltage with low temperature dependence.

The BGR integrates:

- PTAT and CTAT voltage components for temperature compensation.
- A precision single-stage OTA for closed-loop regulation.
- A CMOS startup circuit to avoid the zero-current metastable operating point.
- Cadence Virtuoso simulations for DC, temperature, and AC/PSRR characterization.
- 180nm CMOS technology for circuit implementation.

---

## 2. Importance of Bandgap Reference Circuit in Analog IC Design

A reliable voltage reference is a fundamental building block in many analog and mixed-signal integrated circuits because other circuit blocks often require a voltage that remains relatively insensitive to **temperature, supply variation, and circuit operating conditions**.

A BGR is important because it can provide a stable reference for blocks such as:

- **ADC/DAC reference generation**
- **Bias and current-reference circuits**
- **Voltage regulators and power-management circuits**
- **Operational amplifiers and analog front ends**
- **PLL and clocking circuits**
- **Sensor interfaces**
- **Data converters and mixed-signal systems**

The key idea is to combine a voltage with a **negative temperature coefficient (CTAT)** and a voltage with a **positive temperature coefficient (PTAT)** such that their temperature dependencies partially cancel.

Conceptually:

\[
V_{REF} = V_{CTAT} + V_{PTAT}
\]

With appropriate scaling of the PTAT component, the resulting reference voltage can remain comparatively stable over temperature.

---

## 3. Objective

The main objectives of the project were:

1. Design a **temperature-compensated Bandgap Voltage Reference** in 180nm CMOS.
2. Generate a stable reference voltage using **PTAT and CTAT** components.
3. Design a precision **single-stage OTA** for closed-loop bandgap regulation.
4. Implement a **CMOS startup circuit** to prevent the bandgap core from remaining in the zero-current metastable state.
5. Characterize the circuit across temperature and frequency.
6. Evaluate the resulting **reference-voltage stability, temperature coefficient, power consumption, and PSRR**.

---

## 4. Motivation

Analog and mixed-signal ICs require stable bias and reference voltages even when the surrounding environment changes.

A reference generated directly from a supply or a single semiconductor device can vary significantly with temperature and process conditions. A bandgap reference addresses this problem by exploiting two opposing temperature-dependent voltage components.

The project therefore focuses on understanding and implementing the fundamental techniques used to obtain a stable on-chip reference in CMOS technology.

---

## 5. Key Features

- **180nm CMOS** implementation
- PTAT + CTAT temperature compensation
- Precision **single-stage OTA**
- Closed-loop bandgap regulation
- CMOS startup circuit
- Stable reference voltage of approximately **1.26 V**
- Approximately **3 mV variation** over the specified temperature range
- **15 ppm/°C** temperature coefficient
- **200 µW** power consumption
- **42.78 dB PSRR** at room temperature
- Cadence Virtuoso DC and AC characterization

---

# 6. Design Architecture

## 6.1 Functional Architecture

The overall operation can be represented as:

```text
                    ┌──────────────────┐
                    │   CTAT Component │
                    │ Negative TC      │
                    └────────┬─────────┘
                             │
                             ▼
                       ┌───────────┐
                       │ Summation │──────► VREF
                       │ / Scaling │
                       └─────▲─────┘
                             │
                    ┌────────┴─────────┐
                    │  PTAT Component  │
                    │ Positive TC      │
                    └──────────────────┘

                         ▲
                         │
                  Closed-loop control
                         │
                  ┌──────┴──────┐
                  │ Single-stage│
                  │     OTA     │
                  └─────────────┘

                  ┌──────────────┐
                  │ Startup      │
                  │ Circuit      │
                  └──────────────┘
```

The PTAT and CTAT components are combined so that their temperature dependencies compensate each other. The OTA provides the required closed-loop regulation, while the startup circuit ensures that the bandgap does not remain in the zero-current state.

---

## 6.2 Circuit Components

### PTAT and CTAT Generation

The reference voltage is obtained by combining the positive and negative temperature-dependent components.

- **CTAT:** Provides a voltage component with negative temperature dependence.
- **PTAT:** Provides a voltage component with positive temperature dependence.
- Proper scaling of these components produces a temperature-compensated reference.

<img width="594" height="796" alt="Screenshot 2026-08-29 124938" src="https://github.com/user-attachments/assets/904779b3-f9cb-4a7f-a6fb-fd51c4c77e4a" />


### Precision OTA

A single-stage OTA is used in the closed-loop regulation of the bandgap core.

The OTA provides the feedback mechanism required to establish the operating point of the reference circuit.

### Startup Circuit

A CMOS startup circuit is included to prevent the bandgap core from settling at the undesirable **zero-current metastable state**.

---

# 7. Design Methodology

The design was developed in the following sequence:

1. Define the required reference-voltage and temperature-stability targets.
2. Develop the **PTAT and CTAT components**.
3. Design the **single-stage OTA** required for closed-loop regulation.
4. Integrate the OTA, PTAT/CTAT components, and startup circuit.
5. Verify the DC operating point.
6. Perform temperature sweeps to evaluate reference-voltage stability.
7. Perform AC simulations to characterize **PSRR**.
8. Evaluate temperature coefficient, power consumption, and reference-voltage variation.

---

# 8. Technology and Tools

| Item | Details |
|---|---|
| Technology | 180nm CMOS |
| Design Environment | Cadence Virtuoso |
| Circuit Type | CMOS Bandgap Voltage Reference |
| OTA | Single-stage precision OTA |
| Reference Generation | PTAT + CTAT |
| Startup | CMOS startup circuit |
| Analysis | DC / Temperature Sweep / AC / PSRR |

---

# 9. Specifications and Achieved Results

| Parameter | Result |
|---|---:|
| Technology | 180nm CMOS |
| Reference Voltage | ~1.26 V |
| Temperature Range | -40°C to +125°C |
| Reference Voltage Variation | ~3 mV |
| Temperature Coefficient | 15 ppm/°C |
| Power Consumption | 200 µW |
| PSRR at Room Temperature | 42.78 dB |

The project description reports a stable **1.26 V reference** with approximately **3 mV variation** across **-40°C to +125°C**, a **15 ppm/°C temperature coefficient**, **200 µW power consumption**, and **42.78 dB PSRR at room temperature**.

---

# 10. Simulation Results

## 10.1 Reference Voltage vs Temperature

The Cadence DC simulation shows the reference voltage remaining close to **1.26 V** over temperature.

<img width="940" height="529" alt="image" src="https://github.com/user-attachments/assets/e717ecd7-1a2d-476d-9d69-548532dd7eb6" />


The simulation demonstrates the temperature-compensation behavior of the PTAT and CTAT components.

---

## 10.2 Temperature Sweep

Additional temperature-sweep simulations were performed to examine the stability of the reference voltage.

![VREF Temperature Sweep](BGR_assets/vref_temperature_sweep.png)

---

## 10.3 Reference Voltage Detail

The reference-voltage response around the operating region is shown below.

![VREF Temperature Detail](BGR_assets/vref_temperature_detail.png)

---

## 10.4 PSRR at Different Temperatures

The AC simulations were used to evaluate the power-supply rejection behavior of the reference.

### PSRR at 40°C

![PSRR at 40C](BGR_assets/psrr_40C.png)

The documented result at 40°C is approximately **42.5 dB** in the plotted region.

### PSRR at Room Temperature

![PSRR at Room Temperature](BGR_assets/psrr_room_temperature.png)

The project description reports approximately **42.78 dB PSRR at room temperature**.

### PSRR at Negative Temperature

![PSRR at Negative Temperature](BGR_assets/psrr_negative_temperature.png)

The available simulation data reports:

| Temperature | PSRR |
|---:|---:|
| -40°C | -44.16 dB |
| 0°C | -43.3 dB |
| 40°C | -42.5 dB |
| 80°C | -41.5 dB |

The PSRR values are shown with the sign convention used in the Cadence plots; the corresponding rejection magnitudes are approximately 44.16 dB, 43.3 dB, 42.5 dB, and 41.5 dB.

### PSRR Temperature Sweep

![PSRR Temperature Sweep](BGR_assets/psrr_temperature_sweep.png)

---

# 11. Verification Summary

The design was evaluated using:

- DC operating-point analysis
- Temperature sweep
- Reference-voltage variation analysis
- AC analysis
- PSRR characterization

The main verification targets were reference-voltage stability, temperature dependence, and supply-noise rejection.

---

# 12. References
- Analog IC Design by Prof. Dr. Nagendra Krishnapura (NPTEL Course)
- The Design of a Low-Voltage Bandgap Reference by Behzad Razavi https://share.google/792wx9waopxL3tVIu

---

## Author

**K Ramya**  
B.Tech — Electronics and Communication Engineering  
Indian Institute of Technology Guwahati

**Project Guide:** Prof. Dr. Mahima Arrawatia, IIT Guwahati
