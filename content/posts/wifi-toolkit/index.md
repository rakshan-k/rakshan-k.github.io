---
author: "Rakshan-K"
title: "Wi-Fi Offensive and Defensive Security Toolkit – A Complete Cybersecurity Project"
date: "2025-04-30"
tags: ["Wi-Fi Security", "Cybersecurity", "Wireless Attacks", "Offensive Security", "Defensive Security", "Python", "Raspberry Pi"]
cover:
    image: "img/wifi-toolkit-cover.png"  # Replace with your image path or link
    alt: "Wi-Fi Security Toolkit"
    caption: "A hands-on cybersecurity toolkit for learning and defending Wi-Fi networks."
    relative: true
---

# Wi-Fi Offensive and Defensive Security Toolkit 🚨🔐

Having dedicated the past year and a half to my final year project, I've successfully developed a powerful and hands-on Wi-Fi Offensive and Defensive Security Toolkit leveraging the capabilities of Python and Scapy on a Raspberry Pi. This project goes beyond theoretical concepts, providing a practical platform to simulate real-world wireless attacks and implement effective defense mechanisms.

Designed as both an educational resource and a robust security auditing tool, this toolkit offers invaluable hands-on experience with the offensive and defensive intricacies of Wi-Fi networks. Whether you're a fellow penetration tester, a cybersecurity student looking to bridge the gap between theory and practice, or a hobbyist eager to explore the depths of wireless security, this project offers a unique and practical learning opportunity.

---

## Introduction

In today's world, wireless networks remain a primary target for attackers due to inherent vulnerabilities in the Wi-Fi protocol stack. Traditional tools often address either attack or defense — rarely both. This project bridges that gap.

The **Wi-Fi Offensive and Defensive Security Toolkit** is a Raspberry Pi-based solution designed to **scan**, **attack**, **detect**, and **defend** Wi-Fi networks in real time. Built using Python and Scapy, it provides hands-on insight into wireless attacks and mitigation strategies through a modular, menu-driven interface.

---

## 1. System Overview

The toolkit is built around four core modes:

- **Offensive Mode**: Includes deauthentication, beacon flooding, WPA2 handshake capture, MITM, and DNS spoofing.
- **Defensive Mode**: Detects deauth attacks, rogue APs, ARP spoofing, and triggers alerts.
- **War Driving Mode**: Logs surrounding APs and performs security audits based on encryption type.
- **Automated Mode**: Executes chained attacks autonomously — from scanning to key cracking.

All modes are powered by Scapy for raw packet manipulation and Hostapd for fake AP creation. The toolkit also includes a **real-time intrusion dashboard** hosted on Flask, accessible via browser.

---

## 2. Key Features

### ✅ Offensive Capabilities

- **Deauthentication Attack**
- **Beacon Flooding / Fake APs**
- **WPA2 Handshake Capture**
- **ARP Spoofing & DNS Spoofing**
- **SSL Stripping & Credential Harvesting**

### 🛡️ Defensive Capabilities

- **Rogue AP Detection**
- **Deauth Detection**
- **ARP Spoofing Alerts**
- **Dashboard Logging with Timestamp**

### 📍 Recon & Audit

- **War Driving Module**
- **AP Security Score Classification (Open → WPA2-802.11w)**
- **GPS Tagging & Signal Strength Filtering**

### 🧠 Educational Design

- **Menu-Driven UI**
- **Modular Codebase for Custom Extensions**
- **Includes Real-World Test Results**

---

## 3. Testing Methodologies

### 3.1 Unit Testing

Each module was tested in isolation:

- **Packet Injection Testing**: Verified proper crafting of deauth and beacon packets.
- **Handshake Capture**: Ensured .cap files were compatible with Aircrack-ng.
- **Fake AP Broadcasts**: Confirmed visibility on client devices.
- **Dashboard Logging**: Checked accurate and real-time updates.

### 3.2 Integration Testing

All modules were integrated and tested together:

- **Automated Mode Execution**: Confirmed smooth transitions across attack stages.
- **Defense Mode**: Detected all injected attacks in near real-time.
- **Recon + Audit Workflow**: Seamlessly logged APs and calculated scores.

### 3.3 Performance Testing

Measured under varying conditions:

