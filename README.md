# Thermostat Control System (Simulink)

This repository contains a Simulink-based simulation of a thermostat system using a Proportional-Integral (PI) controller. The model regulates room temperature by comparing the actual temperature to a setpoint and controlling a virtual heater accordingly. The project uses modular subsystems for clarity and realism, and includes a MATLAB workspace file for parameter initialization.

## Files Included

- `Thermostat.slx` – Simulink model of the complete thermostat system
- `Thermostat.mat` – MATLAB workspace file with parameters (setpoint, gains, etc.)
- `README.md` – Project overview and usage guide

## System Description

The system simulates how a thermostat maintains a desired room temperature using feedback control.

### Main Components

1. **PI Controller**
   - Calculates the error between setpoint and current room temperature.
   - Applies proportional and integral control to generate a heater control signal.
   - Output: `y_k` (control signal for the heater, clamped between 0 and 1)

2. **House Subsystem**
   - Accepts the control signal from the PI controller.
   - Contains two subsystems:
     - **Heater Subsystem**: Simulates heat gain based on the control signal and temperature difference.
     - **Room Subsystem**: Models the thermal dynamics of the room using heat capacity and thermal resistance.

3. **Room Thermal Model**
   - Uses the equation:
     ```
     dT/dt = (Q_gain - (T_room - T_outside)/R) / C
     ```
   - Integrates over time to simulate room temperature changes.

## MATLAB Workspace (`Thermostat.mat`)

This file includes:
- `Kp` and `Ki`: Controller gain values
- `setpoint`: Desired room temperature
- `T_initial`, `T_outside`: Initial and external temperatures
- `C`, `R`: Thermal constants (capacitance and resistance)

Load this workspace before running the simulation:

```matlab
load('Thermostat.mat')
