# 🎛️ Multi-Paradigm Industrial Process Controller Tank Automation


![Target](https://img.shields.io/badge/Target-ABB--PLC-blue)
![Software](https://img.shields.io/badge/Software-CODESYS-blue)
![Standard](https://img.shields.io/badge/Standard-IEC_61131--3-orange)
![Status](https://img.shields.io/badge/Status-Functional-brightgreen)
![Author](https://img.shields.io/badge/Author-Mohammed_Gorashi-blue)

![Digital Process Visualization](media/tank_visualization.png)


## 📌 Project Overview
This project presents a high-fidelity industrial control system for a liquid tank process, developed entirely within a **Digital Twin simulation environment**. The system autonomously manages a Pump, Mixer, Heater, and Valve using a master state machine.

The primary engineering objective was to implement a Multi-Paradigm Architecture, utilizing all six industrial programming languages defined by the IEC 61131-3 standard to handle specific task requirements—from safety-critical interlocks to complex thermal mathematical modeling.

## 🚀 Key Technical Features
 Full-Spectrum Language Implementation 
     SFC (Sequential Function Chart) Manages high-level system states and transitions.
     ST (Structured Text) Handles complex scaling math and warm-up threshold logic.
     LD (Ladder Diagram) Manages safety-critical Offline and Emergency interlocks.
     FBD (Function Block Diagram) Controls system-wide variable initialization and reset routines.
     CFC (Continuous Function Chart) Manages real-time Operation mode for continuous process loops.
     IL (Instruction List) Implements low-level corrective logic for the Stability fault-handling mode.
 Digital Process Simulation A custom-coded physics engine simulates liquid dynamics, thermal gaindecay, and actuator response times every 500ms to provide a realistic testing environment.
 Advanced Signal Scaling Implements a precision scaling block that converts raw 14-bit PID values (0-16383) into engineering units for Level (0-100%) and Temperature (0-1000°C).
 Self-Correcting Stability Logic An autonomous safety layer that monitors for HHLL Level and HH Temperature alarms, triggering corrective Stability routines with 10-second confirmation delays.
 Performance Analytics Engine Automatically logs system reliability data, including total startup cycles and a precision timer (HMS) tracking time spent in corrective modes.

## 🛠️ Software Stack
 IDE ABB CODESYS V2.3  V3.5.
 Standard IEC 61131-3.
 HMIVisualization Integrated CODESYS Visualization for real-time process monitoring.

## 🧠 System State Machine & Logic
The controller transitions through five distinct operational phases

1. OFFLINE (LD) Hardware is de-energized; all actuators are locked in a safe state.
2. INIT (FBD) System variables are cleared, and analog sensors are calibrated.
3. STARTUP (ST) The tank fills to 40-70% and pre-heats to 300-350°C before engaging the mixer.
4. OPERATION (CFC) The main production loop maintains liquid level (20-80%) and temperature (400-500°C) while managing the discharge valve.
5. STABILITY (IL) Triggered by system faults; uses low-level instruction-based logic to force the system back into safe operating bounds.


---
Developed by Mohammed Gorashi as a master-level demonstration of industrial automation and IEC 61131-3 standards.
