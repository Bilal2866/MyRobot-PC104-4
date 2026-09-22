# STM32 PC-104 Robotic Control System

<p align="center">
  <img src="assembled%20pcb.png" width="600">
</p>

## Project Overview

This project is a modular embedded robotic control system built around the **STM32 NUCLEO-64 F303RE**. The main goal was to design, manufacture, assemble, and test custom PCBs capable of controlling multiple motors while supporting communication between different parts of the system.

The system uses a **PC-104-inspired three-board architecture** consisting of:

- Power Supply Board
- Motor Driver Board
- Communication Board

The project covered the full PCB development process, including schematic design, PCB layout, component selection, manufacturing, soldering, embedded programming, hardware testing, and debugging.

This project was completed as part of **ESE Project IV** in the Electronic Systems Engineering program at Conestoga College.

---

## System Overview

**Microcontroller:** STM32 NUCLEO-64 F303RE  
**PCB Design:** Altium Designer  
**Architecture:** PC-104-inspired modular PCB stack  
**Communication:** CAN Bus, UART  
**Motors:** 2 × DC Motors, 1 × Stepper Motor, 1 × Servo Motor  
**Assembly:** Reflow and Through-Hole Soldering  
**Programming:** Embedded C / STM32  
**Testing:** Continuity Testing, Power Testing, Breadboard Prototyping, Hardware Debugging

---

## Key Features

- Three custom-designed PCBs
- STM32 NUCLEO-64 F303RE control
- CAN bus communication
- UART communication and debugging
- DC motor control
- Stepper motor control
- Servo motor control
- H-bridge motor driver circuitry
- Encoder and limit switch support
- Custom multi-voltage power system
- PC-104-style board stacking
- Expandable architecture for future sensors and camera integration

---

## PCB Architecture

The system was separated into three PCBs so that power, motor control, and communication could be developed and tested independently.

### 1. Power Supply Board

The Power Supply Board was designed to take a **15 V battery input** and provide the different voltage levels required throughout the system.

Designed outputs:

- 12 V
- 5 V
- 3.3 V

The board included switching and linear voltage regulation along with the supporting capacitors, inductors, diodes, and power distribution circuitry.

<p align="center">
  <img src="Images/power-board-3d.png" width="450">
</p>

---

### 2. Motor Driver Board

The Motor Driver Board was designed to control the different actuators used by the robotic platform.

Supported hardware included:

- 2 × DC motors
- 1 × Stepper motor
- 1 × Servo motor
- H-bridge motor control
- Encoder feedback
- Limit switches

<p align="center">
  <img src="Images/motor-driver-3d.png" width="450">
</p>

---

### 3. Communication Board

The Communication Board interfaces with the **STM32 NUCLEO-64 F303RE** and provides communication and control connections for the system.

The board supports:

- CAN Bus
- UART
- GPIO
- Motor control signals
- Connections for additional peripherals

<p align="center">
  <img src="Images/communication-board-3d.png" width="450">
</p>

---

## Communication

### CAN Bus

CAN communication was incorporated into the system using a CAN transceiver on the communication PCB.

Working with CAN provided practical experience with a communication protocol commonly used in automotive and embedded systems.

### UART

UART was used throughout development for communication, testing, and debugging with the STM32.

It was especially useful during subsystem testing and hardware/software integration.

---

## Motor Control

The robotic platform was designed to work with three different types of motors.

### DC Motors

Two DC motors were used as part of the robotic drive system.

### Stepper Motor

A stepper motor was controlled through the motor driver circuitry and STM32.

### Servo Motor

Servo control was also implemented through the STM32-based control system.

DC, stepper, and servo motor operation was successfully demonstrated during subsystem testing.

---

## PCB Design & Manufacturing

All three PCBs were designed using **Altium Designer**.

The PCB development process included:

- Schematic design
- Component selection
- PCB layout
- Trace routing
- Ground and power plane design
- High-current routing
- Component placement
- Design Rule Checks
- Gerber generation
- Manufacturer review
- Design revisions
- PCB fabrication

The designs went through multiple revisions before manufacturing. Manufacturer feedback helped identify issues including wiring corrections and a missing VCC plane that needed to be corrected before fabrication.

---

## PCB Assembly

After manufacturing, the boards were assembled using a combination of:

- Reflow soldering
- Solder paste
- Surface-mount component assembly
- Manual through-hole soldering

