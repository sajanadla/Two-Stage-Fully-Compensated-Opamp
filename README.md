# Two-Stage Miller Operational Amplifier Design

## Project Overview
This project involves the design and simulation of a two-stage Miller operational amplifier (Op-Amp) using **TSMC 0.35μm CMOS technology**. The Op-Amp is designed to meet a specific set of performance requirements while operating with a 3.3V supply voltage and driving a 10pF capacitive load.

The design includes a differential input stage, a gain stage, and an output stage, compensated using Miller capacitance for stability.

---

## Design Specifications

| **Specification**                    | **Target Value**   |
|---------------------------------------|--------------------|
| **Differential Voltage Gain (Avd)**   | ≥ 60 dB            |
| **Output Voltage Swing (OVSR)**       | ≥ 2 V              |
| **Slew Rate (SR)**                    | ≥ 10 V/μs          |
| **Input Common Mode Range (ICMR)**    | ≥ 1.8 V            |
| **Common Mode Rejection Ratio (CMRR)**| ≥ 70 dB            |
| **Unity Gain Bandwidth (GBW)**        | ≥ 8 MHz            |
| **Phase Margin (PM)**                 | ≥ 60° with CL = 10 pF |
| **Power Dissipation (Pdiss)**         | ≤ 1 mW             |
| **Load Capacitance (CL)**             | 10 pF              |
| **Power Supply Voltage (VDD)**        | 3.3 V              |

---

## Design Structure

The two-stage Miller op-amp consists of the following primary stages:

1. **Differential Input Stage**:  
   A differential amplifier with NMOS4 transistors (M1, M2) forming the input pair, and PMOS4 current mirror transistors (M3, M4) providing load and biasing.

2. **Gain Stage**:  
   A common-source amplifier stage (M5, M6) provides the main voltage gain. This stage is cascoded to improve gain and bandwidth.

3. **Output Stage**:  
   A push-pull configuration (M7, M8) drives the load capacitance (CL = 10pF) and ensures the required output voltage swing.

4. **Miller Compensation**:  
   A compensation capacitor (CC = 5pF) is connected between the output of the gain stage and the output node to ensure stability and an adequate phase margin.

---

## Files in the Repository

- **opamp.spice**:  
  Contains the SPICE netlist for the two-stage Miller opamp. This file defines the transistor configuration, power supplies, load capacitance, and compensation circuit.
- **schematic.jpg**:
- **results.jpg**:

- **README.md**:  
  This README file, providing an overview of the project and design specifications.

---

## Usage

### Prerequisites

- SPICE simulator (e.g., LTspice, Ngspice, HSPICE) installed on your system.
- Model files for TSMC 0.35μm CMOS technology.

### Simulation Instructions

1. Ensure that the **model file** (`TSMC_0.35um_CMOS_models.inc`) is correctly referenced in the SPICE netlist (`opamp.spice`).
2. Open the SPICE netlist in your preferred SPICE simulator.
3. Run **AC analysis** to observe the frequency response, gain, and phase margin.
4. Run **Transient analysis** to check the slew rate, output voltage swing, and settling time.
5. Adjust component values (e.g., W/L ratios, compensation capacitor) if needed to optimize performance.

---

## Design Considerations

- **Transistor Sizing (W/L)**:  
  The W/L ratios of the transistors are crucial to meeting the design specifications. The current mirror, differential pair, and gain stage should be optimized for gain, bandwidth, and power dissipation.

- **Compensation Capacitor (CC)**:  
  The value of the Miller compensation capacitor (CC) determines the stability of the amplifier. It must be carefully selected to achieve a phase margin of ≥ 60° with the 10pF load capacitor.

- **Bias Current (Ibias)**:  
  The bias current should be chosen to meet both the power dissipation constraint (Pdiss ≤ 1mW) and to ensure proper operation of the differential input pair.

---
![Alt text for your image](./circuits.JPG)
## Performance Verification

- **Gain and Bandwidth**:  
  Perform AC analysis to verify that the **differential voltage gain (Avd)** is ≥ 60dB, and the **unity gain bandwidth (GBW)** is ≥ 8MHz.

- **Slew Rate**:  
  Perform transient analysis to ensure that the **slew rate (SR)** is ≥ 10V/μs.

- **Output Swing**:  
  Check the transient output swing to verify that the **output voltage swing range (OVSR)** is ≥ 2V.

- **Phase Margin**:  
  Ensure that the phase margin at unity gain bandwidth is ≥ 60° with a 10pF load capacitance.

---

## Future Work

- **Layout Design**:  
  Following successful simulation, a layout can be created using a suitable CMOS layout tool (e.g., Cadence Virtuoso). Post-layout simulations can further refine the design to account for parasitics.



