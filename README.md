# Embedded Parking Garage Control System

STM32-based embedded systems project implementing secure vehicle access control, automated gate operation, and collision prevention for a scaled parking garage prototype.

## Overview

This project is a modular embedded parking garage control system built on an STM32 Nucleo board using C/C++. The system combines access control, gate automation, user feedback, and collision prevention into a single integrated architecture. It was designed to emphasize clean subsystem separation, maintainability, and real-time embedded behavior.

The prototype simulates a secure underground parking setup. A vehicle is detected at the entrance, a user enters an access code through a keypad, and the system opens the gate if authentication succeeds. LED indicators communicate entry status, and an ultrasonic sensor monitors the vehicle’s position to reduce collision risk while parking.

## Key Features

- Vehicle detection at the entrance using an LDR sensor
- Secure keypad-based access control with multiple attempt handling
- Automated gate actuation using a servo motor
- Red/green LED status signaling for gate movement and safe entry
- Ultrasonic collision detection with buzzer alerting
- Exit button for controlled departure
- Reset button for updating the access code
- USB serial communication for debugging and monitoring
- Modular software architecture with subsystem-based organization

## System Behavior

The system follows this operating flow:

1. A vehicle is detected at the entrance.
2. The driver is prompted to enter an access code.
3. If the code is correct, the gate opens and the system signals safe entry.
4. While parking, the ultrasonic sensor monitors distance to the wall.
5. If the vehicle gets too close, the collision alert is triggered.
6. The driver can exit using the exit button.
7. After repeated incorrect code attempts, the system activates a security alarm.

## Hardware

The prototype integrates the following components:

- STM32 Nucleo microcontroller
- Matrix keypad
- LDR sensor
- Ultrasonic sensor
- Positional servo motor
- LCD display
- Red and green LEDs
- Buzzers
- Exit button
- Reset button

The hardware architecture includes a mix of analog, digital, and PWM-connected devices. The project also includes a block diagram and full schematic for signal flow and wiring layout.

## Software Architecture

The software was structured modularly so that each subsystem had a distinct responsibility. The main parking system controller handles initialization and periodic updates, while supporting modules manage tasks such as gate control, collision detection, keypad input, display logic, entry/exit handling, alarms, and serial communication.

### Core modules include:
- `main.cpp`
- `parking_system.cpp`
- `entrance_subsystem.cpp`
- `exit_subsystem.cpp`
- `move_gate.cpp`
- `collision_sensor.cpp`
- `matrix_keypad.cpp`
- `display.cpp`
- `code.cpp`
- `pc_serial_com.cpp`

The system runs on a real-time update cycle of 10 ms to support responsive behavior across subsystems.

## Testing and Results

The system successfully demonstrated the core intended functionality, including:

- accurate vehicle detection
- correct keypad authentication flow
- proper gate opening and closing behavior
- security alarm activation after repeated failed attempts
- ultrasonic collision alerting
- exit button operation
- code reset functionality via serial interface

One known limitation remained in the gate safety mechanism: the system did not fully prevent gate closure when an obstruction was present, indicating a need for further refinement.

## Engineering Focus

A major emphasis of this project was code maintainability. The software was designed with modularity, readable structure, and configurable constants so that debugging, extension, and subsystem-level changes could be made without destabilizing the entire system.

## Challenges

During integration, some modules interfered with others in unexpected ways, especially when combining servo control, LEDs, the buzzer, and the LCD display. Resolving these issues required repeated debugging, incremental testing, and re-establishing stable intermediate versions of the project.

## Future Improvements

Planned improvements include:

- adding RFID-based authentication for stronger access control
- implementing better obstruction detection during gate closure
- improving safety behavior for more realistic deployment scenarios

## Media

- [Project Demo Video](https://drive.google.com/file/d/1EKjXtH5NMyKs-ejD6vYEh3f0iMNzC9Y5/view)
- [Technical Report](./Embedded_Parking_Garage_Control_System_Technical_Report.pdf)

## Contributors

- Ryan Petrauskas
- Brandon Mori
