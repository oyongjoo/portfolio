# NRC Communication Gateway

[← Back to Portfolio](../README.md)

---

## 📖 Overview

**MAC Layer MQTT Bridge for HaLow Networks**

OpenWrt-based application that enables direct MAC layer communication between MQTT broker and client tags using custom EtherType protocol.

---

## 🔗 Repository

**GitHub**: [oyongjoo/nrc_comm_gw](https://github.com/oyongjoo/nrc_comm_gw) 🔒 Private

> For access to the full repository and source code, please contact: oyongjoo@gmail.com

---

## 🏗️ Architecture
```
┌─────────────┐         ┌──────────────────┐         ┌─────────────┐
│ MQTT Broker │◄───────►│  NRC Comm GW     │◄───────►│  MQTT Tag   │
│             │  TCP/IP │  (OpenWrt App)   │ MAC L2  │  (Client)   │
└─────────────┘         └──────────────────┘         └─────────────┘
                              │      ▲
                              │      │
                    ┌─────────▼──────┴─────────┐
                    │  Protocol Conversion     │
                    │  ┌────────────────────┐  │
                    │  │ MQTT → EtherType   │  │
                    │  │ EtherType → MQTT   │  │
                    │  │ Batch Processing   │  │
                    │  └────────────────────┘  │
                    └──────────────────────────┘
```

**Communication Flow:**

**Downlink (Broker → Tag):**
```
MQTT Message → EtherType Frame (0x88b6) → MAC Layer → Tag Client
              [Batch: 30 msgs]     [Payload: MQTT]
```

**Uplink (Tag → Broker):**
```
Tag Client → MAC Layer → EtherType Frame (0x88b6) → MQTT Message → Broker
                        [Extract Payload]
```

---

## 🛠️ Technical Stack

| Category | Technologies |
|----------|-------------|
| **Platform** | OpenWrt 22.03 |
| **Wireless** | HaLow (IEEE 802.11ah) |
| **Protocol** | Custom EtherType 0x88b6 |
| **Messaging** | MQTT 3.1.1 |
| **Language** | C/C++ |

---

## ✨ Key Features

### 1. MAC Layer Communication
- IP stack bypass for minimal latency
- Raw socket for direct frame control
- Custom EtherType prevents protocol conflicts

### 2. Performance Optimization
- **Batch transmission**: 30 messages per group
- **Firmware load management**: Distributed wireless processing load
- **Zero-copy design**: Minimized memory operations

### 3. Production Deployment
- **31 HaLow APs** in active production
- **Location**: Philadelphia, USA
- **Scalability**: Supports large-scale IoT networks

---

## 📊 Performance Metrics

| Metric | Value |
|--------|-------|
| **Managed APs** | 31 devices |
| **Deployment** | Philadelphia, USA |
| **Batch Size** | 30 messages |
| **Protocol Overhead** | ~14 bytes (Ethernet header) |
| **Communication Layer** | MAC Layer (L2) |

---

## 🎯 Technical Highlights

### Why MAC Layer?

1. **Lower Latency**: Eliminates IP routing overhead
2. **Firmware Optimization**: Reduces HaLow AP wireless processing load
3. **Direct Control**: Precise control over frame transmission timing
4. **Resource Efficiency**: Saves TCP/IP stack memory

### Custom Protocol Design

**EtherType 0x88b6 Frame Structure:**
```
┌──────────────┬──────────────┬──────────┬───────────────┬─────┐
│ Dest MAC (6) │ Src MAC (6)  │ Type (2) │ MQTT Payload  │ FCS │
│              │              │ 0x88b6   │ (Variable)    │     │
└──────────────┴──────────────┴──────────┴───────────────┴─────┘
```

---

## 🌟 Achievements

- ✅ Production deployment: 31 HaLow APs
- ✅ Protocol innovation: Custom MAC layer MQTT bridge
- ✅ Performance tuning: Batch processing for load management
- ✅ Real-world application: Philadelphia deployment

---

## 📝 Use Cases

- **IoT Sensor Networks**: Large-scale low-power HaLow device management
- **Industrial Monitoring**: Factory environment sensor data collection
- **Smart City**: Urban infrastructure monitoring
- **Asset Tracking**: Large-scale asset location tracking systems

---

## 🔐 Access Request

This is a **private repository** containing proprietary technology.

For portfolio review or collaboration:
- 📧 Email: oyongjoo@gmail.com
- 💼 LinkedIn: [linkedin.com/in/oyongjoo](https://www.linkedin.com/feed/)

---

## 🏷️ Tags

`OpenWrt` `HaLow` `802.11ah` `MQTT` `MAC-Layer` `IoT` `Embedded` `C/C++` `Wireless` `Protocol-Design`
