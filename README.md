# Adjustable DC-DC Buck Converter

## Project Overview

Design and development of an adjustable synchronous DC-DC buck converter based on the LTC3895 controller.

The project uses LTspice for switching simulations, LTpowerCAD for loop compensation and power-stage analysis, and KiCad for planned schematic capture and PCB layout.

The design focuses on voltage regulation, component selection, efficiency, thermal performance, and protection circuitry. Control is analog and requires no firmware.

## Target Specifications

| Parameter | Design Target |
|---|---|
| Topology | Synchronous buck |
| Controller | LTC3895 |
| Input voltage | 4–40 V DC |
| Adjustable output voltage | 1.25–37 V DC |
| Continuous output current | Up to 3 A, subject to validation |
| Switching frequency | Approximately 202 kHz |
| Primary operating point | 26 V input → 19 V output |
| Control | Analog PWM with voltage feedback |
| Simulation tools | LTspice and LTpowerCAD |
| PCB design tool | KiCad |

These are preliminary targets, not guaranteed operating specifications.
Output voltage must remain below input voltage with sufficient headroom
for regulation. The full voltage range, including startup at 4 V input,
has not been validated. Available output current depends on component
ratings, losses, and thermal limits.

## Current Simulation Baseline

| Component or Network | Value |
|---|---|
| Inductor | 47 µH |
| Modeled inductor DCR | 20.7 mΩ |
| Current-sense resistor | 10 mΩ |
| Output bulk capacitance | 600 µF, equivalent ESR 2.5 mΩ |
| Output ceramic capacitance | 22 µF, ESR 6 mΩ in LTspice |
| High-side and low-side MOSFETs | BSC082N10LS |
| Compensation resistor | 3.32 kΩ |
| Series compensation capacitor | 47 nF |
| ITH shunt capacitor | 1 nF |
| Feedback feedforward capacitor | 4.7 nF |
| Feedback lower resistor | 10 kΩ |

The upper feedback resistor changes with the selected output voltage.
These are simulation values; final physical parts and ratings remain
under review.

## Simulation Results

Ten unique operating points were evaluated using the same power-stage
and compensation values.

| Output Voltage | Tested Input Voltages |
|---|---|
| 5 V | 15, 26, 40 V |
| 12 V | 15, 26, 40 V |
| 19 V | 22, 26, 30, 40 V |

### Load-Step Test

A resistive load draws approximately 1 A at the target output voltage.
A parallel current sink adds 2 A at 20 ms and removes it at 30 ms,
using 200 ns rise and fall times.

Across these nominal simulations:

- Average inductor current was approximately 3 A during the high-load interval.
- Output excursions remained within ±3% of the target during the measured load transitions.
- Measured steady-state output ripple ranged from approximately 0.66 to 3.73 mV peak-to-peak.

The ±3% figure is a simulation comparison benchmark, not a guaranteed
hardware specification.

### Primary Operating Point: 26 V → 19 V

| Measurement | LTspice Result |
|---|---|
| Average output voltage at approximately 3 A | 18.9955 V |
| Output ripple | 1.49 mV peak-to-peak |
| Minimum voltage during load application | 18.8284 V |
| Maximum voltage during load removal | 19.1637 V |
| Maximum measured load-step deviation | Approximately 0.90% |
| Peak inductor current during the load transition | 3.324 A |

The inspected nominal startup waveform rises smoothly toward 19 V
without visible overshoot at the displayed scale.

### Loop Analysis

LTpowerCAD reported the following results at 19 V output and 3 A:

| Input Voltage | Bandwidth | Phase Margin |
|---|---|---|
| 22 V | 7.94 kHz | 79.82° |
| 26 V | 7.94 kHz | 81.85° |
| 40 V | 7.94 kHz | 85.92° |

These are model-based estimates. Stability across the full adjustable
range, component tolerances, and physical hardware remains to be checked.

### Known Limitations

- LTpowerCAD and LTspice predict different output ripple at the primary operating point: approximately 51.06 mV and 1.49 mV peak-to-peak, respectively. This discrepancy remains unresolved.
- Earlier 1.25 V output tests showed larger load-step deviations; the results above do not establish ±3% performance at 1.25 V.
- Actual inductor selection and saturation/current ratings remain pending.
- Efficiency, thermal performance, protection behavior, and component-tolerance effects are still under evaluation.
- No physical hardware has been tested.

## Remaining Work

1. Complete stability and loss checks at representative operating points.
2. Select actual components and verify voltage, current, and thermal ratings.
3. Validate loaded startup, current limiting, and short-circuit recovery.
4. Design and verify reverse-polarity and input-transient protection.
5. Complete the KiCad schematic and PCB layout.
6. Review footprints, grounding, high-current paths, and switching loops.
7. Prepare the bill of materials and manufacturing files.
8. Assemble and test the prototype.

## Project Status

**In progress - simulation and component validation.**

The current baseline has completed nominal regulation and load-step
tests at ten operating points. PCB fabrication and hardware validation
are pending.
