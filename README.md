# Gas Leakage Detection System

![Platform](https://img.shields.io/badge/Platform-IoT%20%2F%20Web-brightgreen?logo=arduino)
![Language](https://img.shields.io/badge/Language-JavaScript%20%2F%20C++-orange?logo=javascript)
![IDE](https://img.shields.io/badge/IDE-VS%20Code%20%2F%20Arduino%20IDE-007ACC?logo=visualstudiocode)
![Backend](https://img.shields.io/badge/Backend-Node.js-green?logo=node.js)
![Database](https://img.shields.io/badge/Database-MongoDB-darkgreen?logo=mongodb)
![IoT](https://img.shields.io/badge/IoT-MQ--2%20Sensor-red)
![Status](https://img.shields.io/badge/Status-Active-brightgreen)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

**Gas Leakage Detection System** is an IoT-based safety monitoring application designed to detect hazardous gas leaks in real time using gas sensors and microcontroller integration. The system continuously monitors gas concentration levels, triggers emergency alerts, and provides live monitoring through a client-server architecture. 🚨🔥

---

## 📌 Table of Contents

* [Features](#-features)
* [System Architecture](#-system-architecture)
* [Tech Stack](#-tech-stack)
* [Hardware Components](#-hardware-components)
* [Project Structure](#-project-structure)
* [Prerequisites](#-prerequisites)
* [Installation & Setup](#-installation--setup)
* [Server Compilation & Execution](#-server-compilation--execution)
* [Client Compilation & Execution](#-client-compilation--execution)
* [Arduino Compilation & Upload](#-arduino-compilation--upload)
* [Running the Complete System](#-running-the-complete-system)
* [Environment Variables](#-environment-variables)
* [Common Issues & Fixes](#-common-issues--fixes)
* [Future Enhancements](#-future-enhancements)
* [Contributing](#-contributing)
* [Author](#-author)
* [License](#-license)

---

## ✨ Features

| Feature                           | Description                                                       |
| --------------------------------- | ----------------------------------------------------------------- |
| 🚨 **Real-Time Gas Detection**    | Detects harmful gases using MQ-series gas sensors                 |
| 🔔 **Instant Alert System**       | Activates buzzer/alarm when gas threshold exceeds safety limit    |
| 📡 **IoT Monitoring**             | Sends live gas readings to server/dashboard                       |
| 🌐 **Client-Server Architecture** | Real-time communication between hardware and monitoring interface |
| 📊 **Live Data Visualization**    | Displays gas concentration levels on dashboard                    |
| 📱 **Emergency Notification**     | Can be extended for SMS/email alerts                              |
| 🔥 **Threshold Monitoring**       | Automatically detects dangerous gas levels                        |
| ⚡ **Low Cost & Efficient**        | Uses affordable IoT hardware components                           |

---

## 🏗️ System Architecture

```text
┌─────────────────────────────────────────────────────────────┐
│                     SENSOR LAYER                            │
│                                                             │
│   ┌──────────────┐      ┌──────────────┐                  │
│   │ MQ Gas Sensor│────▶ │ Microcontroller│                │
│   │ (MQ-2/MQ-5)  │      │ Arduino/ESP32 │                │
│   └──────┬───────┘      └──────┬───────┘                  │
│          │                     │                           │
│          ▼                     ▼                           │
│     Gas Detection         Alarm/Buzzer                     │
└──────────────────────┬──────────────────────────────────────┘
                       │ Wi-Fi / Serial Communication
┌──────────────────────▼──────────────────────────────────────┐
│                     SERVER LAYER                             │
│                                                              │
│   Node.js Backend                                            │
│   ├── API Handling                                           │
│   ├── Sensor Data Processing                                 │
│   ├── Database Storage                                       │
│   └── Alert Management                                       │
└──────────────────────┬──────────────────────────────────────┘
                       │ REST API / Socket Communication
┌──────────────────────▼──────────────────────────────────────┐
│                     CLIENT LAYER                             │
│                                                              │
│   Web Dashboard                                              │
│   ├── Live Gas Readings                                      │
│   ├── Status Monitoring                                      │
│   ├── Alert Display                                          │
│   └── Safety Notifications                                   │
└──────────────────────────────────────────────────────────────┘
```

---

## 🛠️ Tech Stack

| Layer             | Technology                |
| ----------------- | ------------------------- |
| Frontend / Client | HTML, CSS, JavaScript     |
| Backend / Server  | Node.js, Express.js       |
| Database          | MongoDB (if configured)   |
| IoT Hardware      | Arduino / ESP8266 / ESP32 |
| Sensor            | MQ-2 / MQ-5 Gas Sensor    |
| IDE               | VS Code / Arduino IDE     |
| Communication     | HTTP / Serial / Wi-Fi     |

---

## 🔌 Hardware Components

| Component          | Purpose                |
| ------------------ | ---------------------- |
| MQ-2 / MQ-5 Sensor | Gas leakage detection  |
| Arduino / ESP32    | Sensor data processing |
| Buzzer             | Alarm system           |
| Breadboard         | Circuit connections    |
| Jumper Wires       | Hardware connections   |
| USB Cable          | Programming and power  |
| Power Supply       | System operation       |

---

## 📂 Project Structure

```text
Gas-Leakage-Detection-System/
│
├── client/                     ← Frontend dashboard
│   ├── public/
│   ├── src/
│   ├── package.json
│   └── README.md
│
├── server/                     ← Backend server
│   ├── routes/
│   ├── controllers/
│   ├── models/
│   ├── package.json
│   └── .env
│
├── arduino/
│   └── gas_detector.ino        ← Arduino sensor code
│
├── screenshots/
├── README.md
└── package.json
```

---

## ✅ Prerequisites

Ensure the following are installed:

| Tool        | Version  | Download                                                                 |
| ----------- | -------- | ------------------------------------------------------------------------ |
| Node.js     | v18+     | [https://nodejs.org](https://nodejs.org)                                 |
| npm         | Latest   | Installed with Node.js                                                   |
| VS Code     | Latest   | [https://code.visualstudio.com](https://code.visualstudio.com)           |
| Arduino IDE | Latest   | [https://www.arduino.cc/en/software](https://www.arduino.cc/en/software) |
| MongoDB     | Optional | [https://www.mongodb.com](https://www.mongodb.com)                       |
| Git         | Latest   | [https://git-scm.com](https://git-scm.com)                               |

---

# 🚀 Installation & Setup

## Step 1 — Clone the Repository

```bash
git clone https://github.com/Mayilraj13/Gas-Leakage-Detection-System.git
cd Gas-Leakage-Detection-System
```

---

# ⚙️ Server Compilation & Execution

## Step 1 — Navigate to Server Directory

```bash
cd server
```

---

## Step 2 — Install Dependencies

```bash
npm install
```

---

## Step 3 — Configure Environment Variables

Create a `.env` file inside the `server/` directory.

```env
PORT=5000
MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_secret_key
```

If MongoDB or JWT is not used in your project, remove unnecessary variables.

---

## Step 4 — Start the Server

### Development Mode

```bash
npm run dev
```

### Production Mode

```bash
npm start
```

---

## ✅ Expected Output

```bash
Server running on port 5000
Database connected successfully
```

---

# 💻 Client Compilation & Execution

## Step 1 — Open New Terminal

```bash
cd client
```

---

## Step 2 — Install Dependencies

```bash
npm install
```

---

## Step 3 — Configure API URL

Create a `.env` file inside the `client/` folder.

### React App

```env
REACT_APP_API_URL=http://localhost:5000
```

### Vite App

```env
VITE_API_URL=http://localhost:5000
```

Use the correct variable format depending on your frontend framework.

---

## Step 4 — Run the Client

### React

```bash
npm start
```

### Vite

```bash
npm run dev
```

---

## ✅ Expected Output

```bash
Local: http://localhost:3000
```

or

```bash
Local: http://localhost:5173
```

---

# 🔧 Arduino Compilation & Upload

## Step 1 — Open Arduino IDE

Download and install Arduino IDE:

[https://www.arduino.cc/en/software](https://www.arduino.cc/en/software)

---

## Step 2 — Open Arduino Code

Open:

```text
arduino/gas_detector.ino
```

---

## Step 3 — Select Board

Navigate:

```text
Tools → Board
```

Choose:

* Arduino Uno
* ESP8266
* ESP32

---

## Step 4 — Select COM Port

```text
Tools → Port → COMx
```

---

## Step 5 — Install Required Libraries

Install from:

```text
Sketch → Include Library → Manage Libraries
```

Common libraries:

* WiFi.h
* ESP8266WiFi.h
* ArduinoJson
* PubSubClient

---

## Step 6 — Upload Code

Click:

```text
Upload Button (→)
```

---

## ✅ Expected Output

```text
Done Uploading
```

---

# ▶️ Running the Complete System

## Terminal 1 — Start Backend

```bash
cd server
npm run dev
```

---

## Terminal 2 — Start Frontend

```bash
cd client
npm start
```

---

## Hardware Setup

* Connect MQ sensor to Arduino/ESP board
* Power the microcontroller
* Ensure Wi-Fi connectivity
* Open dashboard in browser

---

# 🌍 Environment Variables

## Server `.env`

```env
PORT=5000
MONGO_URI=your_mongodb_uri
JWT_SECRET=your_secret
```

---

## Client `.env`

```env
REACT_APP_API_URL=http://localhost:5000
```

---

# 🐛 Common Issues & Fixes

| Error                       | Solution                                                 |
| --------------------------- | -------------------------------------------------------- |
| `npm install failed`        | Delete `node_modules` and run `npm install` again        |
| `EADDRINUSE`                | Change port or kill process using the port               |
| `MongoDB connection failed` | Verify MongoDB URI and database status                   |
| `Sensor not detecting gas`  | Allow MQ sensor warm-up for 30–60 seconds                |
| `Arduino upload failed`     | Check COM port and USB cable                             |
| `Dashboard not loading`     | Verify frontend API URL configuration                    |
| `Module not found`          | Install missing package using `npm install package-name` |
| `Wi-Fi not connecting`      | Check SSID/password in Arduino code                      |

---

# 🚀 Future Enhancements

* 📱 Mobile app integration
* ☁️ Cloud-based IoT monitoring
* 📧 SMS / Email emergency alerts
* 🤖 AI-based gas prediction analysis
* 🔥 Automatic gas valve shutoff
* 📊 Advanced analytics dashboard
* 🛰️ Remote monitoring system
* 🔔 Telegram / WhatsApp alert integration

---

# 🤝 Contributing

Contributions are welcome!

1. Fork the repository
2. Create a feature branch:

   ```bash
   git checkout -b feature/your-feature
   ```
3. Commit changes:

   ```bash
   git commit -m "Add your feature"
   ```
4. Push to branch:

   ```bash
   git push origin feature/your-feature
   ```
5. Open a Pull Request

---

# 👤 Author

**Mayilraj R**

* GitHub: [@Mayilraj13](https://github.com/Mayilraj13)

---

# 📄 License

This project is licensed under the **MIT License**.

---
