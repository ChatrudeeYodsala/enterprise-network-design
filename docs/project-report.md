# Project Report: Enterprise Network Design 

## 1. Introduction

This project presents the design and implementation of a simulated enterprise network using Cisco Packet Tracer. The network models a real-world organization with multiple departments and demonstrates key networking concepts such as VLAN segmentation, inter-VLAN routing, DHCP services, and network security using ACLs.

## 2. Project Objectives

The main objectives of this project are:

- To design a structured enterprise network using a hierarchical model
- To implement VLAN segmentation for department isolation
- To enable inter-VLAN communication using Router-on-a-Stick
- To configure centralized DHCP services for automatic IP assignment
- To implement basic network security using Access Control Lists (ACLs)

## 3. Network Design Overview

The network is designed using a three-layer architecture:

- Core Layer (Core Switch)
- Distribution Layer (Router)
- Access Layer (Switches and End Devices)

The network is segmented into five VLANs representing different departments:

- VLAN 10: Management
- VLAN 20: HR
- VLAN 30: IT
- VLAN 40: Sales
- VLAN 50: Server

Each VLAN represents a separate broadcast domain to improve security and performance.

## 4. Implementation Summary

### 4.1 VLAN Configuration
VLANs were created on all switches and assigned to appropriate access ports based on department structure.

### 4.2 Inter-VLAN Routing
Router-on-a-Stick configuration was used on Router R1 with subinterfaces configured using IEEE 802.1Q encapsulation.

### 4.3 DHCP Implementation
A centralized DHCP server was configured to assign IP addresses dynamically to all devices in each VLAN.

### 4.4 DHCP Relay
The ip helper-address command was configured on router subinterfaces to forward DHCP requests to the server in VLAN 50.

### 4.5 ACL Security
Access Control Lists were implemented on the router to restrict communication between VLANs based on predefined security policies.

## 5. Testing and Verification

The following tests were performed to validate network functionality:

- DHCP IP assignment verified on all end devices
- Inter-VLAN communication tested using ICMP ping
- ACL rules verified by testing allowed and blocked traffic
- Router and switch configurations validated using show commands

All tests confirmed that the network operates as intended.

## 6. Key Findings

- VLAN segmentation improves network isolation and security
- Router-on-a-Stick is effective for small to medium enterprise networks
- DHCP centralization simplifies IP management
- ACLs provide basic but effective traffic control between departments

## 7. Conclusion

This project successfully demonstrates a functional enterprise network design using Cisco Packet Tracer. It integrates multiple networking concepts into a single scalable architecture and reflects real-world enterprise networking practices.

## 8. Future Improvements

- Implementation of dynamic routing protocols (OSPF/EIGRP)
- Addition of redundancy using STP optimization
- Deployment of network monitoring tools (SNMP/Syslog)
- Integration of firewall-based security policies