- **Handshake Capture Time**: 3–7 minutes average (weak passphrases).
- **Deauth Success Rate**: 80–90% depending on AP proximity.
- **Dashboard Latency**: Alerts showed within 3–5 seconds.
- **Resource Use**: CPU/memory remained under 70% on Raspberry Pi 4.

### 3.4 Security Testing

Real-world attacks were simulated:

- **MITM + Credential Capture**
- **DNS Spoofing with Fake Google Login**
- **Resilience Testing with WPA2-802.11w Enabled APs**

---

## 4. Contributions and Innovations

### 🔐 Protocol-Level Discovery

Attempted to block deauthentication attacks via software filtering, but discovered that **802.11w (Management Frame Protection)** was the most reliable solution. The toolkit thus recommends hardened APs using `hostapd` with WPA2 + 802.11w.

### 🧰 Integrated Attack-Defense Framework

Unlike other tools, this combines both offensive and defensive modules. Ideal for **penetration testers**, **researchers**, and **students** alike.

### 🛰️ Real-Time Intrusion Dashboard

Built-in dashboard shows:

- Active attacks
- Spoofed frames
- Detected rogue APs
- Deauth logs and timestamps

### 🧬 Custom Packet Engineering

Every attack is custom-coded in Scapy, unlike tools like `aircrack-ng` that abstract low-level behavior. This gives fine-grained control for educational purposes.

### 🔁 Fully Automated Mode

Automatically loops through:

1. Scan for APs
2. Select weakest one
3. Launch deauth
4. Capture handshake
5. Crack password
6. Log and move to next

---

## 5. Results and Analysis

### 5.1 Handshake Capture & Cracking

- ✅ **85% capture rate** across test APs
- ⏱️ **3–7 mins** average cracking time (weak passwords)
- ❌ Strong WPA2 passwords resisted dictionary attacks

### 5.2 Deauthentication Attacks

- 💥 **90% success** in client disconnection
- 📶 Best results within **10 meters**
- ⚠️ 802.11w APs mitigated most attacks

### 5.3 MITM & ARP Spoofing

- ✅ **100% success** on non-802.1X networks
- 🕵️‍♂️ Unencrypted traffic yielded credentials
- 🛡️ Detected within **10 seconds**

### 5.4 DNS Spoofing

- ✅ Successful redirection post-ARP spoofing
- 🎯 Harvested credentials via fake Google login
- 🔓 Worked only on non-HSTS and HTTP sites

### 5.5 Rogue AP Detection

- 🔍 **100% detection** via SSID/MAC mismatch
- 🚫 **85% DoS success** on fake APs
- 🧭 Dashboard flagged excessive beacons in **<5s**

### 5.6 Recon & AP Audit

- 📊 Logged 50+ APs in 500m radius
- 🧠 Classification accuracy: **95%**
  - Open / WEP / Weak WPA2 / WPA2+802.11w

### 5.7 Defense Mode

- 🛡️ **98% detection** of deauth & ARP spoofing
- ⏱️ Alerts triggered within **3–5 seconds**
- 🧱 WPA2-802.11w APs resisted **90%** of deauths

### 5.8 Automated Mode

- ⚙️ **80% success** rate in chained attacks
- 📆 **4–6 minutes/AP** on average
- 🔁 Skipped failed attempts to optimize workflow

---

## Conclusion

The **Wi-Fi Offensive and Defensive Toolkit** is a unique, hands-on solution for learning, testing, and securing Wi-Fi networks. It doesn't just execute attacks — it **teaches** how they work and how to mitigate them.

Whether you're a cybersecurity student, a red teamer, or a wireless researcher, this project provides:

- 📚 A modular learning environment
- 🔐 Practical defense tools
- ⚔️ Real-world attack simulation
- 💡 Protocol-level insights

With growing threats in wireless environments, understanding both sides of the security spectrum is no longer optional — it's essential.

---

## Next Steps

- 📥 Project repo and codebase (coming soon)
- 📦 Install script for easy deployment
- 🧪 Add support for WPA3 and Evil Twin detection
- 💬 Leave feedback or contribute to future versions!

---

*Built with Scapy, Python, Raspberry Pi, and a passion for wireless security.*  

