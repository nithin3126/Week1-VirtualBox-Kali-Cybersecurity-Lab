# 🔐 Week 1 – Cybersecurity Lab Environment Setup

### Building a Virtual Cybersecurity Testing Environment using Oracle VirtualBox and Kali Linux

## 📌 Project Overview

As part of my Week 1 cybersecurity practical assignment, I started building my personal cybersecurity testing laboratory using Oracle VirtualBox and Kali Linux.

The main objective is to create a virtual environment where I can perform cybersecurity experiments, network analysis, penetration testing and security-related practical exercises in a controlled environment.

This laboratory will also serve as the foundation for my upcoming cybersecurity projects.

## 🎯 Project Objectives

* Install and configure Oracle VirtualBox.
* Import and run Kali Linux as a virtual machine.
* Create a dedicated NAT Network.
* Configure virtual machine network connectivity.
* Configure IPv4 networking.
* Enable bidirectional shared clipboard.
* Enable bidirectional drag and drop.
* Test network connectivity.
* Troubleshoot network-related issues.

## 🛠️ Lab Environment

| Component               | Configuration             |
| ----------------------- | ------------------------- |
| Virtualization Platform | Oracle VirtualBox         |
| Operating System        | Kali Linux                |
| Kali VM Version         | 2026.3                    |
| VM Memory               | 2048 MB (2 GB)            |
| Network Mode            | NAT Network               |
| Network Name            | NatNetwork                |
| Target Network          | 10.0.0.0/24               |
| Default Gateway         | 10.0.0.1                  |
| Network Adapter         | Intel PRO/1000 MT Desktop |
| Promiscuous Mode        | Allow All                 |
| Shared Clipboard        | Bidirectional             |
| Drag and Drop           | Bidirectional             |

**Note:** The VirtualBox network list currently displays `10.0.2.0/24`, while the editable IPv4 Prefix field displays `10.0.0.0/24`. The effective configuration needs to be verified.

## 🏗️ Lab Configuration

### 1. NAT Network Configuration

Created a virtual NAT Network named `NatNetwork` in VirtualBox.

Configuration shown in the settings:

* Network Name: NatNetwork
* Intended IPv4 Prefix: 10.0.0.0/24
* DHCP: Enabled
* IPv6: Disabled

<img width="1917" height="1012" alt="01-nat-network" src="https://github.com/user-attachments/assets/e2e14a36-f097-43a1-acec-294d0145b837" />


### 2. Kali Linux Virtual Machine Configuration

Imported and started the Kali Linux virtual machine.

Configured Adapter 1 with the following settings:

```text
Attached to: NAT Network
Network: NatNetwork
Adapter Type: Intel PRO/1000 MT Desktop
Promiscuous Mode: Allow All
Virtual Cable: Connected
```

Allocated 2048 MB RAM to the virtual machine.

<img width="1907" height="975" alt="02-kali-vm-settings (2)" src="https://github.com/user-attachments/assets/5183902a-ab70-4efc-86df-30d1a7363283" />


### 3. Shared Clipboard and Drag & Drop

Enabled the following VirtualBox integration settings:

```text
Shared Clipboard: Bidirectional
Drag and Drop: Bidirectional
```

These settings allow easier interaction and file exchange between the host and virtual machine.

<img width="1915" height="1012" alt="04-kali-snapshot" src="https://github.com/user-attachments/assets/0b1af015-4bb8-413a-a52a-0696cee236c1" />


## 🌐 Network Configuration and Testing

Checked Kali Linux network configuration using:

```bash
ip -br addr
ip route
```

Observed configuration:

```text
Interface: eth0
IP Address: 10.0.0.3/24
Gateway: 10.0.0.1
```

**Important:** The assignment requires `10.0.0.2/24`. The current observed address is `10.0.0.3/24`, so this still needs correction.

### Connectivity Testing

Performed gateway and external IP connectivity tests.

**Gateway Test:**

```bash
ping -c 4 10.0.0.1
```

Result:

* 4 packets transmitted
* 4 packets received
* 0% packet loss

**External IP Test:**

```bash
ping -c 4 1.1.1.1
```

Result:

* 2 replies received before manually interrupting the test.
* Full test still needs verification.

**DNS Resolution Test:**

```bash
ping -c 4 google.com
```

Result:

```text
Temporary failure in name resolution
```

DNS resolution was not working during this test.

<img width="1280" height="800" alt="03-kali-connectivity" src="https://github.com/user-attachments/assets/a495c4f3-0322-4e8f-8837-0820a923e622" />


## 🐛 Problems Encountered and Troubleshooting

During the lab setup, I encountered a network connectivity/DNS resolution issue.

I used NetworkManager commands to restart the network connection.

```bash
sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0

sudo nmcli connection down "Wired connection 1"

sudo nmcli connection up "Wired connection 1"
```

The connection was successfully deactivated and activated.

After restarting the connection:

* Gateway connectivity was successful.
* External IP connectivity returned replies.
* DNS resolution was still unsuccessful.

This helped me understand the importance of troubleshooting IP connectivity and DNS resolution separately.

## 📚 What I Learned

Through this practical assignment, I gained hands-on experience with:

1. Virtual machine creation and configuration.
2. NAT Network configuration in VirtualBox.
3. Virtual network adapter settings.
4. IPv4 addressing and subnet configuration.
5. Linux networking commands.
6. NetworkManager and connection management.
7. Connectivity troubleshooting.
8. VirtualBox clipboard and drag-and-drop integration.


## 🔐 Ethical Use

This laboratory is intended strictly for educational purposes, cybersecurity learning and authorized security testing.

All testing will be conducted only against systems that I own or have permission to assess.

## 👨‍💻 Author

**Nithin S**

Cybersecurity Student | Aspiring SOC Analyst | Cybersecurity Enthusiast

---

### Project Information

**Project:** Cybersecurity Lab Environment Setup

**Week:** 01

**Platform:** Oracle VirtualBox

**Operating System:** Kali Linux

**Documentation:** GitHub