After assembly, the boards were visually inspected and continuity tested before powered testing.

<p align="center">
  <img src="Images/assembled-pcb.jpg" width="500">
</p>

---

## Testing & Debugging

A large part of this project involved hardware bring-up and troubleshooting.

Testing included:

- Visual PCB inspection
- Continuity testing
- Voltage measurements
- Power testing
- Breadboard prototyping
- STM32 debugging
- UART testing
- Motor testing
- Hardware/software integration

Several issues were discovered during testing that required further investigation.

---

## Engineering Challenges

### Power Supply Board

The Power Supply Board successfully passed continuity testing but did not produce the expected voltage outputs when powered.

This showed that continuity testing alone is not enough to verify the operation of a power circuit.

The issue also highlighted the importance of:

- Testing power circuits under load
- Following switching regulator layout recommendations
- Adding test points
- Performing staged testing before full system integration

---

### Motor Driver Debugging

During testing, the stepper motor initially failed to operate.

The circuit was recreated on a breadboard to isolate the problem. During debugging, it was discovered that the **EN1 and EN2 enable pins** of the motor driver were incorrectly connected to ground instead of VCC.

After correcting the configuration, stepper motor operation was restored and the DC and servo motors were also successfully demonstrated.

---

### System Grounding

Another issue discovered during integration was the lack of a proper common ground connection between the three PCBs.

Although each PCB had its own ground plane, the boards did not share the required common ground reference.

This was an important lesson in considering the complete system during PCB design rather than treating each PCB only as an independent circuit.

---

## What I Learned

This project provided hands-on experience with the complete embedded hardware development process, including:

- STM32 development
- Embedded C
- Altium Designer
- Schematic design
- PCB layout
- PCB manufacturing
- Component selection
- CAN Bus
- UART
- DC motor control
- Stepper motor control
- Servo motor control
- Reflow soldering
- Through-hole soldering
- Hardware bring-up
- Reading component datasheets
- Breadboard prototyping
- Hardware/software integration
- PCB troubleshooting
- System-level grounding
- Design revisions

One of the biggest lessons from the project was that a PCB passing schematic checks and continuity testing does not necessarily mean that it will work correctly when powered.

Testing individual subsystems early and considering how all boards interact with each other is just as important as designing the individual circuits.

---

## Project Status

### Completed

- [x] System architecture
- [x] Three PCB schematics
- [x] PCB layouts
- [x] PCB manufacturing
- [x] Component procurement
- [x] PCB assembly
- [x] Continuity testing
- [x] STM32 development
- [x] UART communication
- [x] CAN hardware integration
- [x] DC motor control
- [x] Stepper motor control
- [x] Servo motor control
- [x] Initial hardware testing and debugging

### Future Improvements

- [ ] Redesign and validate Power Supply Board
- [ ] Correct Motor Driver PCB configuration
- [ ] Implement common ground across all boards
- [ ] Complete full board-to-board integration
- [ ] Reduce three-board design to one or two PCBs
- [ ] Add onboard debugging LEDs and test points
- [ ] Add wireless/Bluetooth communication
- [ ] Integrate camera
- [ ] Add additional sensors
- [ ] Develop mechanical enclosure/platform

---

## Repository Structure

```text
STM32-PC104-Robotic-Control-System/
│
├── README.md
│
├── Images/
│   ├── assembled-pcb.jpg
│   ├── power-board-3d.png
│   ├── motor-driver-3d.png
│   └── communication-board-3d.png
│
├── Hardware/
│   ├── Power-Supply/
│   ├── Motor-Driver/
│   └── Communication/
│
├── Software/
│
├── Documentation/
│
└── Demo/
```

---

## Future Development

Future development will focus on improving system reliability and reducing the complexity of the current three-board prototype.

Possible improvements include combining the system into one or two PCBs, redesigning the power supply, adding onboard debugging indicators, integrating wireless communication, and adding camera and sensor support.

The long-term goal is to develop the prototype into a more compact and reliable robotic embedded control platform.

---

## Project Team

**Bilal Hussain Mohammed**  
Flavius Dica  
Noor Al-Massri

Electronic Systems Engineering  
Conestoga College

**ESE Project IV – Winter 2026**

---

## Author

**Bilal Hussain Mohammed**

Electronic Systems Engineering Student  
Conestoga College

GitHub: **Bilal2866**
