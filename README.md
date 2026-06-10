<h1 align="center">REAL TIME DATA COMMUNICATION USING LIFI IN HOSPITAL MANAGEMENT<h1>

<div align="center">

[![Language](https://img.shields.io/badge/Language-C%20%2F%20Arduino-00979D?style=flat-square&logo=arduino&logoColor=white)](https://www.arduino.cc/)
[![Technology](https://img.shields.io/badge/Tech-Li--Fi-70a5fd?style=flat-square&logo=light&logoColor=white)](https://github.com/arunkarthi-03)
[![Platform](https://img.shields.io/badge/Platform-Arduino%20UNO-bf91f3?style=flat-square&logo=arduino&logoColor=white)](https://www.arduino.cc/)
[![IoT](https://img.shields.io/badge/Cloud-IoT%20Platform-38bdae?style=flat-square&logo=thingsboard&logoColor=white)](https://github.com/arunkarthi-03)
[![Paper](https://img.shields.io/badge/Research-Published%20Paper-success?style=flat-square&logo=academia&logoColor=white)](https://github.com/arunkarthi-03)
[![Status](https://img.shields.io/badge/Status-Completed%20%26%20Tested-success?style=flat-square)](https://github.com/arunkarthi-03)
[![College](https://img.shields.io/badge/College-Panimalar%20Institute%20of%20Technology-orange?style=flat-square)](https://github.com/arunkarthi-03)

</div>

---

## 📋 Table of Contents

- [Abstract](#-abstract)
- [What is Li-Fi?](#-what-is-li-fi)
- [System Architecture](#-system-architecture)
- [Hardware Components](#-hardware-components)
- [How It Works](#-how-it-works)
- [Circuit Overview](#-circuit-overview)
- [Project Structure](#-project-structure)
- [Getting Started](#-getting-started)
- [Key Results](#-key-results)
- [Research Paper](#-research-paper)
- [Author](#-author)

---

## 📄 Abstract

This project presents a **secure, real-time patient monitoring system** built on **Li-Fi (Light Fidelity)** technology — a cutting-edge optical wireless communication standard that transmits data through visible light instead of conventional radio frequencies.

The system reads live patient vitals — **pulse rate** and **body temperature** — from sensors interfaced with an **Arduino microcontroller**, transmits the data reliably via a **Li-Fi optical link**, and uploads it to an **IoT cloud platform** for continuous remote viewing by medical staff.

> 📝 A **technical research paper** was authored and published based on this project, demonstrating its real-world viability in hospital environments.

---

## 💡 What is Li-Fi?

**Li-Fi (Light Fidelity)** is a wireless communication technology that uses **visible light** as a medium instead of radio waves (Wi-Fi).

| Feature | Li-Fi | Wi-Fi |
|:---|:---:|:---:|
| Medium | Visible Light | Radio Waves |
| Speed | Up to 224 Gbps | Up to ~9.6 Gbps |
| Security | High (light can't pass walls) | Moderate |
| EMI Interference | ❌ None | ✅ Susceptible |
| Hospital Safe | ✅ Yes | ⚠️ Restricted |
| Range | Short (Line of Sight) | Long |

> 🏥 **Why Li-Fi in hospitals?** Medical equipment is sensitive to electromagnetic interference (EMI). Li-Fi transmits via light — making it completely safe around MRI machines, ICU monitors, and other critical medical devices.

---

## 🏗️ System Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                        TRANSMITTER SIDE                             │
│                                                                     │
│   [ Pulse Sensor ]──┐                                               │
│                     ├──► [ Arduino UNO ] ──► [ LED (Li-Fi TX) ] ───┤
│   [ Temp Sensor  ]──┘                                               │
│                           (Reads & encodes vitals as light pulses)  │
└─────────────────────────────────────────────────────────────────────┘
                                    │
                              ✨ Light ✨
                                    │
┌─────────────────────────────────────────────────────────────────────┐
│                        RECEIVER SIDE                                │
│                                                                     │
│   [ Photodetector / LDR ] ──► [ Arduino UNO ] ──► [ IoT Platform ] │
│                                (Decodes signal)    (Cloud Upload)   │
│                                                         │           │
│                                                    [ Remote Monitor │
│                                                      / Dashboard ]  │
└─────────────────────────────────────────────────────────────────────┘
```

---

## 🔧 Hardware Components

| # | Component | Purpose |
|:---:|:---|:---|
| 1 | **Arduino UNO** | Microcontroller — reads sensors, encodes/decodes data |
| 2 | **Pulse Rate Sensor** | Reads patient's real-time heart rate (BPM) |
| 3 | **Temperature Sensor** | Reads patient's body temperature |
| 4 | **High-Intensity LED** | Li-Fi transmitter — converts data to light pulses |
| 5 | **Photodetector / LDR** | Li-Fi receiver — converts light pulses back to data |
| 6 | **IoT Module** | Uploads decoded vitals to cloud platform (e.g., ThingSpeak / Blynk) |
| 7 | **Breadboard & Wires** | Prototyping and circuit connections |
| 8 | **Power Supply** | Powers the Arduino and peripheral modules |

---

## ⚙️ How It Works

```
Step 1 ── SENSE
         Pulse & Temperature sensors read real-time patient vitals
         and feed analog/digital signals to the Arduino.

Step 2 ── ENCODE & TRANSMIT
         Arduino encodes the sensor data and modulates it as
         rapid ON/OFF light pulses through a high-intensity LED
         (Li-Fi Transmitter).

Step 3 ── RECEIVE
         A photodetector on the receiver side detects the incoming
         light pulses and feeds the signal to a second Arduino.

Step 4 ── DECODE
         The receiver Arduino decodes the light pulses back into
         the original sensor values (pulse rate & temperature).

Step 5 ── UPLOAD TO CLOUD
         The decoded patient data is pushed to an IoT cloud platform
         for continuous, real-time remote monitoring by medical staff.
```

---

## 🔌 Circuit Overview

**Transmitter:**
```
Pulse Sensor  ──► Arduino A0
Temp Sensor   ──► Arduino A1
Arduino D9    ──► LED (+) ──► 220Ω Resistor ──► GND
```

**Receiver:**
```
LDR           ──► Arduino A0 (via voltage divider)
Arduino       ──► IoT Module (Serial / I2C)
IoT Module    ──► Cloud Platform (Wi-Fi)
```

---

## 📁 Project Structure

```
LiFi-Project/
│
├── Transmitter/
│   └── transmitter.ino       # Arduino sketch — sensor read & Li-Fi TX
│
├── Receiver/
│   └── receiver.ino          # Arduino sketch — Li-Fi RX & IoT upload
│
├── Circuit/
│   └── circuit_diagram.png   # Wiring & circuit schematic
│
├── Paper/
│   └── research_paper.pdf    # Published technical research paper
│
└── README.md                 # Project documentation
```

---

## 🚀 Getting Started

### Prerequisites

- [Arduino IDE](https://www.arduino.cc/en/software) (v1.8+ or v2.x)
- Arduino UNO boards (×2 — one TX, one RX)
- Required hardware components (see table above)
- IoT platform account (ThingSpeak / Blynk)

### Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/arunkarthi-03/LiFi-Project.git
   cd LiFi-Project
   ```

2. **Upload Transmitter sketch**
   - Open `Transmitter/transmitter.ino` in Arduino IDE
   - Select the correct COM port & board (Arduino UNO)
   - Click **Upload**

3. **Upload Receiver sketch**
   - Open `Receiver/receiver.ino` in Arduino IDE
   - Update your IoT platform credentials (API key / channel ID)
   - Click **Upload**

4. **Assemble the circuit**
   - Follow `Circuit/circuit_diagram.png` for wiring
   - Ensure the LED and photodetector are **aligned on the same optical axis**

5. **Monitor**
   - Open Serial Monitor (115200 baud) to verify data flow
   - View live vitals on your IoT platform dashboard

---

## 📊 Key Results

| Metric | Result |
|:---|:---|
| **Data Transmission Medium** | Visible Light (Li-Fi) |
| **Vitals Monitored** | Pulse Rate (BPM) + Body Temperature (°C) |
| **System Type** | Real-Time, Continuous Monitoring |
| **Data Persistence** | IoT Cloud Upload (Remote Access) |
| **EMI Risk** | ✅ Zero — fully safe for hospital use |
| **Data Integrity** | ✅ Verified through rigorous prototype testing |
| **Environment Tested** | Simulated hospital environment |
| **Research Output** | ✅ Technical paper authored and published |

---

## 📝 Research Paper

A formal **technical research paper** was authored and published based on this project.

- **Title:** Real-Time Patient Monitoring Using Li-Fi in Hospital Management
- **Author:** Karthikeyan Arun Kumar
- **Institution:** Panimalar Institute of Technology, Chennai (Anna University)
- **Year:** March 2025
- **Status:** ✅ Published

> 📄 The paper is available in the `Paper/` directory of this repository.

---

## 👤 Author

<div align="center">

**Karthikeyan Arun Kumar**
B.E. Electronics & Communication Engineering
Panimalar Institute of Technology, Chennai | Anna University | 2025

[![GitHub](https://img.shields.io/badge/GitHub-arunkarthi--03-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/arunkarthi-03)
[![Email](https://img.shields.io/badge/Email-arunkarthi4761%40gmail.com-D14836?style=flat-square&logo=gmail&logoColor=white)](mailto:arunkarthi4761@gmail.com)

</div>

---

<div align="center">

*"Transmitting life-critical data — not through radio waves, but through light."* 💡

⭐ **If this project helped you, consider giving it a star!** ⭐


</div>
