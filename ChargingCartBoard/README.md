# Charging Cart Board Documentation

## Project Overview
Wisconsin Formula SAE Racing - Charging Cart Board PCB Documentation

## Design Files
- Complete schematic documentation (PDF)
- Comprehensive PCB layout files
- Detailed 3D model visualizations for mechanical verification

## Circuit Sections
### MCUs
- **BMS MCU Configuration**: TM4C Launchpad implementation
- **Key Features**:
  - CAN communication for BMS control
  - ISOSPI interface
  - Multiple GPIO for system monitoring
  - Fault and reset handling
- **Power**: Using 3V3 LDO off of Launchpad for 3V3 Power

### Digital Signals
- **BMS CAN Transceiver**:
  - TCAN1042HVDQ1 implementation
  - Built-in protection features
  - Differential signaling optimization
- **Layout Considerations**:
  - TVS diodes and bus filtering capacitors placed close to connectors
  - Dual grounding vias for bypass capacitors
  - CAN_H and CAN_L routing prioritized over TX/RX

### Power Management
- **Input**: 12V battery source
- **Regulators**:
  - 5V LDO for system components
  - 3.3V rail from MCU
- **Protection**:
  - Reverse voltage protection
  - TVS diodes for transient suppression
  - Fused inputs (FUSE1, FUSE2)

### Shutdown Circuit
- **Safety Features**:
  - BMS fault monitoring
  - IMD fault detection
  - Reset functionality
- **Debug Capabilities**:
  - Status LEDs
  - Test points
  - Jumpers for testing

### TSAL Systems
- **Comparator**:
  - 60V HV monitoring
  - Isolated design with opto-isolation
  - Precision voltage divider network
- **Driver Circuit**:
  - LED control for status indication
  - Timer-based operation (2Hz-5Hz)
  - Configurable timing via RC network

## Technical Documentation
### Design Files
- Detailed schematics in PDF format
- Multi-layer PCB layout documentation
- 3D renders for mechanical integration

## Component Selection Notes
- **MCU**: TM4C series chosen for CAN and GPIO capabilities
- **Transceiver**: TCAN1042HVDQ1 selected for robustness
- **Power Components**: Emphasis on thermal management and protection

## Layout Guidelines
- Critical signal routing prioritization
- Ground plane considerations
- Thermal management requirements
- EMI/EMC best practices implementation

## Debug & Testing
- Test points provided at key nodes
- LED indicators for status monitoring
- Jumper options for fault simulation
- Voltage monitoring points

## Safety Notes
- High voltage presence indicators
- Fault detection systems
- Emergency shutdown procedures
- Required safety protocols