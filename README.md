# Enterprise Network Infrastructure Simulation

## Overview

This project is a simulated enterprise network using the freely avaliable tool Cisco packet tracer, used for simulating networks
The goal of my project was to learn new concepts and sharpen my existing understanding of networking.
The goal of my project was to practice and sharpen my understanding of the following core networking concepts such as VLAN segmentation, subnetting, inter-VLAN routing, DHCP relay, ACLs, and centralized infrastructure services.

The network was designed to simulate a small enterprise environment with multiple departments, centralized servers, and segmented network access.

---

## My Objectives

- Implement VLAN segmentation between departments
- Configure inter-VLAN communication using a Router-on-a-Stick topology
- Configure a centralized server to provide DHCP services to all devices on the network
- Implement DHCP relay using the Cisco CLI command `ip helper-address`
- Configure DNS and Email services
- Apply a core cybersecurity concept such as using ACLs to isolate guest traffic, allowing only the necessary DHCP service to be provided
- Practice subnetting and structured IP addressing
- Simulate the design and configuration of a scalable enterprise-style network

---

## Networking concepts
- Cisco Packet Tracer
- VLANs, as each department in the simulated enterprise has its own VLAN such as the HR and Accounting department belonging to the VLANs: 10 and 60 respectively
- 802.1Q Trunking, as data packets from 2 Vlans can move through a single switch interface
- Router-on-a-Stick, as the topology of this project consists of a router connected to a single switch receiving traffic from multiple networks
- Subnetting, as I have split the network 192.168.18.0/24 into 6 seperate networks by increasing the number of bits in the subnet to 27
- DHCP, as IP addresses, Default gateways, DNS address etc can be assigned automatically
- DHCP Relay, as There is a single DHCP server, belonging to the VLAN dedicated from servers providing DHCP service to devices in seperate LANs. I did this By using the cisco CLI command `ip helper-address` to allow broadcasts requesting an IP address to be routed straight to the DHCP server's IP address
- DNS, A dedicated DNS server is avaliable to all networks except the guest network
- Email Server, I made use of a centralized Email server with the custom hostname: `enterprise.net`
- Wireless Access Points, The guest LAN is made up of 3 wireless access points, all with the same name and password, allowing devices to automatically connect to the closes access point

## Cybersecurity concepts
ACLs (Access Control Lists) were used, The Guest network is not permitted to send traffic out to any other device on any network, except for udp traffic through the the 2 ports, 67 and 68, which are used for DHCP services, no other type of traffic is permitted to flow outside the guest network even udp traffic to a port different from the 2 mentioned before. This minimizes the risk of the Guest network being a potential route for attacks to interfer with the enterprise's network, as the strict criteria I set in the ACL helps prevent attackers from making use of specially crafted data packets such as making a udp data packet be received through a port other then 67 or 68.
- Network Segmentation, Each network is segmented from each other. This reduces unnecessary traffic and most importantly adheres to the cybersecurity concepts of: Least privilage access and reducing the attack surface as devices belonging to the HR department do not need direct access to devices in the accounting department. Segmentation also helps protect the servers in the enterprise as the key server infrastructure is isolated from all other networks, reducing the likelihood of a seperate LAN being compromised resulting in critical infrastructure being affected.

---

## Network Topology

> Insert topology screenshot here

Example:

```text
/images/topology.png
