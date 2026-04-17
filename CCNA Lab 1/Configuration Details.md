# Configuration Details 
---
## VLAN Table

| VLAN ID | Name | Subnet | Branch | Switch |
|---------|------|--------|--------|--------|
| 10 | IT | 192.168.1.160/28 | Left | AS1 |
| 20 | MNTC | 192.168.1.128/27 | Left | AS1, AS2 |
| 30 | DEV | 192.168.1.0/25 | Left | AS2 |
| 40 | CLIENT1 | 192.168.2.0/25 | Right | AS3 |
| 50 | CLIENT2 | 192.168.2.128/25 | Right | AS3, AS4 |
## STP Configuration Table

| Device | Mode | Role | VLANs | Priority |
|--------|------|------|-------|----------|
| DS1 | Rapid-PVST | Root Primary | 10, 20, 30 | 24576 |
| DS2 | Rapid-PVST | Root Secondary | 10, 20, 30 | 28672 |
| AS1 | Rapid-PVST | Non-Root | 10, 20 | Default |
| AS2 | Rapid-PVST | Non-Root | 20, 30 | Default |
| CS1 | Rapid-PVST | Non-Root | 10, 20, 30 | Default |

## STP Port Configuration

| Device | Port        | VLAN       | Mode           | Feature               |
| ------ | ----------- | ---------- | -------------- | --------------------- |
| DS1    | All uplinks | 10, 20, 30 | Designated FWD | Root Primary          |
| DS2    | Fa0/1       | 10, 20, 30 | Alternate BLK  | Failover only         |
| DS2    | Fa0/2       | 10, 20, 30 | Root FWD       | Root port             |
| AS1    | Host ports  | 10, 20     | Access         | PortFast + BPDU Guard |
| AS2    | Host ports  | 20, 30     | Access         | PortFast + BPDU Guard |

## Link Legend

| Color                                                    | Hex     | Link Type        | VLANs      | Description                    |
| -------------------------------------------------------- | ------- | ---------------- | ---------- | ------------------------------ |
| ![#FF9933](https://placehold.co/15x15/FF9933/FF9933.png) | #FF9933 | Trunk            | 10, 20     | IT & MNTC — DS1/DS2 to AS1/AS2 |
| ![#97D077](https://placehold.co/15x15/97D077/97D077.png) | #97D077 | Trunk            | 20, 30     | DEV & MNTC — DS1/DS2 to AS2    |
| ![#FF0000](https://placehold.co/15x15/FF0000/FF0000.png) | #FF0000 | Trunk            | 10, 20, 30 | All VLANs — CS1 to DS1/DS2     |
| ![#000000](https://placehold.co/15x15/000000/000000.png) | #000000 | EtherChannel     | -          | CS1 to IMR1 uplink             |
| ![#0000FF](https://placehold.co/15x15/0000FF/0000FF.png) | #0000FF | EtherChannel WAN | -          | IMR1 to IMR2 inter-site link   |
| ![#00FFFF](https://placehold.co/15x15/00FFFF/00FFFF.png) | #00FFFF | Trunk            | 40, 50     | CLIENT1 & CLIENT2 right branch |
