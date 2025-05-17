# 🚘Advanced Driver Assistance System(ADAS)- Featuring Adaptive Cruise Control (ACC) & Lane Keeping Assist (LKA)

## 📌 Project Overview
This project showcases a model‑based design and real‑time prototyping of Adaptive Cruise Control (ACC) and Lane Keeping Assist (LKA) – two core features of modern Advanced Driver Assistance Systems (ADAS). The system combines Simulink‑based modeling (for controller design and PID tuning) with Arduino + Pixy2 prototyping (for live sensor feedback and actuation) to validate concepts like speed regulation, safe distance maintenance, and lane tracking.

## ⚙️ What I Built

### ✅ Adaptive Cruise Control (ACC)
- Maintains a set following distance using PID control logic.  
- Simulink model used to design, simulate, and tune PID parameters (root‑locus & step‑response).  
- Real‑time distance measurements via HC‑SR04 ultrasonic sensor connected to Arduino.  

### ✅ Lane Keeping Assist (LKA)
- Detects lane markings using Pixy2 vision sensor (CMUcam5).  
- Processes single‑ vs. dual‑vector outputs for center‑offset calculation.  
- Implements corrective steering commands to keep the vehicle centered between road lines.  

### ✅ Integrated ADAS System
- Modular Arduino firmware allows standalone or combined ACC + LKA operation.  
- Visual feedback via 16×2 LCD and LEDs indicating “Cruise Active,” “Lane Centered,” “Turn Left/Right.”  
- Data logging of distance and lane‑offset values for offline analysis.  

## 📈 Key Outcomes
- 🔹 Stable, responsive control with PID‑tuned ACC (overshoot < 5%, rise time < 0.1 s)  
- 🔹 Accurate lane tracking under straight and curved sections using Pixy2 vectors  
- 🔹 Real‑world validation on a scaled test track with obstacles and painted lanes  

## 🧠 Tech Stack
- 🔧 **Simulink + MATLAB**: control‑system modeling, PID tuning, root‑locus & step‑response analysis  
- 🔧 **Arduino IDE + Embedded C**: sensor interfacing, Pixy2 CMUcam5 library, motor actuation via PWM  
- 🔧 **Sensors & Actuators**:  
  - HC‑SR04 Ultrasonic (distance for ACC)  
  - Pixy2 Vision Sensor (line detection for LKA)  
  - L298N Motor Driver & DC motors (speed/steering simulation)  

## 🔍 How It Works

### 🛣️ Adaptive Cruise Control (ACC)
1. Arduino triggers HC‑SR04 and reads echo time → distance.  
2. Simulink‑tuned PID calculates throttle adjustment to maintain a safe gap.  
3. PWM signals modulate motor speed accordingly.  

### 🧭 Lane Keeping Assist (LKA)
1. Pixy2 runs the “line” program, outputs up to two vectors per frame.  
2. Arduino reads `pixy.line.vectors[]`, computes lane center vs. frame center.  
3. If deviation > threshold → generate left/right steering command; else go straight.  

## 🧪 Tools Used
- 🛠️ **MATLAB + Simulink** (control design & PID tuning)  
- 🛠️ **Arduino IDE + Pixy2 library** (firmware & vision integration)  
- 🛠️ **PixyMon** (training and calibration of Pixy2 vision sensor)

## 🚘Car Model

![Initial_Car_Model](https://github.com/user-attachments/assets/232eec37-83d9-4745-9057-b65ca74fcffc)

## 📘 What I Learned
Throughout this project, I gained hands‑on experience with model‑based control in Simulink-designing and tuning PID controllers via root‑locus and step‑response analysis-and then translating those gains into Embedded C on an Arduino. I used PixyMon to train and calibrate the Pixy2 vision sensor’s line‑tracking parameters, and integrated its line‑vector output into real‑time lane‑centering logic. I also fused ultrasonic distance readings with vision feedback for a robust multi‑modal control strategy. Building the full prototype from high‑level Simulink models to low‑level Arduino firmware-taught me system validation on constrained hardware, while custom track testing and performance logging reinforced a safety‑focused approach essential for automotive applications.
