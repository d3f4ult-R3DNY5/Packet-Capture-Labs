# CCNA mega Lab 1 
---
This lab was built as a part of my learning process and progress towards my CCNA journey with the resources learnt from **Jeremy IT Lab CCNA v1 (200-301) Videos Day 1 -Day24**

## Scenario 
Two branch offices of a WAN are connecting and communicating with each other i.e. (Branch 1 and Branch 2)
- (Main) Branch 1 : Hosts the *IT, Maintenance, Sales* Team 
- (Clients) Branch 2 : Hosts the *Clients 1 , Clients 2*

#### Assumption
The main provides services to the two clients in a B2B connectivity, hosting X services for the clients. All of the devices connecting in a network can communicate with each other.

---

## Network Diagrams

###  Connections and interfaces diagram
![](LAYER2-Conn.drawio.png)

#### Link Legend

| Color                                                        | Hex     | Link Type        | VLANs Carried | Description                          |
| ------------------------------------------------------------ | ------- | ---------------- | ------------- | ------------------------------------ |
| ![#FF9933](https://via.placeholder.com/15/FF9933/FF9933.png) | #FF9933 | Trunk            | 10, 20        | IT & MNTC VLANs — DS1/DS2 to AS1/AS2 |
| ![#97D077](https://via.placeholder.com/15/97D077/97D077.png) | #97D077 | Trunk            | 20, 30        | DEV & MNTC VLANs — DS1/DS2 to AS2    |
| ![#FF0000](https://via.placeholder.com/15/FF0000/FF0000.png) | #FF0000 | Trunk            | 10, 20, 30    | All VLANs — CS1 to DS1/DS2           |
| ![#000000](https://via.placeholder.com/15/000000/000000.png) | #000000 | EtherChannel     | -             | CS1 to IMR1 uplink                   |
| ![#0000FF](https://via.placeholder.com/15/0000FF/0000FF.png) | #0000FF | EtherChannel WAN | -             | IMR1 to IMR2 inter-site link         |
| ![#00FFFF](https://via.placeholder.com/15/00FFFF/00FFFF.png) | #00FFFF | Trunk            | 40, 50        | CLIENT1 & CLIENT2 — right branch     |





