 MotorRelayControlForSutter.ino
This IoT project controls a relay and a stepper motor rotation. The system is designed to activate the relay and trigger motor rotations using serial commands, making it suitable for automation and motor control Sutter.
 IoT Relay and Stepper Motor Control System

 Overview
This IoT project controls a relay and a stepper motor using an Arduino-based system. The project is designed to activate the relay and trigger motor rotations through serial commands, making it ideal for automation and motor control setups.

 Features
- Relay Control**: Activate a relay for a specified duration using serial commands.
- Stepper Motor Control: Perform motor rotations in both clockwise and counterclockwise directions, replacing traditional LED blinking indicators.
- Serial Command Interface**: Simple command-based interaction for relay and motor operations.

 How It Works
1. The system listens for serial commands via the serial monitor.
2. Sending the command `1000` initiates the following sequence:
   - Activates the relay for 1 second.
   - Starts a stepper motor rotation:
     - Clockwise for a specified number of steps.
     - Pauses briefly.
     - Counterclockwise for the same number of steps.
3. The motor rotation replaces traditional LED blinking as an indicator of the system's activity.

 Hardware Requirements
- Microcontroller: Arduino (or compatible device)
- Relay Module
- Stepper Motor: With driver (e.g., A4988 or similar)
- Power Supply: As per the motor and relay specifications
- Connecting wires and a breadboard (optional)

 Software Requirements
- Arduino IDE
- Serial Monitor (or any terminal software)

 Usage Instructions
1. Setup:
   - Connect the relay and stepper motor according to the pin configuration.
   - Upload the `MotorRelayControl.ino` file to your Arduino board.
2. Run:
   - Open the serial monitor at `115200` baud rate.
   - Send the command `1000` to initiate the relay and motor sequence.
3. Observe:
   - The relay activates for 1 second.
   - The stepper motor performs rotations in both directions.

 Example Command
- Command: `1000`
  - Activates the relay for 1 second.
  - Rotates the motor clockwise and counterclockwise.

 Applications
- Home automation
- Industrial motor control
- IoT-based relay switching systems


