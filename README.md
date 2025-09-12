# AGRIGEST BOT: Agriculture Gesture-control-bot

Agri-Gest Bot is a gesture-controlled agricultural robot powered by ESP32.It interprets farmer’s hand gestures using the LSM6DSO sensor for navigation and control with TB6612FNG motor driver and payload modules handle movement and farming tasks. We aim to structure it to aid farmer in efficient sowing, precise watering and spraying fertilizing to minimise resources wastage, physical strain on farmers and no need of prior knowledge of technology for rural small-scale farmers.

# ESP32 Robot Transmitter

This project runs on an **ESP32 controller** with an **Adafruit LSM6DSOX accelerometer**.  
It detects hand gestures (by tilting the board) and sends commands to the robot via **ESP-NOW**.  


## Features
- Gesture-based robot control
- Commands: `forward`, `back`, `left`, `right`, `stop`
- Only sends command when it changes → reduces ESP-NOW traffic
- Works directly with the [ESP32 Robot Receiver](../RobotReceiver/)


## Hardware Setup

### Components
- ESP32 Dev Board (Controller)
- Adafruit LSM6DSOX accelerometer (I²C)
- USB cable for flashing

### Wiring

| ESP32 Pin | LSM6DSOX Pin |
|-----------|--------------|
| 3.3V      | VIN          |
| GND       | GND          |
| 21        | SDA          |
| 22        | SCL          |

(Default ESP32 I²C pins: SDA=21, SCL=22)

## Usage

1. Flash this code (`Transmittercode.txt`) to your **controller ESP32**.  
2. Open the **Serial Monitor** (115200 baud).  
3. Ensure your receiver ESP32’s MAC address is correctly set in this file:  

   ```cpp
   uint8_t broadcastAddress[] = {0xC4, 0x4F, 0x33, 0x6A, 0x3F, 0x69};

## ESP32 Robot Receiver 

This project runs on an **ESP32-based robot** with a **TB6612FNG (or compatible) motor driver**.  
It receives movement commands from a transmitter ESP32 via **ESP-NOW** and drives two DC motors accordingly.  


## Features
- Wireless peer-to-peer control using **ESP-NOW**
- Handles commands: `forward`, `back`, `left`, `right`, `stop`
- Automatic safety stop if connection is lost
- Clear serial feedback for debugging
- Clean, modular code — easy to extend

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


##  Usage

1. Flash this code (`Receivercode.txt`) to your **receiver ESP32**.
2. Open the **Serial Monitor** to see logs (115200 baud).
3. Copy the **MAC address** shown on startup.
4. Paste this MAC into your **transmitter ESP32** code so it knows where to send commands.
5. Control your robot.


## 📂 Repository Structure
