# BadgerBrigade RC Fire Truck: Controller PCB

## Project Purpose
This main controller PCB is the central hub that coordinates motor control, sensor data acquisition, and communication with an ESP32 camera module and remote controller. The BadgerBrigade RC Fire Truck is designed to remotely assess fire environments using live video streaming and sensor feedback, minimizing risks for firefighters.

## Key Features
- **Remote Monitoring:** Live video stream via ESP32 camera over WiFi
- **Actuator Control:** 4x wheels, water pump, and servo for firefighting actions
- **Sensor Suite:** IMU (LSM6DSMTR), magnetometer (IIS2MDCTR), and EEPROM for motion tracking and data logging

## Hardware Design

### Power Management
- **Input Voltage:** 12V battery
- **Power Rails:**
  - 5V: AP63205WU-7 buck converter (1A rated, input/output capacitors for stability)
  - 3.3V: TLV1117LV33 LDO (0.5A max, thermal vias for heat dissipation)
- **Current Handling:**
  - 5V/3.3V traces and components rated for ≥1A
  - Motors/pump powered directly from battery voltage

### Motor & Actuator Control
- **Motor Drivers:** DRV8251DDAR H-bridges (flyback diodes for inductive kickback)
- **Pump:** MOSFET-controlled (back-EMF managed via clamping circuits)
- **Servo:** Reused lab unit, driven by MOSFET for 5V compatibility

### Sensor Integration
- **IMU/Magnetometer:** Polled continuously for motion tracking
- **EEPROM (SPI):** Stores IMU and motor data every 10 seconds (black-box functionality)

### Communication & Data Handling
- **UART:** Shielded wiring for robust communication with ESP32 (WiFi control/video)
- **I2C:** Interfaces IMU, magnetometer, and IO expander (TCA9534PWR)
- **WiFi:** ESP32 modules handle video streaming and bidirectional control signals

### Mechanical & Safety
- **Mounting:** Secured to chassis via drilled standoffs (4 corners)
- **Environmental Protection:** Non-waterproof design; pump operations avoid direct PCB exposure
- **Speaker Output:** LC filter (10µH inductor + 63nF capacitor) for siren signal smoothing

## Design Challenges & Solutions

### Thermal Management
- Thermal vias under TLV1117LV33 LDO eliminated the need for heatsinks

### Load Transients
- Buck converter stability ensured via calculated capacitor selection

### Budget Constraints ($300)
- Reused servo and prioritized cost-effective ICs (e.g., DRV8251DDAR)

### Component Limitations
- Mandated CY8CPROTO-063-BLE MCU necessitated ESP32 for WiFi
- Most sensors picked were available for free as per project brief

## System Performance
- **Motor Response:** Smooth acceleration/deceleration via H-bridge control
- **Sensor Accuracy:** IMU/magnetometer data fused for directional awareness
- **Fault Handling:** Status LEDs alert for power faults or communication drops

## Future Improvements
- Waterproofing for harsh environments
- Higher-resolution IMU for precise motion tracking