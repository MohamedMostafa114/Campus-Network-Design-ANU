# Campus Network Design – ANU

![Project Banner](assets/anu-network-banner.png)

## Overview
This project presents the **LAN network design** and **IP addressing plan** for multiple buildings in a campus environment.  
It includes topology diagrams, subnetting calculations, NAT configuration, and OSPF dynamic routing setup.

The network was designed and implemented as part of a **Computer Networks** course project at **Alexandria National University (ANU)**.

---

## Authors
- **Mohamed Mostafa** – ID: 2205051
- **Mahmoud Amir** – ID: 2205148
- **Abd Al-Rahman Mohamed** – ID: 2205078

---

## Features
- Multiple LAN topologies:
  - Bus topology (3 switches)
  - Ring topology (5 switches)
  - Tree topology (5 switches)
  - Star topology (2 switches)
- Detailed subnetting for each building:
  - Building A: `193.168.1.0/24`
  - Building B: `193.168.2.0/26`
  - Building C: `193.168.2.64/26`
  - Building D: `193.168.2.128/25`
- **NAT Overload / Port Address Translation (PAT)** configuration
- **Dynamic Routing** using OSPF with router IDs and area assignments

---

## Network Components
- **Switches** and **Routers** configured with:
  - IP addresses
  - Subnet masks
  - Default gateways
  - Broadcast and usable host addresses
- **Routing Protocol**: OSPF (Open Shortest Path First)
- **Address Translation**: NAT Overload (PAT) to map internal addresses to a single global address with unique ports

---

## Subnetting Summary
| Building   | Network IP      | Subnet Mask       | DG IP         | Host Range                  | Broadcast IP      |
|------------|-----------------|------------------|--------------|----------------------------|-------------------|
| A          | 193.168.1.0     | 255.255.255.0    | 193.168.1.1  | 193.168.1.2 – 193.168.1.254 | 193.168.1.255     |
| B          | 193.168.2.0     | 255.255.255.192  | 193.168.2.1  | 193.168.2.2 – 193.168.2.62  | 193.168.2.63      |
| C          | 193.168.2.64    | 255.255.255.192  | 193.168.2.65 | 193.168.2.66 – 193.168.2.126| 193.168.2.127     |
| D          | 193.168.2.128   | 255.255.255.128  | 193.168.2.129| 193.168.2.130 – 193.168.2.254| 193.168.2.255    |

---

## Routing Configuration (OSPF Examples)

### Building A
```bash
en
conf t
router ospf 1
router-id 1.1.1.1
network 193.168.1.0 0.0.0.255 area 1
network 10.0.0.0 0.255.255.255 area 0
network 30.0.0.0 0.255.255.255 area 0
