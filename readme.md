# Secure Hospital Area Network Design

A secure, scalable hospital network design project developed as an academic networking and cybersecurity project. The design uses a **hierarchical three-layer network architecture** with core, distribution, and access layers, together with VLAN segmentation, routing, firewall/NAT, AAA authentication, wireless connectivity, IP telephony, and network services.

> **Project type:** Academic / Network Design & Simulation  
> **Author:** Ashish Sapkota  
> **Institution:**  incoln University College  
> **Date:** September 2023

---

## 📌 Project Overview

Healthcare organizations depend on reliable network infrastructure for electronic health records, communication between departments, medical devices, telemedicine, billing, research, and emergency services.

This project presents a **secure hospital network design** intended for a municipality-level hospital consisting of multiple buildings and floors. The network is designed to be:

- Secure
- Scalable
- Reliable
- Easy to manage
- Easy to troubleshoot
- Adaptable to future medical and IoT devices

The design follows a **hierarchical network architecture** consisting of:

```text
                 ┌───────────────────┐
                 │       CORE        │
                 │ High-speed / L3   │
                 └─────────┬─────────┘
                           │
                 ┌─────────▼─────────┐
                 │   DISTRIBUTION    │
                 │ Routing / Policy  │
                 └─────────┬─────────┘
                           │
                 ┌─────────▼─────────┐
                 │      ACCESS       │
                 │ Users / Devices   │
                 └───────────────────┘
```

---

## 🎯 Objectives

The main objectives of the project are:

1. Provide high-speed network connectivity.
2. Support organized healthcare records and information systems.
3. Improve data security and privacy.
4. Enable efficient data sharing and collaboration.
5. Support wired and wireless medical devices.
6. Provide secure communication between hospital departments.
7. Support future expansion of the hospital network.
8. Provide reliable services for critical healthcare operations.

---

## 🏥 Hospital Network Scenario

The proposed environment represents a municipality-level hospital with:

- Multiple buildings
- Multiple floors
- Reception areas
- Medical stores
- Nurse stations
- Doctor offices
- Patient rooms
- Operation theatre areas
- Emergency/mortuary areas
- Administrative departments
- Data center/server infrastructure
- Visitor wireless access
- Medical IoT devices
- IP phones
- Internet connectivity

The original design assumes approximately **400–500 simultaneous Internet users** and includes provisions for future hospital expansion.

---

## 🏗️ Network Architecture

### 1. Core Layer

The core layer acts as the high-speed backbone of the hospital network.

Responsibilities include:

- High-speed packet forwarding
- Reliable connectivity between network sections
- Low-latency data transport
- Backbone connectivity

The project proposes Cisco 4351 routers and Cisco 6000-series switching infrastructure for the core environment.

### 2. Distribution Layer

The distribution layer provides routing and policy control between different network segments.

Responsibilities include:

- Inter-VLAN routing
- Routing between subnets
- Network policy enforcement
- Connectivity between access and core layers
- Firewall integration

### 3. Access Layer

The access layer connects end users and devices to the network.

Examples include:

- PCs
- Laptops
- IP phones
- Wireless access points
- Medical devices
- Printers
- IoT devices

Cisco 4510 access switches are used in the proposed design.

---

## 🔐 Security Design

Security is an important part of the hospital network because the environment contains sensitive patient and administrative information.

The project incorporates:

### Firewall

An ASA firewall is positioned between the internal hospital network and the external network.

Functions demonstrated include:

- Network address translation (NAT)
- Access control
- Internet connectivity
- Traffic filtering

### VLAN Segmentation

VLANs are used to separate logical groups of users and devices.

The project demonstrates VLANs including:

- VLAN 10
- VLAN 20
- VLAN 30
- VLAN 40

Example access-switch configuration:

```text
interface FastEthernet0/3
 switchport access vlan 10
 switchport mode access
```

### AAA / TACACS+

AAA authentication is used for administrative access to network devices.

The design demonstrates:

- Local authentication
- TACACS+ authentication
- SSH-based management
- Privileged administrative access

### SSH

Separate credentials are configured for administrative/doctor access to network devices.

