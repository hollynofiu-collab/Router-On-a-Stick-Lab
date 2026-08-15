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

![Network Topology](https://github.com/hollynofiu-collab/Router-On-a-Stick-Lab/blob/main/Screenshots/router%20on%20a%20stick.png)

## VLAN Design

| VLAN | Department | Network | Default Gateway |
|-----:|------------|---------|-----------------|
| 10 | Production / Admin | 192.168.10.0/24 | 192.168.10.1 |
| 20 | Sales / Staff | 192.168.20.0/24 | 192.168.20.1 |
| 30 | HR / IT | 192.168.30.0/24 | 192.168.30.1 |
| 40 | Accounting / Access | 192.168.40.0/24 | 192.168.40.1

The VLANs provide logical segmentation of the network and create separate broadcast domains.

# 1. VLAN Configuration

The first step was to create the required VLANs on the switches.

Example:

vlan 10
name Production

vlan 20
name Sales

vlan 30
name HR

vlan 40
name Admin

The VLANs were created on both access switches so that the same VLANs could be extended across the network.

![Vlan config on switch 1](https://github.com/hollynofiu-collab/Router-On-a-Stick-Lab/blob/main/Screenshots/vlan%20config.png)









