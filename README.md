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

It follows a **SOC-style workflow**:

* Generate network traffic
* Capture packets at the host level
* Analyze packet data using Wireshark
* Detect anomalies using Python scripting

---

## 🧱 Lab Setup

### ☁️ Azure Virtual Machine

![VM](Python%20Wireshark/01-azure-vm-overview.png)

A Linux (Ubuntu 24.04) virtual machine was deployed in Microsoft Azure to act as the target system for traffic generation and analysis.

---

### 🌐 Networking Configuration

![Networking](Python%20Wireshark/02-networking-overview.png)

Basic network configuration was reviewed, including public IP assignment and virtual network settings to allow external connectivity for testing.

---

### 🔐 NSG Inbound Rules

![NSG](Python%20Wireshark/03-nsg-inbound-rules.png)

Network Security Group (NSG) rules were configured to allow:

* SSH (port 22) for remote access
* ICMP and HTTP traffic for testing and analysis

---

## 💻 System Access

### 🖥️ Linux Access & Network Info

![Linux](Python%20Wireshark/04-linux-access-and-network.png)

Connected to the VM and verified system details such as IP address, network interfaces, and connectivity.

---

### 🔑 SSH Connection

![SSH](Python%20Wireshark/07-ssh-successful-login.png)

Secure remote access was established using SSH from a local machine to manage and interact with the cloud-hosted system.

---

## 📡 Traffic Generation

### 📶 ICMP Traffic (Ping)

![Ping](Python%20Wireshark/08-traffic-generation-ping.png)

Generated ICMP traffic using `ping` to simulate normal network communication and establish a baseline for analysis.

---

### ⚠️ Simulated Suspicious Traffic

![Suspicious](Python%20Wireshark/09-suspicious-traffic-loop.png)

Simulated abnormal behavior by repeatedly sending traffic in a loop to mimic high-frequency or suspicious activity patterns.

---

## 📦 Packet Capture

### 📥 tcpdump Installed

![tcpdump](Python%20Wireshark/05-tcpdump-installed.png)

Installed `tcpdump`, a command-line packet capture tool used to monitor network traffic directly on the VM.

---

### 🎥 Capturing Traffic

![Capture](Python%20Wireshark/06-tcpdump-capturing.png)

Captured live network traffic, including both normal (ICMP) and simulated suspicious activity.

---

### 💾 PCAP File Created

![PCAP](Python%20Wireshark/10-pcap-file-created.png)

Saved captured traffic to a `.pcap` file for offline analysis.

---

### 🔄 Download to Local Machine

![Download](Python%20Wireshark/11-pcap-download.png)

Transferred the `.pcap` file from the VM to a local machine for deeper inspection using Wireshark.

---

## 🔍 Wireshark Analysis

### 📶 ICMP Analysis

![ICMP](Python%20Wireshark/12-wireshark-icmp.png)

Analyzed ICMP traffic to observe normal request/response behavior and establish a baseline.

---

### 🌐 HTTP Analysis

![HTTP](Python%20Wireshark/13-wireshark-http.png)

Inspected HTTP traffic to identify patterns such as repeated requests or anomalies in communication behavior.

---

## 🧠 Python Threat Detection

### ⚙️ Scapy Setup

![Scapy](Python%20Wireshark/14-python-scapy-installed.png)

Configured Python with the Scapy library to programmatically analyze packet data.

---

### 🚨 Detection Output

![Detection](Python%20Wireshark/15-python-threat-detection.png)

Developed a Python script to process packet captures and identify suspicious activity patterns.

---

## 🐍 Python Detection Script

```python
from scapy.all import rdpcap, IP
from collections import Counter

# Load the pcap file
packets = rdpcap("capture.pcap")

ip_counter = Counter()

# Analyze packets
for packet in packets:
    if packet.haslayer(IP):
        src_ip = packet[IP].src
        ip_counter[src_ip] += 1

# Display top talkers
print("Top Talkers:")
for ip, count in ip_counter.most_common(5):
    print(f"{ip}: {count} packets")

# Detect suspicious behavior
THRESHOLD = 20

print("\nPotential Suspicious Activity:")
for ip, count in ip_counter.items():
    if count > THRESHOLD:
        print(f"[ALERT] {ip} exceeded threshold with {count} packets")
```

---

## ⚙️ Detection Logic

The Python script analyzes packet capture data and identifies:

* **Top Talkers** → IPs generating the most traffic  
* **Traffic Spikes** → unusually high request frequency  
* **Potential Scanning Behavior** → repeated connection attempts  

This demonstrates foundational **detection engineering concepts** used in SOC environments.

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

This project demonstrates a full end-to-end workflow for capturing, analyzing, and detecting network activity in a controlled environment.

It reflects real-world SOC analyst responsibilities, including traffic inspection, behavioral analysis, and building simple detection logic using scripting.
