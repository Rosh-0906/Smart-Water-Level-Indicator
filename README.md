# Smart-Water-Level-Indicator
# IoT-Based Smart Water Level Monitor

A connected hardware solution that measures fluid depth in real-time. This project uses an Arduino Uno and an ultrasonic sensor to track water levels inside a reservoir, provide visual feedback through local indicator lights, and stream data to a cloud network for remote analysis.

## Project Objective
The goal of this project is to build an automated fluid tracking system. By leveraging ultrasonic waves, the system calculates the exact volume of water remaining in a container and transmits this telemetry online for seamless remote monitoring.

---

## Hardware Requirements
* **Microcontroller:** Arduino Uno development board
* **Prototyping Platform:** Standard Breadboard
* **Primary Sensor:** HC-SR04 Ultrasonic Distance Sensor
* **Visual Output:** Multi-colored LEDs (for visual status alerts)
* **Hardware Links:** Solid-core jumper wires
* **Testing Medium:** A deep jar or transparent water tank

---

## Wiring Schema

### Ultrasonic Sensor Configuration

| Sensor Pin | Arduino Pin | Purpose |
| :--- | :--- | :--- |
| **VCC** | 5V | Positive Power Line |
| **GND** | GND | Common Ground Line |
| **TRIG** | D8 | Trigger Pulse Output |
| **ECHO** | D9 | Echo Return Input |

### LED Integration
* **Data Interface (D2 to D13):** Configurable digital pins reserved for managing status LEDs, warning buzzers, and sensor lines.

---

## Implementation Steps

### Phase 1: Environment & Hardware Setup
1. **Initialize IDE:** Link the Arduino Uno to your PC using a USB data cable. Select the appropriate hardware target and communication port in the Arduino IDE.
2. **Wire the Sensor:** Establish connections between the HC-SR04 module and the microcontroller according to the pin configuration map.
3. **Assemble the Indicators:** Mount the status LEDs on the breadboard, connecting them to dedicated digital output pins through protective resistors.

### Phase 2: Software Development & Calibration
4. **Define Signal Variables:** Allocate memory variables to capture the echo duration (microseconds) alongside calculated dimensions in both centimeters and inches.
5. **Establish Bounds:** Measure your physical testing container to determine minimum and maximum water depth limits for your conditional loops.
6. **Set Pin Modes:** Initialize the controller's I/O architecture inside `setup()`, defining the trigger pin as a digital output and the echo pin as a digital input.

### Phase 3: Distance Tracking Logic
7. **Generate Sonic Pulses:** Clear the line by driving the trigger pin low, then cycle it high for exactly 10 microseconds to fire the acoustic burst.
8. **Measure Time-of-Flight:** Capture the incoming pulse width from the echo pin to determine how long the sound wave took to bounce back.
9. **Calculate Depth:** Convert the microsecond time frame into precise distance metrics based on the standard speed of sound.
10. **Map Thresholds:** Write logic branches to turn on specific LEDs sequentially as the liquid surface gets closer to the sensor array.

### Phase 4: Verification & Deployment
11. **Flash the Chip:** Verify the sketch code for syntax errors and upload it to the memory of the Arduino board.
12. **System Benchmark:** Fix the ultrasonic sensor face down over an open container of water. Maintain a strict 90-degree angle relative to the liquid surface to prevent data scattering and read errors.

---

## Technical Considerations
* **Sensor Angle:** Keep the face of the sensor strictly perpendicular to the target liquid. Offsets beyond 15 degrees will cause severe echo reflection failures.
* **Multi-LED Alerts:** Remove any static low-state constraints from your conditional blocks if you want multiple indicator lights to stay illuminated simultaneously as the fluid level climbs.
