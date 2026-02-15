# Enterprise Network Lab – Cisco Packet Tracer

## 📌 Project Overview

This project simulates a structured multi-level enterprise campus network using Cisco Packet Tracer.

The lab demonstrates VLAN segmentation, inter-VLAN routing (Router-on-a-Stick), DHCP deployment, WAN connectivity simulation, ACL-based traffic restriction, and wireless VLAN integration.

The objective was to design and implement a secure, scalable, and segmented enterprise network environment.

---

## Network Topology

![Enterprise Network Topology](diagrams/enterprise-network-topology.png)

---

## 🏗 Network Architecture

The topology includes:

- Simulated ISP Router
- Core Router (Router-on-a-Stick design)
- Multi-level switching hierarchy
- Department-based VLAN segmentation
- Dedicated Server VLAN
- Guest network with restricted access
- Wireless Access Points integrated per VLAN
- WAN simulation (10.10.10.0/30 link)

---

## 🗂 VLAN Design & IP Addressing

| VLAN | Department | Subnet | Gateway |
|------|------------|--------|---------|
| 10 | Students | 172.16.254.0/23 | 172.16.255.254 |
| 20 | Business | 192.168.0.0/23 | 192.168.1.254 |
| 30 | Staff-Marketing | 192.168.2.0/24 | 192.168.2.254 |
| 40 | Staff-Students | 192.168.3.0/24 | 192.168.3.254 |
| 50 | Guest | 10.10.1.0/23 | 10.10.2.254 |
| 60 | Servers | 172.16.0.0/24 | 172.16.0.254 |

Each VLAN is isolated at Layer 2 and routed through subinterfaces on the Core Router.

---

## 🔁 Inter-VLAN Routing (Router-on-a-Stick)

Inter-VLAN routing was implemented using subinterfaces on the Core Router with 802.1Q encapsulation.

Each VLAN has a dedicated subinterface configured with:

- VLAN ID encapsulation
- Default gateway IP address

This allows communication between departments while maintaining segmentation.

---

## 🌐 DHCP Implementation

Centralized DHCP pools were configured on the Core Router.

Each VLAN automatically receives:

- IP address
- Default gateway
- DNS server

DHCP verification was performed using:
- `show ip dhcp binding`
- Client-side DHCP configuration testing

---

## 🌍 WAN Connectivity Simulation

A serial link (10.10.10.0/30) connects the Core Router to the simulated ISP Router.

A default static route was configured on the Core Router to simulate internet connectivity.

---

## 📡 Wireless Deployment

Wireless access was integrated into the VLAN architecture.

Due to Packet Tracer model limitations (AccessPoint-PT-N), wireless was implemented using one Access Point per VLAN with switch ports configured in access mode.

### SSID Configuration

| SSID | VLAN | Security |
|------|------|----------|
| Abbey-Student | 10 | WPA2-PSK |
| Abbey-Business | 20 | WPA2-PSK |
| Abbey-Staff | 30 | WPA2-PSK |
| Abbey-Guest | 50 | WPA2-PSK |

Wireless clients:

- Successfully obtained IP via DHCP
- Respected VLAN segmentation
- Were restricted by ACL policies (Guest isolation)

---

## 🔐 Security Implementation (ACL)

An extended ACL was configured to:

- Deny traffic from Guest VLAN (50) to Server VLAN (60)
- Permit all other traffic

The ACL was applied inbound on the Guest VLAN subinterface.

This ensures controlled access while maintaining usability for other departments.

---

## 🧪 Testing & Validation

The following verification steps were performed:

- Verified VLAN trunk links (`show interfaces trunk`)
- Verified subinterface status (`show ip interface brief`)
- Tested DHCP assignment across VLANs
- Confirmed inter-VLAN communication
- Validated Guest network isolation
- Verified wireless segmentation behavior
- Performed end-to-end ping testing

---

## 🛠 Troubleshooting Highlights

During implementation, the following issue was identified and resolved:

- Wireless VLAN tagging was not functioning when Access Points were configured on trunk ports.
- Due to Packet Tracer limitations (AccessPoint-PT-N model), AP ports were reconfigured to access mode (one VLAN per AP).
- After reconfiguration, DHCP and connectivity were restored.

This demonstrates real-world troubleshooting methodology and understanding of VLAN behavior.

---

## 💻 Technologies Used

- Cisco Packet Tracer
- VLAN configuration
- 802.1Q trunking
- Router-on-a-Stick
- DHCP services
- Static routing
- Extended ACL configuration
- Wireless SSID deployment
- IP addressing & subnetting

---

## 🎯 Skills Demonstrated

- Layer 2 and Layer 3 network configuration
- Enterprise VLAN segmentation
- Inter-VLAN routing design
- DHCP implementation
- ACL-based traffic control
- Wireless integration into VLAN architecture
- Structured troubleshooting and validation
- Technical documentation

---

## 📂 Repository Structure

- `packet-tracer-file/` – Final .pkt topology file
- `diagrams/` – Network topology screenshots
- `routing-configuration/` – Router configurations
- `dhcp-configuration/` – DHCP pool configuration
- `acl-configuration/` – ACL implementation
- `troubleshooting/` – Scenario analysis & resolution

---

Author: Monica Leiva  
IT Support / Network Support Professional  