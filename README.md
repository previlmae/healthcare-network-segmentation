Healthcare Wi-Fi Network Segmentation
Securing Patient Data Through VLAN Segmentation and Access Control

IT 700 Capstone Project | Southern New Hampshire University | Master of Science in Information Technology

 Project Overview

This project designs, simulates, and tests a HIPAA-compliant, segmented wireless network infrastructure for a small rural health clinic serving an underserved, low-income community. The clinic's existing flat network mixed patient guest Wi-Fi, clinical workstations, and administrative systems on a single unsegmented network — a direct violation of the HIPAA Security Rule.

The solution replaces this insecure architecture with three completely isolated network segments enforced by VLANs and Access Control Lists (ACLs) on a Cisco 3560 Multilayer Switch, simulated and tested in Cisco Packet Tracer.

 The Problem

Small healthcare providers in rural and underserved communities routinely operate on flat, consumer-grade networks where:

- Guest Wi-Fi and clinical EHR systems share the same network
- No traffic isolation or access controls exist between patient-facing and clinical devices
- Any device connected to waiting room Wi-Fi can potentially reach medical records

This violates HIPAA 45 CFR § 164.312(a)(1) (Access Control) and exposes the clinic to federal fines, data breaches, and potential closure.

 The Solution

A three-VLAN segmented network architecture that creates isolated "lanes" for each user group:

VLAN	Name	Subnet	Purpose
VLAN 10	Clinical	192.168.10.0/24	Doctors, nurses, EHR Server
VLAN 20	Administrative	192.168.20.0/24	Front desk, billing
VLAN 30	Guest	192.168.30.0/24	Patient waiting room Wi-Fi

ACL (BLOCK_GUEST) is applied to VLAN 30 to deny all traffic destined for the clinical and administrative subnets while permitting internet access.

Technologies Used:
Tool	Purpose
Cisco Packet Tracer	Network simulation and testing
Cisco 3560 Multilayer Switch	Layer 3 switching, inter-VLAN routing, DHCP, ACL enforcement
Cisco 2911 Router	Gateway router
draw.io	Network topology diagram
NIST CSF v1.1	Security framework alignment
NIST SP 800-66	HIPAA Security Rule implementation guidance
 Test Results

Two critical tests were conducted to verify the solution:

Test 1 — Guest Isolation (Critical Security Test)
From: PC-Guest (192.168.30.10)
To:   EHR-Server (192.168.10.3)

Result: Packets Sent = 4, Received = 0, Lost = 4 (100% loss) 

The ACL successfully blocks all unauthorized guest traffic from reaching patient medical records.

Test 2 — Clinical Access Verification
From: PC-Clinical (192.168.10.2)
To:   EHR-Server (192.168.10.3)

Result: Packets Sent = 4, Received = 4, Lost = 0 (0% loss) 

Authorized clinical staff retain full, unimpeded access to the EHR Server.

🗂️ Repository Contents
📁 healthcare-network-segmentation/
├── 📄 README.md                          ← You are here
├── 📄 IT700_Final_Report.pdf             ← Full capstone project report (APA)
├── 📁 simulation/
│   └── 🖧  HealthcareNetwork.pkt         ← Cisco Packet Tracer simulation file
├── 📁 diagrams/
│   └── 🗺️  NetworkTopology.drawio        ← Editable network topology diagram
│   └── 🖼️  NetworkTopology.png           ← Exported topology diagram
└── 📁 evidence/
    ├──   Fig1_VLAN_Creation.png
    ├──   Fig2_VLAN_IP_Addresses.png
    ├──   Fig3_DHCP_Configuration.png
    ├──   Fig4_PCAdmin_DHCP.png
    ├──   Fig5_PCClinical_DHCP.png
    ├──  Fig6_EHRServer_DHCP.png
    ├──  Fig7_ACL_Configuration.png
    ├──   Fig8_Guest_Isolation_Test.png  ← 100% packet loss 
    └──   Fig9_Clinical_Access_Test.png  ← 0% packet loss 
 How to Open the Simulation
Download and install Cisco Packet Tracer (free with Cisco NetAcad account)
Open HealthcareNetwork.pkt
Click on PC-Guest → Desktop → Command Prompt
Type ping 192.168.10.3 to verify the guest isolation test
Click on PC-Clinical → Desktop → Command Prompt
Type ping 192.168.10.3 to verify clinical access
 Compliance & Frameworks

This project aligns with the following standards and regulations:

HIPAA Security Rule — 45 CFR § 164.312(a)(1) Access Control
HIPAA Security Rule — 45 CFR § 164.312(e)(1) Transmission Security
NIST Cybersecurity Framework v1.1 — Protect function
NIST SP 800-66 — HIPAA Security Rule implementation for healthcare
 Future Enhancements:
IDS Integration — Add Snort for real-time intrusion detection and alerting
Multi-Site VPN — Expand to site-to-site VPN tunnels for multi-location clinics
Zero Trust Architecture — Evolve from perimeter-based to identity-aware access control
Change Management — Implement SolarWinds NCM for auditable configuration tracking
 Why This Matters

Rural and low-income communities often rely on small clinics as their only accessible healthcare option. A data breach at one of these facilities doesn't just mean a fine — it can mean the clinic closes permanently, eliminating care for an entire community.

This project demonstrates that enterprise-grade network security is achievable on a small-clinic budget, using widely available tools and industry-standard frameworks.


Elvie Previlma M.S. Information Technology — Southern New Hampshire University LinkedIn | GitHub

 References
Cisco Systems. (2024). Cisco Packet Tracer. https://www.netacad.com
National Institute of Standards and Technology. (2018). NIST CSF v1.1. https://www.nist.gov/cyberframework
National Institute of Standards and Technology. (2008). NIST SP 800-66. https://doi.org/10.6028/NIST.SP.800-66
U.S. Department of Health and Human Services. (1996). HIPAA. https://www.hhs.gov/hipaa
