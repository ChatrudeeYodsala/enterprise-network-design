# Enterprise Network Design 

## Project Overview

This project demonstrates the design and implementation of a simulated enterprise network using Cisco Packet Tracer. The network is designed to reflect a real-world organizational structure with multiple departments, VLAN segmentation, and inter-VLAN communication using Router-on-a-Stick architecture.

The main objective of this project is to practice enterprise-level network design, configuration, and troubleshooting using Cisco networking concepts.

## Network Topology

The network is built using a hierarchical design model consisting of three layers:

- Core Layer
- Distribution Layer (Core Switch)
- Access Layer (Access Switches)

### Devices Used:

- 1 × Cisco 2911 Router (R1)
- 1 × Cisco 2960 Core Switch (Core-SW1)
- 2 × Cisco 2960 Access Switches (Access-SW2, Access-SW3)
- 4 × End Devices (HR-PC, IT-PC, Sales-PC, Management-PC)
- 1 × Enterprise Server

### Topology Structure:

Router → Core Switch → Access Switches → End Devices

## VLAN Design

The network is segmented into multiple VLANs to separate department traffic and improve security and performance.

| VLAN ID | Department   | Network Address     |
|----------|--------------|---------------------|
| 10       | Management   | 192.168.10.0/24     |
| 20       | HR           | 192.168.20.0/24     |
| 30       | IT           | 192.168.30.0/24     |
| 40       | Sales        | 192.168.40.0/24     |
| 50       | Server       | 192.168.50.0/24     |

Each VLAN represents a separate broadcast domain.

## Inter-VLAN Routing

Inter-VLAN routing is implemented using **Router-on-a-Stick** configuration on R1. This allows communication between different VLANs through a single physical interface using subinterfaces and IEEE 802.1Q encapsulation.

### Router Subinterface Configuration:

- GigabitEthernet0/0.10 → VLAN 10 (Management) → 192.168.10.1
- GigabitEthernet0/0.20 → VLAN 20 (HR) → 192.168.20.1
- GigabitEthernet0/0.30 → VLAN 30 (IT) → 192.168.30.1
- GigabitEthernet0/0.40 → VLAN 40 (Sales) → 192.168.40.1
- GigabitEthernet0/0.50 → VLAN 50 (Server) → 192.168.50.1

Each subinterface is configured using 802.1Q encapsulation to identify VLAN traffic.

## Switching Configuration

### Core Switch (Core-SW1)

- VLANs 10, 20, 30, 40, 50 created
- Trunk links configured between:
  - Core-SW1 ↔ Access-SW2
  - Core-SW1 ↔ Access-SW3
  - Core-SW1 ↔ Router (R1)

### Access Switches

Each access switch is configured with access ports assigned to specific VLANs:

- HR-PC → VLAN 20
- Sales-PC → VLAN 40
- IT-PC → VLAN 30
- Management-PC → VLAN 10
- Server → VLAN 50

## Network Design Features

This network implements the following enterprise-level concepts:

- VLAN segmentation for department isolation
- Trunk links for VLAN propagation between switches
- Router-on-a-Stick for inter-VLAN routing
- Centralized routing architecture using R1
- Logical separation of broadcast domains
- Scalable network design suitable for enterprise environments

## Connectivity Verification

Inter-VLAN communication was successfully tested using ICMP (ping).

### Test Results:

- HR-PC can ping IT-PC
- HR-PC can ping Management-PC
- Sales-PC can reach Server
- All VLANs can communicate through Router R1

This confirms that inter-VLAN routing is functioning correctly.

## Network Traffic Flow

The communication flow in the network is as follows:

End Device → Access Switch → Core Switch → Router → Destination VLAN

This architecture simulates a real enterprise network with centralized routing control.

## Tools & Technologies Used

- Cisco Packet Tracer
- Cisco 2911 Router
- Cisco 2960 Switches
- VLAN Configuration
- Trunking (IEEE 802.1Q)
- Router-on-a-Stick Inter-VLAN Routing

## Learning Outcomes

Through this project, the following concepts were practiced:

- Enterprise network design principles
- VLAN segmentation and configuration
- Inter-VLAN routing implementation
- Switch trunk configuration
- Basic network troubleshooting
- IP addressing and subnet planning

## Future Improvements

- Implement DHCP for automatic IP assignment
- Add ACL (Access Control Lists) for security policies
- Implement network redundancy (STP optimization)
- Add monitoring and logging services
- Simulate firewall integration