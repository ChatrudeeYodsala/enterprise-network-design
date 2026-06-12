# Enterprise Network Design

## Project Overview

This project demonstrates the design and implementation of an enterprise network using Cisco Packet Tracer. The network is designed with multiple departments, VLAN segmentation, inter-VLAN routing, DHCP services, and access control policies.

## Objectives

* Design an enterprise network topology
* Implement VLAN segmentation
* Configure inter-VLAN routing
* Deploy DHCP services
* Apply network security using ACLs
* Validate connectivity and security policies

## Network Topology

* 1 Cisco 2911 Router
* 3 Cisco 2960 Switches
* 4 Department PCs
* 1 Enterprise Server

## VLAN Plan

| VLAN | Department | Network         |
| ---- | ---------- | --------------- |
| 10   | Management | 192.168.10.0/24 |
| 20   | HR         | 192.168.20.0/24 |
| 30   | IT         | 192.168.30.0/24 |
| 40   | Sales      | 192.168.40.0/24 |
| 50   | Server     | 192.168.50.0/24 |

## Current Features

* Enterprise network topology design
* VLAN segmentation
* Access port configuration
* Trunk link configuration between switches

