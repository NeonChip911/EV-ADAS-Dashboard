# EV ADAS Dashboard

## 📌 Project Overview

A complete Electric Vehicle Advanced Driver Assistance System (ADAS) Dashboard built during the Embedded Systems Internship at **Emertxe Information Technologies**.

The system uses an STM32F103C8T6 (Blue Pill) microcontroller to read sensor data, process EV dynamics, detect obstacles, and stream telemetry to a Python dashboard over UART.

## 🚀 Features

### Electric Vehicle Monitoring
- Real-time Speed (0-200 km/h)
- State of Charge (SOC) with Range Estimation
- Motor Torque & Power
- Motor Temperature Monitoring
- 3 Drive Modes: ECO, NORMAL, SPORT

### ADAS Safety Features
- Forward Collision Warning (Distance & TTC based)
- Blind Spot Detection (Left & Right)
- Priority-based Alarm System (P0-P3)
- Hysteresis Logic for Stable Alerts

### Vehicle State Machine
- **PARKED**, **READY**, **DRIVING**, **REGEN**, **FAULT**

### Telemetry & Visualization
- UART Communication @ 115200 baud
- Python Dashboard with matplotlib
- Live Speedometer, SOC Gauge, ADAS Bird-Eye View
- Speed History Graph & EV Metrics Panel

## 🛠️ Tech Used

| Category | Tech |
|----------|--------------|
| Microcontroller | STM32F103C8T6 (Blue Pill) |
| Firmware | Embedded C, STM32 HAL, ARM Cortex-M3 |
| Sensors | 3x HC-SR04 Ultrasonic Sensors |
| Simulation | PICSimLab |
| Dashboard | Python, matplotlib, pyserial |
| Communication | UART @ 115200 baud |
| Peripherals | ADC, TIM, GPIO, PWM |

### 🗂️ Project Architecture

| Directory / File | Description |
| :--- | :--- |
| 📁 **Core/** | Contains all C firmware for the microcontroller. |
| ├── 📁 `Inc/` | Header files defining function prototypes and global constants. |
| ├── 📁 `Src/` | Main C implementation files handling core logic. |
| 📄 common.h | Contains shared macros, global configurations, and standard includes used across all modules.
| 📄 `adas.c/.h` | Logic for Advanced Driver Assistance Systems (e.g., obstacle detection). |
| 📄 `ev_control.c/.h` | Core logic for electric vehicle power and motor control. |
| 📄 `ultrasonic.c/.h` | Drivers for reading raw sensor data from ultrasonic modules. |
| 📄 `fault.c/.h` | Error handling, system diagnostics, and fail-safe triggers. |
| 📄 `uart_shell.c/.h` | Serial communication setup to talk to the dashboard. |
| 📁 **Python/** | Contains the desktop-side software. |
| ├── 🐍 `dashboard.py`| The main GUI script for visualizing ADAS data in real-time. |

## 🎥 Demo Video & Architecture

[![EV ADAS Dashboard Demo](https://img.youtube.com/vi/nI4DvmGFNV0/maxresdefault.jpg)](https://youtu.be/nI4DvmGFNV0)

## 🚦 How It Works

```mermaid
graph LR
    A[Sensors & ADC] -->|Distance, Accel, Brake| B(STM32 Processing)
    B -->|Dynamics & State Machine| C{Fault Manager}
    C -->|Clear / Fault State| D[UART 115200]
    D --> E((Python Dashboard))
    
    style B fill:#00b4d8,stroke:#000,color:#fff
    style E fill:#2ecc71,stroke:#000,color:#fff

