Dual Active Bridge (DAB) DC-DC Converter — Simulink Model
Overview

This project implements a Dual Active Bridge (DAB) converter in MATLAB Simulink using Simscape Electrical (Specialized Power Systems) blocks. The DAB is a bidirectional, isolated DC-DC converter widely used in EV charging, renewable energy storage, and solid-state transformer applications due to its high power density and soft-switching capability.

Model Architecture
Two full H-bridges (8x IGBT/Diode switching devices) — primary and secondary active bridges
High-frequency isolation transformer (Linear Transformer block) linking the two bridges
Series RLC branches modeling transformer leakage inductance and filtering
DC voltage source as the input supply
Voltage & current measurement blocks for monitoring input/output electrical quantities
powergui block for simulation solver configuration (Specialized Power Systems)
Control Strategy

Power flow direction and magnitude are controlled via Single-Phase-Shift (SPS) modulation:

A Pulse Generator produces the base switching signal
A Variable Time Delay block phase-shifts the secondary bridge's gating signal relative to the primary bridge
Logical operators combine/condition the gate signals for the IGBT/Diode pairs

The phase-shift angle between the two bridges determines the direction and magnitude of power transfer across the transformer.

How to Run
Open DAB_1_1.slx in MATLAB Simulink (R2021a or later recommended).
Ensure the Simscape Electrical / Specialized Power Systems add-on is installed.
Run the simulation and observe the scopes for:
Input/output voltage and current waveforms
Switching behavior of the H-bridge legs
Adjust the Variable Time Delay block to change the phase-shift angle and observe the effect on power transfer direction/magnitude.
Future Work
 Add closed-loop control (PI / MPC) for output voltage regulation
 Implement Dual-Phase-Shift (DPS) or Triple-Phase-Shift (TPS) modulation to reduce circulating current losses
 Quantify efficiency across load and phase-shift range
 Compare soft-switching (ZVS) boundaries under different loading conditions
