# Airport Baggage Handling Automation

**A PLC-based system for automating baggage routing at airport check-in and check-out, with real-time monitoring, anomaly detection, and conveyor control.

## Overview

This project automates the baggage handling process in an airport logistics center. It monitors luggage weight (>20kg), X-ray anomalies, and controls conveyor belts (rolls) from check-in to check-out, improving efficiency and reducing errors.

Key components:
- **Check-in**: 3 counters with scales, X-ray checks, labeling, and container counting (max 20 bags).
- **Check-out**: 3 conveyor rolls with sensor-based control and blockage detection.

## Features

- Weight validation at check-in (alarm for >20kg).
- X-ray anomaly detection with manual intervention.
- Automatic container filling and reset.
- Conveyor control:
  - Roll 1: Runs with baggage input.
  - Roll 2: Interlocked with Roll 1 and exit clearance.
  - Roll 3: Always runs with system baggage.
- Real-time supervision via CX-Supervisor.
- Ladder logic implemented in CX-Programmer.

## System Architecture

The system uses:
- **CX-Programmer**: For ladder logic (LADDER diagrams).
- **CX-Supervisor**: For HMI/supervision interface.
- Sensors for baggage presence, scales, X-ray.
- Buttons for manual simulations (overweight, anomalies, blockages).
- Outputs with SET/RSET for reliable state updates.

### Check-In Flow
1. Place baggage on scale (sensor detects).
2. Check weight/X-ray (buttons 2/3 simulate issues → alarm).
3. Tag (button 4) and dispatch (button 5) if OK.
4. Count in container.

### Check-Out Flow
1. Insert on Roll 1 (button 1).
2. Advance to Roll 2 (button 3), detect end (button 4).
3. Clear Roll 2 exit (button 5) → to Roll 3 (button 6).
4. Empty detection stops rolls.

## Technologies

- Omron CX-Programmer (PLC ladder logic).
- CX-Supervisor (HMI).
- Simulated hardware: sensors, buttons, LEDs, scales.
