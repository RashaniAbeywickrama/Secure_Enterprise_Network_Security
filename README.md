# Secure Enterprise Network Infrastructure & Network Security

## Project Overview

This project focuses on designing and implementing a secure enterprise network infrastructure using **Cisco Packet Tracer**.

The network simulates an enterprise environment with multiple departments, separate VLANs, centralized network management, internal servers, and an external ISP connection.

The main objective is to improve network segmentation, control communication between departments, secure network device management, and provide external network connectivity through NAT/PAT.

## Technologies & Tools

- Cisco Packet Tracer
- Cisco IOS CLI
- VLANs and Inter-VLAN Routing
- IEEE 802.1Q Trunking
- Extended Access Control Lists (ACLs)
- SSH Remote Management
- Port Security
- DHCP Snooping
- Spanning Tree Protocol (STP)
- Static Routing
- Network Address Translation (NAT)
- Port Address Translation (PAT)

## Network Topology

The simulated network consists of:

- 1 Edge Router
- 1 ISP Router
- 1 Multilayer Core Switch
- 2 Access Switches
- Multiple department PCs
- Internal Server
- DMZ Server

The multilayer switch provides inter-VLAN routing, while the edge router connects the enterprise network to the simulated ISP.

## VLAN and IP Addressing Plan

| VLAN ID | Department / Purpose | Network |
|---|---|---|
| 10 | Management | 192.168.10.0/24 |
| 20 | HR | 192.168.20.0/24 |
| 30 | Finance | 192.168.30.0/24 |
| 40 | IT Department | 192.168.40.0/24 |
| 50 | Internal Servers | 192.168.50.0/24 |
| 60 | DMZ | 192.168.60.0/24 |
| 70 | Guest | 192.168.70.0/24 |
| 99 | Network Management | 192.168.99.0/24 |

Each VLAN uses a separate IP subnet and default gateway to provide network segmentation.

## Implemented Features

### 1. VLAN Configuration and Network Segmentation
- Created separate VLANs for enterprise departments.
- Assigned switch access ports to the appropriate VLANs.
- Configured trunk links between switches.
- Implemented inter-VLAN routing using a multilayer switch.

### 2. Access Control Lists (ACLs)
- Configured extended ACLs to control inter-VLAN communication.
- Restricted Guest VLAN access to internal network resources.
- Blocked communication between HR and Finance.
- Configured SSH access restrictions for network devices.

### 3. SSH Remote Management
- Configured SSH version 2.
- Created local administrator accounts.
- Generated RSA encryption keys.
- Restricted remote SSH access to the authorized IT workstation.
- Successfully tested SSH connections to all three switches from PC-IT.

### 4. Switch Port Security
- Enabled port security on end-device access ports.
- Configured sticky MAC address learning.
- Limited each protected port to one secure MAC address.
- Configured violation mode to shutdown.
- Tested a port-security violation and recovered the affected port.

### 5. DHCP Snooping
- Enabled DHCP Snooping on the access switches.
- Configured the relevant VLANs.
- Configured trusted uplink ports.
- Verified DHCP Snooping settings.

Note: DHCP address assignment is not yet successfully validated and remains pending further testing.

### 6. Spanning Tree Protocol Protection
- Configured PortFast on end-device access ports.
- Enabled BPDU Guard on end-device access ports.

### 7. Static Routing
- Configured static routes between the core switch, edge router, and ISP router.
- Configured a default route towards the ISP.
- Verified connectivity to the simulated external network.

### 8. NAT and PAT
- Configured NAT inside and outside interfaces.
- Implemented NAT overload (PAT).
- Allowed internal private IP addresses to access the simulated external network using the edge router's outside IP address.
- Verified NAT translations and statistics.

## Network Security and Connectivity Testing

The following tests were performed during implementation.

| Test Scenario | Expected / Observed Result |
|---|---|
| Management PC to default gateway | Successful |
| HR PC to default gateway | Successful before DHCP testing |
| IT PC to default gateway | Successful |
| Guest PC to default gateway | Successful |
| HR to IT communication | Successful |
| HR to Finance communication | Blocked |
| Guest to HR communication | Blocked |
| Guest to Internal Server communication | Blocked |
| SSH from IT PC to SW1-CORE | Successful |
| SSH from IT PC to SW2-ACCESS | Successful |
| SSH from IT PC to SW3-ACCESS | Successful |
| Port security violation test | Successful |
| NAT from Management PC | Successful |
| NAT from IT PC | Successful |
| DHCP address assignment | Pending validation |

## NAT Testing

A simulated external destination was configured on the ISP router:

- External test IP: `198.51.100.1`
- Edge router outside IP: `203.0.113.1`

NAT translations were verified for:

- Management PC: `192.168.10.10`
- IT PC: `192.168.40.10`

Both internal devices successfully accessed the simulated external destination through NAT/PAT.

## Learning Outcomes

Through this project, I gained practical experience in:

- Designing and configuring enterprise network topologies.
- Implementing VLAN-based network segmentation.
- Configuring inter-VLAN routing and trunk links.
- Applying ACLs to control network traffic.
- Securing network devices using SSH.
- Implementing switch port security.
- Configuring DHCP Snooping and STP protections.
- Configuring static routing between network devices.
- Implementing and verifying NAT/PAT.
- Testing network connectivity and troubleshooting configuration issues.

GitHub: [RashaniAbeywickrama](https://github.com/RashaniAbeywickrama)
