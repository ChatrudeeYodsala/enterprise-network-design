# Enterprise Network Design

## Project Overview

This project demonstrates the design and implementation of a simulated enterprise network using Cisco Packet Tracer. The network is designed to reflect a real-world organizational structure with multiple departments, VLAN segmentation, inter-VLAN communication using Router-on-a-Stick architecture, centralized DHCP services, and network security using ACLs.

The main objective of this project is to apply enterprise-level networking concepts including switching, routing, IP management, and security policies.

## Network Topology

The network follows a hierarchical design model:

- Core Layer (Core Switch)
- Distribution Layer (Router)
- Access Layer (Switches)
- End Devices Layer

### Devices Used

- 1 × Cisco 2911 Router (R1)
- 1 × Cisco 2960 Core Switch (Core-SW1)
- 2 × Cisco 2960 Access Switches (Access-SW2, Access-SW3)
- Multiple End Devices (PCs)
- 1 × Enterprise Server (DHCP Server)

### Topology Structure

End Devices → Access Switches → Core Switch → Router → Server / Other VLANs

## VLAN Design

The network is segmented into multiple VLANs to isolate departments and improve security and performance.

| VLAN ID | Department   | Network Address     |
|----------|--------------|---------------------|
| 10       | Management   | 192.168.10.0/24     |
| 20       | HR           | 192.168.20.0/24     |
| 30       | IT           | 192.168.30.0/24     |
| 40       | Sales        | 192.168.40.0/24     |
| 50       | Server       | 192.168.50.0/24     |

Each VLAN represents a separate broadcast domain.

## Inter-VLAN Routing

Inter-VLAN communication is implemented using Router-on-a-Stick configuration on R1.

### Router Subinterfaces

- G0/0.10 → VLAN 10 → 192.168.10.1  
- G0/0.20 → VLAN 20 → 192.168.20.1  
- G0/0.30 → VLAN 30 → 192.168.30.1  
- G0/0.40 → VLAN 40 → 192.168.40.1  
- G0/0.50 → VLAN 50 → 192.168.50.1  

Each subinterface uses IEEE 802.1Q encapsulation.

## DHCP Implementation

A centralized DHCP server is used to automatically assign IP addresses to all end devices.

Each VLAN has a dedicated DHCP pool configured with:

- Default Gateway
- Subnet Mask
- IP Address Range
- DNS Server

This removes the need for manual IP configuration on each device.

## DHCP Relay Configuration

Since the DHCP server is located in VLAN 50, router-based DHCP relay is required.

The `ip helper-address` command is configured on all VLAN subinterfaces to forward DHCP requests to the DHCP server.

This enables centralized IP management across all VLANs.

## Switching Configuration

### Core Switch Configuration

- VLANs 10, 20, 30, 40, 50 created on all switches
- Trunk links configured using IEEE 802.1Q
- Access ports assigned per department

### Access Switch Configuration

- HR-PC → VLAN 20
- IT-PC → VLAN 30
- Sales-PC → VLAN 40
- Management-PC → VLAN 10
- Server → VLAN 50

## ACL Security Implementation

Access Control Lists (ACLs) were implemented on router R1 to control inter-VLAN communication.

### Security Policies

- HR is restricted from accessing IT network
- Sales is allowed to access only Server network
- Management has full access to all VLANs

### ACL Configuration Summary

Extended ACLs were applied on router subinterfaces to filter traffic between VLANs based on source and destination IP addresses.

## Testing & Verification

Network functionality was tested using the following methods:

- Successful DHCP IP assignment on all PCs
- Inter-VLAN communication using ICMP (ping)
- ACL enforcement verified using blocked and allowed ping tests
- Router subinterface and trunk link verification

All tests confirmed correct network operation.

## Network Traffic Flow

End Device → Access Switch → Core Switch → Router → DHCP Server / Other VLANs

This represents a real enterprise network architecture with centralized routing and controlled access.

## Tools & Technologies Used

- Cisco Packet Tracer
- Cisco 2911 Router
- Cisco 2960 Switches
- VLAN Configuration
- Trunking (IEEE 802.1Q)
- Router-on-a-Stick Inter-VLAN Routing
- DHCP Server Configuration
- DHCP Relay (ip helper-address)
- Access Control Lists (ACL)

## Learning Outcomes

Through this project, the following skills were developed:

- Enterprise network design and segmentation
- VLAN configuration and management
- Inter-VLAN routing implementation
- DHCP server setup and management
- DHCP relay configuration
- Network security using ACLs
- Network troubleshooting and verification

## Future Improvements

- Implement STP optimization for redundancy
- Add network monitoring (SNMP/Syslog)
- Implement firewall integration
- Introduce dynamic routing protocols (OSPF/EIGRP)