# Router-on-a-stick 

## Overview

This project demonstrates the design and implementation of a segmented enterprise LAN using Cisco Packet Tracer. The network uses multiple VLANs to separate departmental traffic while allowing controlled communication between VLANs through Router-on-a-Stick inter-VLAN routing.

The lab also demonstrates 802.1Q trunking, multi-switch VLAN extension, DHCP, DNS, ACL configuration, IP addressing, and network connectivity verification.

## Objectives.

The objectives of this lab were to:

- Design a segmented LAN using VLANs
  
- Create and configure multiple VLANs
  
- Assign switch ports to appropriate VLANs
  
- Configure 802.1Q trunk links
  
- Extend VLANs across multiple switches
  
- Configure Router-on-a-Stick inter-VLAN routing
  
- Configure IP addressing and default gateways
  
- Configure DHCP services
  
- Configure DNS services
  
- Implement ACLs for traffic control
  
- Verify connectivity between hosts and VLANs
  
- Troubleshoot Layer 2 and Layer 3 connectivity issues

## Network Topology

-The network consists of:

-1 Router

-2 Access Switches 

-Multiple PCs and Laptops 

-A DHCP/DNS SERVER 

-Four VLANs 

-Trunk links between network devices.

![Network Topology](https://github.com/hollynofiu-collab/Router-On-a-Stick-Lab/tree/main/Screenshots)

## VLAN Design

| VLAN | Department | Network | Default Gateway |
|-----:|------------|---------|-----------------|
| 10 | Production / COO | 192.168.10.0/24 | 192.168.10.1 |
| 20 | HR / Finance | 192.168.20.0/24 | 192.168.20.1 |
| 30 |Staff / Access| 192.168.30.0/24 | 192.168.30.1 |
| 40 | IT / Servers Farm| 192.168.40.0/24 | 192.168.40.1

The VLANs provide logical segmentation of the network and create separate broadcast domains.

# 1. VLAN Configuration

The first step was to create the required VLANs on the switches.

Example:

vlan 10
name Production

vlan 20
name HR


The VLANs were created on both access switches so that the same VLANs could be extended across the network.

![Vlan config on switch 1](https://github.com/hollynofiu-collab/Router-On-a-Stick-Lab/tree/main/Screenshots)


# 2. Access Port Configuration.

End devices were assigned to their appropriate VLANs using access ports.

Example:

interface range fastEthernet0/1-3
switchport mode access
switchport access vlan 10

Additional ports were assigned to VLANs 20, 30, and 40 according to the network design. This ensured that devices connected to an access port belonged to the correct departmental VLAN.

![Access Port config](https://github.com/hollynofiu-collab/Router-On-a-Stick-Lab/tree/main/Screenshots)


## 3. Trunk Configuration

The link between the switch and router was configured as an 802.1Q trunk.

Example:

interface gigabitEthernet0/1
switchport mode trunk
switchport trunk allowed vlan 10,20,30,40

The trunk carries traffic for multiple VLANs over a single physical connection.

A second trunk was configured between the access switches to extend VLANs across the network.

![Trunk config/verification](https://github.com/hollynofiu-collab/Router-On-a-Stick-Lab/tree/main/Screenshots)

## 4. Router-on-a-Stick Configuration

Router-on-a-Stick was used to provide inter-VLAN routing.

Instead of requiring a separate physical router interface for every VLAN, multiple logical subinterfaces were created on a single physical router interface.

Example:

interface fastEthernet0/0.10
encapsulation dot1Q 10
ip address 192.168.10.1 255.255.255.0

The Router interface was verified and verification confirmed that the VLAN Subinterfaces were operational and in an up/up state.

![Router interface verification](https://github.com/hollynofiu-collab/Router-On-a-Stick-Lab/tree/main/Screenshots)

Connectivity was tested by pinging different IPs in different Vlans. 

E.g:
PC1 ping 192.168.30.2

Successful replies confirmed inter-VLAN routing.

![Connectivity Tests](https://github.com/hollynofiu-collab/Router-On-a-Stick-Lab/tree/main/Screenshots)













