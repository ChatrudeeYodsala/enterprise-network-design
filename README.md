# Enterprise Network Design using Cisco Packet Tracer

## Project Overview

This project demonstrates the design and implementation of a simulated enterprise network using Cisco Packet Tracer. The network is designed to reflect a real-world organizational structure with multiple departments, VLAN segmentation, inter-VLAN communication using Router-on-a-Stick architecture, and centralized DHCP services.

The main objective of this project is to practice enterprise-level network design, configuration, and troubleshooting using Cisco networking concepts.

## Network Topology

The network is built using a hierarchical design model consisting of three layers:

- Core Layer
- Distribution Layer (Router)
- Access Layer (Switches)
- End Devices Layer

### Devices Used

- 1 × Cisco 2911 Router (R1)
- 1 × Cisco 2960 Core Switch (Core-SW1)
- 2 × Cisco 2960 Access Switches (Access-SW2, Access-SW3)
- 4 × End Devices (HR-PC, IT-PC, Sales-PC, Management-PC)
- 1 × Enterprise Server (DHCP Server)

### Topology Structure

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

Inter-VLAN routing is implemented using Router-on-a-Stick configuration on R1. This allows communication between different VLANs through a single physical interface using subinterfaces and IEEE 802.1Q encapsulation.

### Router Subinterface Configuration

- GigabitEthernet0/0.10 → VLAN 10 → 192.168.10.1
- GigabitEthernet0/0.20 → VLAN 20 → 192.168.20.1
- GigabitEthernet0/0.30 → VLAN 30 → 192.168.30.1
- GigabitEthernet0/0.40 → VLAN 40 → 192.168.40.1
- GigabitEthernet0/0.50 → VLAN 50 → 192.168.50.1

Each subinterface is configured using 802.1Q encapsulation.

## DHCP Implementation

A centralized DHCP server is used to automatically assign IP addresses to all end devices.

Each VLAN has its own DHCP pool containing:

- Default Gateway
- Subnet Mask
- IP Address Range
- DNS Server

This eliminates the need for manual IP configuration on each device.

## DHCP Relay Configuration

Since the DHCP server resides in VLAN 50, router-based DHCP relay is required.

The `ip helper-address` command is configured on all VLAN subinterfaces to forward DHCP requests to the DHCP server.

This enables centralized IP management across all VLANs.

## Switching Configuration

### Core Switch (Core-SW1)

- VLANs 10, 20, 30, 40, 50 created on all switches
- Trunk links configured using IEEE 802.1Q
- Access ports assigned per department

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
- Scalable enterprise network design

## Testing & Verification

Network functionality was verified using the following tests:

- All PCs successfully received IP addresses via DHCP
- Inter-VLAN communication using ICMP (ping) was successful
- Router subinterfaces (802.1Q) were verified as operational
- Trunk links between switches were confirmed active

All tests confirmed proper network operation.

## Network Traffic Flow

End Device → Access Switch → Core Switch → Router → DHCP Server / Other VLANs

This structure reflects a real enterprise network environment.

## Tools & Technologies Used

- Cisco Packet Tracer
- Cisco 2911 Router
- Cisco 2960 Switches
- VLAN Configuration
- Trunking (IEEE 802.1Q)
- Router-on-a-Stick Inter-VLAN Routing
- DHCP Server Configuration
- DHCP Relay (ip helper-address)

## Learning Outcomes

Through this project, the following concepts were practiced:

- Enterprise network design principles
- VLAN segmentation and configuration
- Inter-VLAN routing implementation
- Switch trunk configuration
- DHCP server configuration and management
- Network troubleshooting and verification
- IP addressing and subnet planning

## Future Improvements

- Implement Access Control Lists (ACL) for traffic control between VLANs
- Add redundancy using STP optimization
- Integrate network monitoring system (SNMP/Syslog)
- Simulate firewall-based segmentation
