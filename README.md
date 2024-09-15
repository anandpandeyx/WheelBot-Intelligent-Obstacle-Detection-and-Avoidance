# WheelBot-Intelligent-Obstacle-Detection-and-Avoidance
Sure, here's a detailed README file for your GitHub repository. This README provides an overview of the project, describes how to set up and use the code, and explains the purpose and functionality of each part.

---

# Autonomous Robot with Obstacle Avoidance

## Overview

This project demonstrates how to control a basic autonomous robot using an ultrasonic sensor and L298N motor driver. The robot can move forward, backward, and turn based on obstacle detection. This is accomplished with an Arduino and the NewPing library for the ultrasonic sensor.

## Components

- Arduino board (e.g., Arduino Uno)
- Ultrasonic sensor (HC-SR04)
- L298N Motor Driver
- DC Motors (2)
- Jumper wires
- Breadboard (optional for connections)

## Circuit Diagram

1. **Ultrasonic Sensor (HC-SR04)**
   - `Trig` to Arduino Analog Pin A1
   - `Echo` to Arduino Analog Pin A2
   - `VCC` to Arduino 5V
   - `GND` to Arduino GND

2. **L298N Motor Driver**
   - `IN1` to Arduino Pin 7
   - `IN2` to Arduino Pin 6
   - `IN3` to Arduino Pin 4
   - `IN4` to Arduino Pin 5
   - `OUT1` and `OUT2` to Left Motor
   - `OUT3` and `OUT4` to Right Motor
   - `VCC` to Arduino 5V (or external 5V power supply)
   - `GND` to Arduino GND (and external power supply GND if used)

## Code Description

The provided Arduino code controls the robot using the L298N motor driver and an ultrasonic sensor. Here's a breakdown of the code:

### Libraries

- `#include <NewPing.h>`: Library to handle ultrasonic sensor readings.

### Pin Definitions

- **Motor Pins:**
  - `LeftMotorForward` (Pin 7)
  - `LeftMotorBackward` (Pin 6)
  - `RightMotorForward` (Pin 4)
  - `RightMotorBackward` (Pin 5)
- **Sensor Pins:**
  - `trig_pin` (A1)
  - `echo_pin` (A2)

### Functions

- **`setup()`**
  - Initializes motor pins as outputs.
  - Takes several distance readings to stabilize initial distance measurement.

- **`loop()`**
  - Main control logic:
    - If an obstacle is detected within 20 cm, stop the robot, move backward, and then determine which direction (left or right) has more space.
    - Turn in the direction with more space.
    - If no obstacle is detected, the robot moves forward.

- **`lookRight()` and `lookLeft()`**
  - Simulate right and left sensor sweeps by reading the distance from the sensor.

- **`readPing()`**
  - Reads distance from the ultrasonic sensor and returns the value in cm. If the sensor returns 0 (no object detected), it defaults to 250 cm.

- **Motor Control Functions:**
  - **`moveStop()`**: Stops all motor movements.
  - **`moveForward()`**: Moves the robot forward by setting appropriate motor pins high.
  - **`moveBackward()`**: Moves the robot backward.
  - **`turnRight()`**: Turns the robot to the right.
  - **`turnLeft()`**: Turns the robot to the left.

## Usage

1. **Connect the Components**
   - Follow the circuit diagram to connect the ultrasonic sensor and motor driver to the Arduino.

2. **Upload the Code**
   - Open the Arduino IDE.
   - Copy and paste the provided code into a new sketch.
   - Select your Arduino board and port from the Tools menu.
   - Upload the code to your Arduino.

3. **Power the Robot**
   - Ensure your Arduino and motor driver have adequate power.

4. **Run the Robot**
   - Place the robot on the ground and power it on. The robot should start moving forward. When it detects an obstacle, it will stop, reverse, and choose a direction to turn based on available space.

## Troubleshooting

- **Robot does not move:**
  - Check all connections and ensure the motor driver and motors are powered correctly.
  - Verify that the Arduino code is uploaded correctly and the correct pins are used.

- **Inconsistent distance readings:**
  - Ensure the ultrasonic sensor is mounted securely and is not obstructed.
  - Check the sensor connections and power supply.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contributing

Feel free to fork the repository, make changes, and submit pull requests. If you encounter any issues or have suggestions for improvements, please open an issue in the repository.

---

This README file provides clear instructions and information about the project, making it easy for others to understand and replicate your setup.
