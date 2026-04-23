# Arduino Stepper Motor Direction Control

## Overview
This project demonstrates how to control a **Stepper Motor (28BYJ-48)** using an **Arduino Uno** and **ULN2003 driver module**.

![ghgh]()

The motor:
- Rotates **clockwise**
- Then rotates **counterclockwise**

This is a fundamental project for understanding:
- Stepper motor control
- Direction switching
- Basic motion control

---

## Components
- Arduino Uno
- Stepper Motor (28BYJ-48)
- ULN2003 Driver Module
- Jumper Wires
- Breadboard (optional)
- USB Cable

---

## Wiring

### ULN2003 → Arduino
- IN1 → Pin 8
- IN2 → Pin 9
- IN3 → Pin 10
- IN4 → Pin 11
- VCC → 5V
- GND → GND

### Stepper Motor
- Plug directly into ULN2003 module

---

## How It Works
- The Arduino sends signals in sequence to the ULN2003 driver
- The driver energizes motor coils
- This creates rotation step-by-step

---

## Code
```cpp
#include <Stepper.h>

const int stepsPerRevolution = 2048;

Stepper myStepper(stepsPerRevolution, 8, 10, 9, 11);

void setup() {
  myStepper.setSpeed(10);
}

void loop() {
  // Clockwise
  myStepper.step(stepsPerRevolution);
  delay(1000);

  // Counterclockwise
  myStepper.step(-stepsPerRevolution);
  delay(1000);
}
