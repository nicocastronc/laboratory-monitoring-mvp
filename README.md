# laboratory-monitoring-mvp
Pleroma is an industrial monitoring and operational traceability platform designed to integrate existing laboratory and industrial assets into a unified real-time monitoring system. It focuses on telemetry acquisition, operator traceability, compliance reporting and scalable industrial architectures.

<img width="1578" height="722" alt="Captura de pantalla 2026-05-24 214001" src="https://github.com/user-attachments/assets/4293c89f-8234-4c90-9970-d351775d395c" />

 ## Features

- 🌡️ Real-time environmental monitoring
- 📡 MQTT communication between edge devices and backend
- ⚡ Live telemetry using WebSockets
- 🚨 Configurable threshold-based alert engine
- 👤 Operator acknowledgement workflow
- 📋 Immutable monthly compliance reports
- 🗂️ Historical telemetry visualization
- 🏗️ Laboratory digital twin
- 🔌 Plug-and-play WiFi provisioning through captive portal


## System Architecture

```text
Environmental Sensor
        │
        ▼
   ESP32 Edge Node
        │
 WiFi Captive Portal
        │
        ▼
      MQTT Broker
        │
        ▼
     Go Backend
   (Business Logic)
        │
 ┌──────┴─────────────┐
 │                    │
 ▼                    ▼
Timeseries DB    WebSocket Hub
 │                    │
 └──────┬─────────────┘
        ▼
   React Dashboard
```

### Architecture Overview

The current implementation follows an event-driven architecture designed for real-time industrial monitoring.

- **ESP32 Edge Node** acquires telemetry from environmental sensors and publishes measurements through MQTT.
- **Captive Portal** enables plug-and-play WiFi provisioning without firmware modifications.
- **Go Backend** processes telemetry, validates thresholds, generates alerts and exposes REST APIs.
- **WebSocket Hub** streams live updates to connected clients with minimal latency.
- **Timeseries Database** stores historical telemetry and operator actions.
- **React Dashboard** provides a digital twin of the monitored environment with live status visualization.


## ⚙️ How It Works

```text
Environmental Sensor
        │
        ▼
ESP32 measures temperature and humidity
        │
        ▼
Telemetry is published via MQTT
        │
        ▼
Go backend processes incoming events
        │
        ├── Stores telemetry
        ├── Evaluates thresholds
        ├── Generates alerts
        └── Exposes REST APIs
        │
        ▼
WebSocket broadcasts updates in real time
        │
        ▼
React dashboard displays current system status
        │
        ▼
Operator acknowledges alerts and records corrective actions
        │
        ▼
Immutable monthly compliance reports are automatically generated
```

### Operational Flow

The platform continuously acquires telemetry from ESP32-based edge devices, processes incoming events through the Go backend, evaluates configurable alert rules and streams live updates to connected dashboards via WebSockets.

Whenever an abnormal condition is detected, operators are immediately notified and every acknowledgement or corrective action is permanently recorded. Historical telemetry and operator actions are later consolidated into immutable monthly reports for compliance and traceability.

![Go](https://img.shields.io/badge/Go-00ADD8?logo=go&logoColor=white)

![React](https://img.shields.io/badge/React-61DAFB?logo=react&logoColor=black)

![MQTT](https://img.shields.io/badge/MQTT-660066?logo=eclipsemosquitto&logoColor=white)

![ESP32](https://img.shields.io/badge/ESP32-E7352C?logo=espressif&logoColor=white)

## 🎯 Current MVP Scope

The current implementation focuses on laboratory environmental monitoring using ESP32-based edge devices.

The platform was designed with a modular architecture so that future versions can integrate additional industrial assets and communication protocols such as:

- RS-232
- Modbus RTU
- Modbus TCP
- Ethernet-enabled devices
- OPC-UA
- PLCs and industrial gateways

This allows the same platform to evolve from environmental monitoring to a complete industrial monitoring and operational traceability framework.

> **Note:** This repository is intended to showcase the platform architecture, engineering decisions and system capabilities. The production source code is intentionally not included.

<img width="725" height="715" alt="Captura de pantalla 2026-05-28 225109" src="https://github.com/user-attachments/assets/8404bd17-f37a-4c9e-9537-707ef5174f47" />

