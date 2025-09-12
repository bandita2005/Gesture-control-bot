# Gesture-control-bot



## ESP32 Robot Receiver 

This project runs on an **ESP32-based robot** with a **TB6612FNG (or compatible) motor driver**.  
It receives movement commands from a transmitter ESP32 via **ESP-NOW** and drives two DC motors accordingly.  

---

## Features
- Wireless peer-to-peer control using **ESP-NOW**
- Handles commands: `forward`, `back`, `left`, `right`, `stop`
- Automatic safety stop if connection is lost
- Clear serial feedback for debugging
- Clean, modular code — easy to extend

---

## Hardware Setup

### Components
- ESP32 Dev Board (Receiver)
- TB6612FNG Motor Driver (or similar dual H-bridge driver)
- 2 × DC Motors
- Power Supply (battery pack)

### Pin Mapping

| ESP32 Pin | Motor Driver | Description     |
|-----------|--------------|-----------------|
| 25        | STBY         | Standby (enable)|
| 14        | PWMA         | Motor A PWM     |
| 27        | AIN1         | Motor A Dir     |
| 26        | AIN2         | Motor A Dir     |
| 12        | PWMB         | Motor B PWM     |
| 32        | BIN1         | Motor B Dir     |
| 33        | BIN2         | Motor B Dir     |

---

##  Usage

1. Flash this code (`Receivercode.txt`) to your **receiver ESP32**.
2. Open the **Serial Monitor** to see logs (115200 baud).
3. Copy the **MAC address** shown on startup.
4. Paste this MAC into your **transmitter ESP32** code so it knows where to send commands.
5. Control your robot.

---

## 📂 Repository Structure