### NAT

NAT is configured on the ASA firewall to allow internal hosts to access external networks.

---

## 🌐 Networking Technologies

The project covers and demonstrates the following technologies:

| Technology | Purpose |
|---|---|
| Hierarchical Network Design | Organize the network into functional layers |
| VLAN | Network segmentation |
| RIP | Dynamic routing between network segments |
| NAT | Translate internal addresses for external connectivity |
| ASA Firewall | Traffic filtering and network security |
| DHCP | Dynamic IP address assignment |
| SSH | Secure device administration |
| AAA | Authentication and authorization |
| TACACS+ | Centralized device authentication |
| FTP | File transfer |
| SMTP | Email communication |
| NTP | Time synchronization |
| IP Telephony | Internal voice communication |
| Wireless | Connectivity for mobile/medical devices |
| IoT | Support for connected medical devices |

---

## 🖥️ Network Services

### FTP

FTP is used for file transfer between network systems.

### SMTP

SMTP is included for email communication between hospital systems.

### NTP

NTP provides time synchronization for network-connected devices.

Accurate time is particularly useful when troubleshooting and correlating network events.

### DHCP

DHCP dynamically assigns IP addresses to clients.

Example:

```text
ip dhcp pool pool1
 network 192.168.3.0 255.255.255.0
 default-router 192.168.3.1
```

### DNS

DNS services are included in the hospital network to support name resolution.

### IP Telephony

The design includes internal IP phones with example extensions such as:

```text
100
200
300
```

and another phone group using:

```text
1000
2000
3000
```

---

## 📡 Wireless Network

Wireless access points are deployed throughout the hospital to support:

- Laptops
- Smartphones
- Tablets
- Medical equipment
- IoT devices
- Other wireless clients

The original design proposes two wireless access points per floor to improve coverage.

> **Security note:** The original academic configuration contains a legacy WEP example. For a real hospital deployment, WEP should **not** be used. Modern WPA2-Enterprise or WPA3-Enterprise with centralized authentication should be preferred.

---

## 🧮 IP Addressing

The project uses multiple private and simulated network ranges for different hospital areas.

Examples include:

```text
192.168.1.0/24
192.168.2.0/24
192.168.3.0/24
192.168.10.0/24
10.0.0.0/8
20.0.0.0/8
30.0.0.0/8
50.0.0.0/8
```

The project also discusses the difference between:

- Static IP addressing
- Dynamic IP addressing
- DHCP-based addressing

---

## 🔄 Routing

The original implementation uses **RIP** as the dynamic routing protocol.

Example:

```text
router rip
 network 10.0.0.0
 network 20.0.0.0
 network 192.168.2.0
 network 192.168.3.0
```

RIP was used to demonstrate dynamic communication between different network segments.

> **Production consideration:** For a modern hospital deployment, OSPF or another enterprise-grade routing protocol would generally be more appropriate than RIP because of scalability, convergence, and operational requirements.

---

## 🔥 ASA Firewall Configuration

The simulated ASA configuration contains:

- Inside interface
- Outside interface
- Security levels
- Dynamic NAT
- Default route
- Access control
- DHCP

Simplified example:

```text
interface Vlan1
 nameif inside
 security-level 100

interface Vlan2
 nameif outside
 security-level 0

object network LAN
 subnet 172.168.1.0 255.255.255.0
 nat (inside,outside) dynamic interface
```

The original project also demonstrates access-control rules for traffic entering the network.

---

## 🧪 Implementation & Testing

The project includes configuration and verification activities for:

- VLAN connectivity
- Inter-network communication
- FTP
- SMTP
- NTP
- SSH
- TACACS+
- NAT
- RIP
- DHCP
- IP telephony
- IoT services
- Firewall connectivity

Testing examples include:

```text
Ping from same VLAN
Ping between different VLANs
```

and verification of:

```text
FTP
SMTP
NTP
SSH
TACACS+
RIP
NAT
```

---

## 🗺️ Major Network Areas

The implementation is divided into functional hospital areas.

### Emergency / Mortuary

Contains:

