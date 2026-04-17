# CCNA Mega Lab 1

> This lab was built as part of my learning process and progress  towards my CCNA journey with the resources learnt from Jeremy IT  Lab CCNA v1 (200-301) Videos Day 1 - Day 24

---

## Scenario
Two branch offices of a WAN are connecting and communicating with each other i.e. (Branch 1 and Branch 2)

- **(Main) Branch 1** — Hosts the IT, Maintenance, Development Team
- **(Clients) Branch 2** — Hosts the Clients 1, Clients 2

## Assumption
The main provides services to the two clients in a B2B  connectivity, hosting X services for the clients. All of the  devices connecting in a network can communicate with each other.

---
## Network Diagrams

### Connections and Interfaces (Layer 2)

<p align="center">
  <img src="LAYER2-LAYER3-LAB1.drawio.svg" />
</p>

### IP Addressing (Layer 3)

<p align="center">
  <img src="IP DIAGRAM.drawio.svg" />
</p>

---

## Abbreviations

| Abbreviation | Full Name                  |
| ------------ | -------------------------- |
| ER1          | Edge Router 1              |
| IMR1         | Internal Main Router 1     |
| IMR2         | Internal Main Router 2     |
| CS1          | Core Switch 1              |
| DS1          | Distribution Switch 1      |
| DS2          | Distribution Switch 2      |
| AS1          | Access Switch 1            |
| CR1          | Client Router 1            |
| NID          | Network ID                 |
| DG           | Default Gateway            |
| SVI          | Switched Virtual Interface |
| VLAN         | Virtual Local Area Network |
| CAN          | Campus Area Network        |
| SI           | Sub Interfaces             |

---

## Configuration Details Overview

The configuration details are given in the following file 
 [Configuration Details](Configuration%20Details.md)

---


## Design Decisions 

### In Internal Network 1

- Partial Mesh in DS1/DS2 and AS1/AS2 for increased redundancy 
- DS1 has been made as the **primary root in the Spanning Tree Protocol in VLAN 10,20,30** so that all the traffic flows through the interfaces from DS1
- DS2 is configured to be **secondary root primary root in the Spanning Tree Protocol in VLAN 10,20,30**
- All the ports connecting to the client Devices have been **configured with portfast so that they can instantly connect to the network and start forwarding the traffic**
	- Since Port fast cannot prevent switches from connecting in the network all the port have been configured with BPDU guard to **prevent from connecting the switch**
	- Root guard has been configured on DS1 and DS2 downlinks to **prevent any of the access switches from becoming the root** 
	- Loop guard has been configured on the Distribution Switches uplinks to protect **against the unidirectional link failures**

### In internal network 2
- All the ports connecting to the client Devices have been **configured with portfast so that they can instantly connect to the network and start forwarding the traffic**
	- Since Port fast cannot prevent switches from connecting in the network all the port have been configured with BPDU guard to **prevent from connecting the switch**
- AS3 and AS4 form an ether channel using 4 interfaces
- AS4 has been configured as a trunk port to CR1 and AS3
- CR1 has been configured with Router on a stick to perform inter VLAN routing


## External Network 
- Routers CR1 and CR2 are used to perform routing between the internal networks and also routing the addresses outside the networks 

---


