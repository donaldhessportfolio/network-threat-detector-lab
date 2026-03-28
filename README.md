<p align="center">
  <img src="AzurePyShark.png" width="700"/>
</p>

<h1 align="center">🛡️ Network Threat Detector Lab</h1>

<p align="center">
Azure • Wireshark • Python • Scapy
</p>

---

## 📌 Overview

This project simulates real-world network traffic in a cloud environment, captures it, analyzes it, and detects suspicious behavior using Python.

It demonstrates a full SOC-style workflow:

* Generate traffic
* Capture packets
* Analyze in Wireshark
* Detect anomalies using Python

---

## 🧱 Lab Setup

### ☁️ Azure Virtual Machine

![VM](01-azure-vm-overview.png)

### 🌐 Networking Configuration

![Networking](02-networking-overview.png)

### 🔐 NSG Inbound Rules

![NSG](03-nsg-inbound-rules.png)

---

## 💻 System Access

### 🖥️ Linux Access & Network Info

![Linux](04-linux-access-and-network.png)

### 🔑 SSH Connection

![SSH](07-ssh-successful-login.png)

---

## 📡 Traffic Generation

### 📶 ICMP Traffic (Ping)

![Ping](08-traffic-generation-ping.png)

### ⚠️ Simulated Suspicious Traffic

![Suspicious](09-supicious-traffic-loop.png)

---

## 📦 Packet Capture

### 📥 tcpdump Installed

![tcpdump](05-tcpdump-installed.png)

### 🎥 Capturing Traffic

![Capture](06-tcpdump-capturing.png)

### 💾 PCAP File Created

![PCAP](10-pcap-file-created.png)

### 🔄 Download to Local Machine

![Download](11-pcap-download.png)

---

## 🔍 Wireshark Analysis

### 📶 ICMP Analysis

![ICMP](12-wireshark-icmp.png)

### 🌐 HTTP Analysis

![HTTP](13-wireshark-http.png)

---

## 🧠 Python Threat Detection

### ⚙️ Scapy Setup

![Scapy](14-python-scapy-installed.png)

### 🚨 Detection Output

![Detection](15-python-threat-detection.png)

---

## ⚙️ Detection Logic

The Python script analyzes packet capture data and identifies:

* **Top Talkers** (most active IP addresses)
* **High-frequency HTTP requests**
* **Potential port scanning behavior**

---

## 🧰 Tools Used

* Microsoft Azure
* Ubuntu Linux
* tcpdump
* Wireshark
* Python
* Scapy

---

## 🎯 Skills Demonstrated

* Cloud infrastructure deployment
* Network traffic analysis
* Packet capture and inspection
* Detection engineering fundamentals
* Python scripting for cybersecurity
* Threat pattern recognition

---

## 🚀 Conclusion

This project demonstrates a complete end-to-end network analysis and detection workflow, closely aligned with real-world SOC analyst responsibilities.

---
