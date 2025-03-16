# Shadow Security Alarm

## Overview
This repository contains the implementation of a **Shadow Security Alarm** using a **BPW34 photodiode** and a **CA3130 operational amplifier**. The system detects shadows as potential intrusions and triggers an alarm. Additionally, it integrates **IoT functionality** using the **ESP8266 Wi-Fi module** to send real-time alerts via mobile notifications and email.

## Key Features
- **Shadow Detection**: Uses a BPW34 photodiode to detect changes in light intensity.
- **Op-Amp-Based Comparator**: The CA3130 operational amplifier acts as an inverting comparator.
- **Buzzer and LED Alerts**: Triggers an alarm when a shadow is detected.
- **IoT Integration**: Sends real-time notifications via **ESP8266 Wi-Fi module**.
- **Low Power Consumption**: Efficient and cost-effective security solution.

## Components Required
- **BPW34 Photodiode**
- **CA3130 Op-Amp**
- **10KΩ Potentiometer**
- **Piezo Buzzer**
- **LED**
- **Resistors (100KΩ, 100Ω)**
- **BJT Transistor (C945)**
- **ESP8266 Wi-Fi Module**
- **Perf board for hardware implementation**

## How It Works
1. The **BPW34 photodiode** detects ambient light changes.
2. The **CA3130 Op-Amp** compares the photodiode’s voltage with a reference voltage.
3. When a shadow falls on the photodiode:
   - The input voltage drops below the reference voltage.
   - The Op-Amp output goes **HIGH**, triggering the buzzer and LED.
   - The **ESP8266** sends a notification and email alert.

## Example Scenario
Consider a **museum** where a **precious artifact** is displayed under controlled lighting. No one is allowed near it, ensuring that the area remains well-lit at all times. Logically, there should be **no shadow** over the artifact. If a shadow appears, it **indicates the presence of an unauthorized individual**, triggering an immediate alert to security personnel. This ensures real-time protection of valuable items.

## Circuit Diagram
The circuit consists of:
- A photodiode connected to the inverting terminal of the Op-Amp.
- A reference voltage at the non-inverting terminal.
- A buzzer and LED at the Op-Amp’s output.
- An ESP8266 module to handle real-time notifications.

## Software Implementation
- The **TinkerCAD** simulation verified the circuit’s accuracy.
- When no shadow is detected, the output remains **LOW**.
- When a shadow is detected, the output switches **HIGH**, activating the buzzer and LED.

## Hardware Implementation
The hardware implementation involves assembling all components on a **Perf board** to create a stable and functional shadow security alarm system.

### Step-by-Step Assembly
1. **Component Placement**:
   - Arrange the **BPW34 photodiode**, **CA3130 Op-Amp**, **ESP8266 Wi-Fi module**, **buzzer**, **LED**, and supporting resistors and transistors on the **Perf board**.
   - Ensure optimal spacing between components for easy soldering and stability.

2. **Soldering the Components**:
   - Solder the terminals of each component to the **Perf board**.
   - Establish strong electrical connections to prevent signal loss or instability.
   - Use **10KΩ–100KΩ resistors** in series with the photodiode to regulate voltage levels.

3. **Power and Ground Connections**:
   - **IC Powering**: Connect **CA3130 Op-Amp’s Pin 7** to the **+V supply**.
   - **Grounding**: Connect **Pin 4** of CA3130 to the **ground line**.

4. **Photodiode & Op-Amp Connections**:
   - **BPW34 Photodiode**:
     - The **anode (+)** is connected to the **reference voltage** via the **potentiometer (Pin 3)** of CA3130.
     - The **cathode (-)** is connected to the **inverting input (Pin 2)** of CA3130.
   - **CA3130 Output (Pin 6)**:
     - This output pin controls the **buzzer** and **LED**.
     - A **100Ω resistor** is placed in series with the LED to limit current.

5. **ESP8266 Integration**:
   - The **CA3130 output (Pin 6)** is connected to a **digital input pin** of ESP8266.
   - Since **ESP8266 operates at 3.3V**, a **voltage divider** (using resistors) is used to reduce the Op-Amp’s 5V output to a safe level.
   - **ESP8266 Wi-Fi module setup**:
     - The module is powered by a **9V supply**, with **regulated 3.3V output** powering the ESP.
     - It listens for **HIGH signals** from the Op-Amp to trigger notifications.
     - The buzzer and LED outputs are controlled via **GPIO 7D and 4D**.
   - **Transistor as a Switch**:
     - The **BJT transistor (C945)** is used as a **switch** to control the **5V buzzer** using the ESP8266, which operates at **3.3V logic level**.
     - When the ESP8266 outputs a HIGH signal (3.3V), the transistor turns ON, allowing current to flow and activating the buzzer.

6. **ESP8266-Based Shadow Detection Logic**:
   - The ESP8266 is programmed to monitor **D8 (shadow detection pin)**.
   - If **D8 is HIGH**, it logs an event via Blynk (`"WARNING: SHADOW DETECTED!!!"`).
   - The ESP8266 also turns on **LED_BUILTIN** and **D7 (buzzer pin)** when a shadow is detected.
   - The **Blynk cloud platform** sends notifications to a **registered mobile device** and can trigger an **email alert**.
   - The buzzer and LED automatically turn OFF when no shadow is detected.

7. **Final Testing & Debugging**

8. **Output Documentation**:
   - The output pictures demonstrating the shadow detection and alert system have been included in the **documentation file**.
   - These images showcase different scenarios, such as normal lighting conditions, shadow detection, buzzer activation, and notification alerts.
   - Refer to the documentation for a visual representation of the system's working.:
   - Power the circuit and verify the **response to shadows**.
   - Check if the **buzzer sounds** and **LED glows** when a shadow is detected.
   - Ensure that the **ESP8266 sends notifications and emails** upon detection.
   - Adjust the **potentiometer** if necessary to fine-tune sensitivity.

This structured approach ensures **stable, real-time shadow detection** with effective alerting mechanisms. The final assembly is tested under different lighting conditions to validate performance.

## License
This project is intended for **private use only**. Redistribution, modification, or public sharing of this repository is **prohibited**.

## Contact
For any inquiries, please contact **Naveen Kumar B(naveenau2023@gmail.com)**.

