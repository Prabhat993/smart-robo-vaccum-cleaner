🤖 Smart Robo Vacuum Cleaner: Notes
Here are the notes for building the circuit and getting your project up and running.

Core Components You'll Need
Microcontroller: Arduino UNO or Nano (the brain 🧠).

Motor Driver: L298N module is perfect for controlling two DC motors.

Motors & Chassis: A 2WD or 4WD robot chassis kit with DC motors, wheels, and a caster ball.

Power Source: A battery pack. A 7.4V Li-ion or a 9V-12V battery holder is ideal to power the motors. A separate 5V power bank for the Arduino can be helpful but isn't required.

Sensors: An HC-SR04 or SRF05 ultrasonic sensor for obstacle detection.

Communication: An HC-05 or HC-06 Bluetooth module to receive commands from your phone.

Vacuum Mechanism: A small 5V or 12V DC motor with a fan blade attached (like a small computer fan) and a 5V single-channel relay module to turn it on/off.

Wires: Plenty of jumper wires (male-male, male-female).

Circuit and Connections
Connecting everything correctly is the most important step. Always connect the grounds (GND) of all separate power sources together!

1. Powering the L298N Motor Driver
12V Terminal: Connect the positive (+) wire from your 7.4V-12V battery pack here.

GND Terminal: Connect the negative (-) wire from your battery pack here. Also, connect this pin to a GND pin on your Arduino. This is critical.

5V Terminal: This can output 5V. You can use it to power the Arduino by connecting it to the Arduino's VIN pin. Make sure the jumper on the L298N is in place.

2. L298N to Arduino
ENA → Arduino Pin 3

IN1 → Arduino Pin 5

IN2 → Arduino Pin 6

IN3 → Arduino Pin 7

IN4 → Arduino Pin 8

ENB → Arduino Pin 4

3. L298N to Motors
OUT1 & OUT2: Connect to your left motor.

OUT3 & OUT4: Connect to your right motor. (If the robot goes backward when you command forward, just swap the two wires for that motor).

4. Bluetooth Module (HC-05/06) to Arduino
VCC → Arduino 5V

GND → Arduino GND

TXD → Arduino RX (Pin 0)

RXD → Arduino TX (Pin 1)

Important: The HC-05's RX pin is technically 3.3V tolerant. To be safe, use a simple voltage divider (a 1kΩ and a 2kΩ resistor) to step down the Arduino's 5V TX signal.

5. Ultrasonic Sensor (HC-SR04) to Arduino
VCC → Arduino 5V

GND → Arduino GND

Trig → Arduino Pin 9

Echo → Arduino Pin 10

6. Relay and Vacuum Motor
The relay acts as a remote-controlled switch for the vacuum motor, which needs more power than an Arduino pin can supply.

Relay to Arduino:

VCC → Arduino 5V

GND → Arduino GND

IN → Arduino Pin 2

Relay to Vacuum Motor & Power:

Connect the positive (+) terminal of the battery pack to the COM (Common) terminal on the relay.

Connect the NO (Normally Open) terminal on the relay to the positive (+) wire of your vacuum motor.

Connect the negative (-) wire of your vacuum motor to the negative (-) terminal of the battery pack (the common ground).

Installation and Setup Guide
Assemble the Chassis: Build your robot frame, attach the motors, and mount the wheels.

Mount Components: Find good spots for the Arduino, L298N module, breadboard, and battery pack. Mount the ultrasonic sensor at the very front, facing forward.

Wire Everything: Follow the circuit connections above carefully. Use a small breadboard if it helps keep things tidy.

Software & Uploading:

Install the Arduino IDE on your computer.

Download and install the SRF05.h library if you don't have it.

CRITICAL STEP: Disconnect the wires from Arduino pins 0 (RX) and 1 (TX) before uploading your code. The Bluetooth module will interfere with the USB connection used for programming. Reconnect them after the upload is complete.

Bluetooth Pairing:

Power up your robot. The light on the HC-05 module should be blinking rapidly.

On your smartphone, go to Bluetooth settings and scan for devices.

Connect to the "HC-05" device. The default password is usually 1234 or 0000. Once paired, the blinking light will become slower.

Testing:

Download a "Bluetooth Terminal" app from the app store (e.g., "Serial Bluetooth Terminal" on Android).

In the app, connect to the HC-05 module.

Now you can send single characters to control your robot!

f - Forward

b - Backward

o - Vacuum On

p - Vacuum Off (if you use the improved code)# smart-robo-vaccum-cleaner
