# 🚀 Deep Packet Inspection (DPI) Engine

A high-performance **Deep Packet Inspection (DPI)** engine built in **C++** that analyzes network traffic from PCAP files, identifies applications using TLS SNI, applies filtering rules, and generates traffic statistics.

## ✨ Features

- 📦 PCAP file parsing
- 🔍 Deep Packet Inspection (DPI)
- 🌐 TLS SNI extraction
- 🎯 Application identification (YouTube, Google, Facebook, etc.)
- 🚫 Rule-based application and domain blocking
- 🔄 Connection tracking using Five-Tuple
- ⚡ Multi-threaded packet processing
- 📊 Traffic statistics and reporting
- 💾 Filtered PCAP output generation

## 🛠️ Technologies Used

- C++
- CMake
- Multithreading
- PCAP Processing
- STL
- Network Programming

## 📂 Project Structure

```
include/
src/
test_dpi.pcap
CMakeLists.txt
README.md
```

## ⚙️ Build

```bash
mkdir build
cd build
cmake ..
cmake --build . --config Release
```

## ▶️ Run

```bash
./dpi_mt input.pcap output.pcap
```

Example with blocking:

```bash
./dpi_mt input.pcap output.pcap --block-app YouTube
```

## 🔄 Workflow

```
Input PCAP
     │
     ▼
Read Packets
     │
     ▼
Parse Network Headers
     │
     ▼
Extract TLS SNI
     │
     ▼
Identify Application
     │
     ▼
Apply Blocking Rules
     │
     ▼
Generate Statistics
     │
     ▼
Output PCAP
```

## 📊 Example Capabilities

- Detect YouTube traffic
- Detect Google traffic
- Detect Facebook traffic
- Block selected applications
- Block specific domains
- Track network connections
- Generate processing reports

## 🎯 Purpose

This project demonstrates concepts of:

- Deep Packet Inspection
- Computer Networks
- Network Security
- Traffic Analysis
- Multi-threaded Programming
- High-performance Packet Processing

## 👨‍💻 Author

**Toufik Shaikh**
