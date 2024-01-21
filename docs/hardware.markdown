---
layout: default
title: Hardware
permalink: /hardware/
---


**Table of Contents**

* TOC
{:toc}

# Hardware

## Modem

### ISP DSL Modem

This is just a stock standard ISP supplied DSL NBN Modem Router.

General Config Notes:
- External Address: Dynamic / assigned by ISP
- Internal Address: Static 192.168.x.1
- Port Forwarding rules are defined to forward VPN traffic
  
  | Description  | LAN Address        | Protocol | LAN Port      | External Port |
  | -------------| ------------------ | -------- | ------------- | ------------- |
  | VPN Server 1 | (Mesh Gateways IP) | UDP      | N<sub>1<sub>  | N<sub>1<sub>  |
  | VPN Server 2 | (Mesh Gateways IP) | UDP      | N<sub>2<sub>  | N<sub>2<sub>  |

- DMZ not enabled.
- Secure DNS disabled, to allow use of custom DNS Servers
- Wifi disabled , to prevent conflicts with Mesh Wifi
- Has DHCP enabled on Subnet 192.168.x.0/24 ( addresses x.2 -> x.8 )
  - There is just one static IP defined for the primary Wifi Mesh Gateway Node.
- IPv6 is disabled

## Wifi Mesh

The gateway node connects directly to the ISP supplied via 100 MBit Ethernet.

General Config Notes:
- External Address: Dynamic ( but is statically set on modem) as 192.168.x.2
- Internal Address: Static 192.168.y.1/22
- Port Forwarding rules are defined to forward VPN traffic

  | Description  | LAN Address        | Protocol | LAN Port      | External Port |
  | -------------| ------------------ | -------- | ------------- | ------------- |
  | VPN Server 1 | 192.168.y.2        | UDP      | N<sub>1<sub>  | N<sub>1<sub>  |
  | VPN Server 2 | 192.168.y.3        | UDP      | N<sub>2<sub>  | N<sub>2<sub>  |

## Hypervisors

In the ozlan labs there are multiple systems acting as Hypervisors.

### Dell OptiPlex 7040 SFF
 - Role(s):
   -  Dev / Test of VMs / Containers 
 - CPU: Intel i5 6500 3.2 GHz 
 - RAM: 64 GB 
 - Storage: 
   - 2x 1 TB NVMe PCIe SSD 
 - Network: 1 Gbit Ethernet
 - IP: 192.168.y.4

![Dell Optiplex 7040](./assets/images/hardware/dell-7040.jpg)

### Dell OptiPlex 7060 Micro
 - Role(s):
   -  Production VMs / Containers
 - CPU: Intel i5 8500T 2.1 Ghz
 - RAM: 48 GB 
 - Storage: 
   - 1x 1 TB NVMe PCIe SSD
   - 1x 1 TB Sata SSD
 - Network: 1 Gbit Ethernet
 - IP: 192.168.y.10

![Dell Optiplex 7060](./assets/images/hardware/dell-optiplex-7060.jpg)

### HP EliteDesk 800 G5 
 - Role(s): 
   - Production VMs / Containers
 - CPU: Intel i5 9500T 2.2 Ghz
 - RAM: 64 GB
 - Storage: 
   - 1x 1 TB NVMe PCIe SSD
   - 1x 1 TB Sata SSD
 - Network: 1 Gbit Ethernet
 - IP: 192.168.y.11

![Hp EliteDesk 800 G5](./assets/images/hardware/hp-g5.jpg)


## Standalone Servers

Several Single board ARM64 computers are used as dedicated servers.

### Server #1
- Role(s):
  - VPN Server 
  - Ad blocking DNS Server
  - Dynamic DNS Client 
  - and more (to be confirmed [TODO](/todo) )
- Hardware: Raspberry Pi 4 8GB
- Storage: 
  - 1x 128 GB Micro SD
- Network: 1 Gbit Ethernet
 - IP: 192.168.y.?

### Server #2
- Role(s): 
  - VPN Server
  - Ad blocking DNS Server
  - and more (to be confirmed [TODO](/todo) )
- Hardware: Raspberry Pi 4 8GB
- Storage: 
  - 1x 128 GB Micro SD
- Network: 1 Gbit Ethernet
 - IP: 192.168.y.?

### Server #3
- Role(s):
  - Network PVR / TV recorder
  - and more (to be confirmed [TODO](/todo) ) 
- Hardware: Raspberry Pi 4 8GB
- Storage: 
  - 1x 128 GB Micro SD
- Network: 1 Gbit Ethernet
 - IP: 192.168.y.?
