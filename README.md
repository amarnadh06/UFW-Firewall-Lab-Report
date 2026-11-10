# Host-Based Firewall Configuration & Traffic Filtering (UFW)

![OS](https://img.shields.io/badge/OS-Kali_Linux-557C94?style=flat-square&logo=kalilinux&logoColor=white)
![Tool](https://img.shields.io/badge/Firewall-UFW_%2F_Netfilter-E95420?style=flat-square&logo=linux&logoColor=white)
![Category](https://img.shields.io/badge/Focus-Network_Security-blue?style=flat-square)

## Overview
This repository documents the practical implementation, testing, and verification of host-based packet filtering on **Kali Linux** using **UFW (Uncomplicated Firewall)** and the underlying Linux kernel **Netfilter** subsystem (`iptables`/`nftables`). 

The lab demonstrates how to establish baseline firewall policies, block insecure legacy protocols (`TCP/23` Telnet), validate packet drops across a local subnet using `netcat` and kernel ring buffer logs (`dmesg`), permit secure administrative access (`TCP/22` SSH), and restore the firewall to a clean operational state.

---

## Lab Topology & Environment

| Component | Details |
| :--- | :--- |
| **Operating System** | Kali Linux Rolling (Debian-based x86_64) |
| **Core Utilities** | `ufw` (v0.36.2), `iptables`/`netfilter`, `nc` (Netcat), `dmesg` |
| **Target Host (Kali)** | `192.168.1.50/24` |
| **Remote Test Client** | `192.168.1.10/24` |

---

## Step-by-Step Implementation

### 1. Install and Enable UFW
Update package repositories, install UFW, and enable the service to persist across system reboots.
```bash
sudo apt update && sudo apt install ufw -y
sudo ufw enable
