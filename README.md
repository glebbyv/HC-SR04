# HSRW GoKart Ultrasonic Sensor Library

This library provides a simple interface for using an ultrasonic sensor with an Arduino board. It consists of two files: `ultrasonic.h` and `ultrasonic.cpp`.

## Ultrasonic.h

### Overview
The `ultrasonic.h` header file defines a class `UltraSonic` for interacting with an ultrasonic sensor. It includes necessary Arduino libraries and declares the class members and methods.

### Class Members
- `TrigPin`: An integer representing the Arduino pin connected to the trigger pin of the ultrasonic sensor.
- `EchoPin`: An integer representing the Arduino pin connected to the echo pin of the ultrasonic sensor.

### Public Methods
- `UltraSonic(int Trig, int Echo)`: Constructor method for initializing the ultrasonic sensor with specified trigger and echo pins.
- `void trigger()`: Method for triggering the ultrasonic sensor to send out a pulse.
- `int dist()`: Method for measuring the distance to an object using the ultrasonic sensor and returning the distance in centimeters.

## Ultrasonic.cpp

### Overview
The `ultrasonic.cpp` source file implements the methods declared in `ultrasonic.h`. It includes the necessary Arduino libraries and provides the functionality to interact with the ultrasonic sensor.

### Constructor
- `UltraSonic::UltraSonic(int Trig, int Echo)`: Constructor method for initializing the ultrasonic sensor with the specified trigger and echo pins. It configures the pins as input and output accordingly.

### Public Methods
- `UltraSonic::trigger()`: Method for triggering the ultrasonic sensor to send out a pulse. It sets the trigger pin to LOW, sends a short pulse, and then sets the trigger pin back to LOW.
- `UltraSonic::dist()`: Method for measuring the distance to an object using the ultrasonic sensor. It triggers the sensor, measures the duration of the echo pulse, calculates the distance based on the duration, and returns the rounded distance in centimeters.

## Usage
To use the Ultrasonic Sensor Library in your Arduino project, include the `ultrasonic.h` header file and `ultrasonic.cpp` source file in your project directory. Then, create an instance of the `UltraSonic` class with the appropriate trigger and echo pins. You can then call the `dist()` method to measure the distance to an object.

```cpp
#include "ultrasonic.h"
#include <Arduino.h>

UltraSonic sensor(9, 10); // Trigger pin: 9, Echo pin: 10

void setup() {
  Serial.begin(9600);
}

void loop() {
  int distance = sensor.dist();
  Serial.print("Distance: ");
  if (distance == -1) {
    Serial.println("Out of range");
  } else {
    Serial.print(distance);
    Serial.println(" cm");
  }
  delay(500);
}
