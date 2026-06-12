## VLAN Configuration

The enterprise network is segmented into five VLANs:

- VLAN 10 – Management  
- VLAN 20 – HR  
- VLAN 30 – IT  
- VLAN 40 – Sales  
- VLAN 50 – Server  

Each VLAN represents a separate broadcast domain to improve security and network efficiency.

## Trunk Links

Trunk links are configured between the core switch and access switches to allow multiple VLAN traffic across the network.

All trunk links use IEEE 802.1Q encapsulation.

- Core-SW1 ↔ Access-SW2  
- Core-SW1 ↔ Access-SW3  

## Access Port Assignment

Each access switch port is assigned to specific VLANs based on department:

- HR → VLAN 20  
- IT → VLAN 30  
- Sales → VLAN 40  
- Management → VLAN 10  
- Server → VLAN 50  