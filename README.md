# Blynk IoT Stepper Robotic Arm

A 4-DOF (Degrees of Freedom) robotic arm controlled globally via the Blynk IoT platform. This project utilizes precise 28BYJ-48 stepper motors driven by the `AccelStepper` library, allowing for accurate articulation, variable speed control, and remote operation from any mobile device.

**Quick Mental Model:** You press buttons or move sliders on the Blynk mobile app -> Commands are routed via the cloud to the ESP32 -> The ESP32 translates virtual pin data into precise, non-blocking step commands to drive the stepper motors.

## Features
- Global Remote Control: Fully integrated with Blynk IoT, allowing control of the arm from anywhere in the world.
- - High-Precision Steppers: Uses 28BYJ-48 stepper motors via ULN2003 drivers to provide exact positional control over the arm joints.
  - - Variable Speed Control: Dynamic maximum speed adjustment implemented via Blynk sliders, bypassing default stepper slowness.
   
    - ## Architecture
    -   [Blynk App]                 [Cloud]                  [Hardware Layer]
    -          |                         |                            |
    -         UI Buttons -----------+       |       +---------------> 28BYJ-48 (Base)
    -                              |   +---v---+   |  ULN2003      > 28BYJ-48 (Elbow 1)
    -                             UI Sliders -----------+-->| ESP32 |---+---------------> 28BYJ-48 (Elbow 2)
    -                                                  |   +---+---+   |               > 28BYJ-48 (Wrist)
    -                                              