- Router
- FTP/SMTP server
- Wireless connectivity
- Emergency-related network devices

### First Floor

Contains:

- Diet office
- IP phones
- IoT/webcam services
- ISP connectivity
- ASA firewall
- DNS server

### Doctor Office

Provides:

- Individual login credentials
- SSH access
- Network connectivity to hospital systems

### Operation Theatre / Patient Rooms

Provides:

- Wireless connectivity
- Patient-room communication
- Network access for doctors and devices

### Administration

Contains:

- Administrative systems
- VLAN segmentation
- TACACS+ authentication
- Network management controls

---

## 🧰 Proposed Hardware

The original design references the following Cisco infrastructure:

- Cisco 4351 Router
- Cisco 6000 Series Core Switch
- Cisco 5548 Data Center Switch
- Cisco 4510 Access Switch
- Cisco ASA Firewall
- Wireless Access Points
- Servers
- IP Phones
- Cat6 UTP cabling

The exact hardware selection is part of the academic design and should be reassessed against current vendor models and requirements before production deployment.

---

## 📁 Suggested GitHub Repository Structure

A clean repository for this project can be organized as:

```text
secure-hospital-network/
│
├── README.md
│
├── docs/
│   ├── project-report.pdf
│   └── network-design.md
│
├── diagrams/
│   ├── network-topology.png
│   ├── core-layer.png
│   ├── distribution-layer.png
│   └── access-layer.png
│
├── configurations/
│   ├── routers/
│   ├── switches/
│   ├── asa/
│   └── services/
│
├── testing/
│   ├── ftp-verification.png
│   ├── smtp-verification.png
│   ├── ntp-verification.png
│   ├── ssh-verification.png
│   ├── tacacs-verification.png
│   ├── rip-verification.png
│   └── nat-verification.png
│
└── LICENSE
```

---

## 🔒 Security & GitHub Publishing Notes

The original academic document contains example credentials, authentication keys, and passwords in the configuration appendix.

**Do not publish those credentials directly to GitHub.**

For example, replace values such as:

```text
password: <REDACTED>
tacacs-server key <REDACTED>
username <REDACTED>
```

with placeholders before publishing configuration files.

If this project is uploaded as a public repository, also avoid publishing:

- Real passwords
- API keys
- TACACS+ secrets
- Private keys
- Real public IP addresses
- Production device credentials
- Sensitive patient information
- Internal organizational information

---

## 🚀 Future Improvements

The original project recommends a scalable and secure design for future hospital expansion.

Potential modernization areas include:

- Replace RIP with OSPF or another modern routing protocol.
- Replace legacy WEP with WPA2-Enterprise/WPA3-Enterprise.
- Introduce stronger network access control.
- Implement dedicated IoT/medical-device segmentation.
- Add redundancy for critical network components.
- Introduce centralized monitoring and logging.
- Deploy IDS/IPS capabilities.
- Improve high-availability firewall architecture.
- Implement stronger administrative access controls.
- Introduce role-based network access.
- Improve wireless capacity planning.
- Consider modern data-center architectures for future expansion.
- Apply appropriate healthcare security and compliance requirements.

---

## 📚 References

The original project bibliography includes:

1. *The Hospital Network – A New Approach Towards Networking* — Zeeshan Ahmed Siddique.
2. *Hospital Network Infrastructure: A Modern Look Into the Network Backbone with Real Time Visibility* — Homan Mike Hirad.
3. Purdue networking lecture/reference material.
4. Regis University thesis/reference material.

---

## 👤 Author

**Ashish Sapkota**

Cybersecurity & Network Engineering

Kathmandu, Nepal

---

## 📄 Project Information

**Project:** Secure Hospital Area Network Design  
**Academic Submission:** September 27, 2023  
**Department:** Cyber Security and Networking  
**Institution:** Texas College of Management & IT / Lincoln University College

---

## ⚠️ Disclaimer

This repository documents an **academic network design and simulation project**. The configurations and hardware references represent the design created for the original project and should not be deployed directly in a production healthcare environment without security review, redesign, testing, compliance assessment, and appropriate modernization.

