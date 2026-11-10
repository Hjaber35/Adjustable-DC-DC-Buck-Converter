# Adjustable DC-DC Buck Converter

## Project Overview

Design and development of an adjustable synchronous DC-DC buck converter using LTspice for circuit simulation and KiCad for schematic capture and PCB layout.

The project focuses on power electronics design, component selection, switching efficiency, voltage regulation, thermal management, and protection circuitry.

## Target Specifications

Target Specifications

Converter Topology: Synchronous Buck
Input Voltage: 4–40 V DC
Adjustable Output Voltage: 1.25–37 V DC
Maximum Output Current: Up to 3 A
Control Method: Analog PWM with voltage feedback
Simulation Software: LTspice
PCB Design Software: KiCad

*These are preliminary design targets. Achievable output voltage and current depend on input voltage, component ratings, thermal limits, and converter operating conditions. As a step-down converter, the output voltage must remain below the input voltage.*

## Development Plan

**Phase 1 — Circuit Design and Simulation**
- Select a suitable buck controller and power-stage components.
- Calculate inductor and capacitor requirements.
- Design the adjustable voltage-feedback network.
- Simulate startup behavior, switching waveforms, output ripple, and load response.

**Phase 2 — Design Optimization**
- Evaluate conduction and switching losses.
- Implement current limiting and protection circuitry.
- Analyze efficiency and component thermal requirements.
- Validate operation across selected input and output conditions.

**Phase 3 — PCB Design**
- Develop the schematic and PCB layout in KiCad.
- Optimize high-current paths, grounding, and switching-loop placement.
- Verify footprints, component ratings, and electrical connections.
- Prepare manufacturing files and a bill of materials.

## Project Status

**In Progress — Design and Simulation**

Hardware performance has not yet been validated. Simulation results, design calculations, PCB files, and test documentation will be added as development progresses.
