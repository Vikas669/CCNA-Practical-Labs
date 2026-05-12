
# Layer 3 Switch Inter-VLAN Routing Lab

## Objective
Configure Inter-VLAN Routing using a Layer 3 Switch.

---

## Devices Used
- 1 Layer 3 Switch (3560)
- 4 PCs

---

## VLAN Configuration

| VLAN ID | Name |
|----------|------|
| 10 | IT |
| 20 | SALES |

---

## IP Addressing

| Device | IP Address | Default Gateway | VLAN |
|--------|-------------|----------------|------|
| PC1 | 192.168.10.2 | 192.168.10.1 | 10 |
| PC2 | 192.168.10.3 | 192.168.10.1 | 10 |
| PC3 | 192.168.20.4 | 192.168.20.1 | 20 |
| PC4 | 192.168.20.5 | 192.168.20.1 | 20 |

---

# Switch Configuration

## VLAN Creation

```bash
enable
configure terminal

vlan 10
name IT

vlan 20
name SALES
```

---

## Access Port Configuration

```bash
interface FastEthernet0/1
switchport access vlan 10
no shutdown

interface FastEthernet0/4
switchport access vlan 10
no shutdown

interface FastEthernet0/2
switchport access vlan 20
no shutdown

interface FastEthernet0/3
switchport access vlan 20
no shutdown
```

---

## Enable Routing

```bash
ip routing
```

---

## SVI Configuration

```bash
interface vlan 10
ip address 192.168.10.1 255.255.255.0
no shutdown

interface vlan 20
ip address 192.168.20.1 255.255.255.0
no shutdown
```

---

# Verification Commands

## VLAN Verification

```bash
Switch#show vlan brief
```

---

## Interface Verification

```bash
Switch#show ip interface brief

Interface              IP-Address      OK? Method Status                Protocol
Vlan10                 192.168.10.1    YES manual up                    up
Vlan20                 192.168.20.1    YES manual up                    up
```

---

## Routing Verification

```bash
Switch#show ip route

C    192.168.10.0/24 is directly connected, Vlan10
C    192.168.20.0/24 is directly connected, Vlan20
```

---

## Connectivity Test

```bash
PC> ping 192.168.20.4
```

---

## Features
- Inter-VLAN Routing
- Layer 3 Switching
- SVI Configuration
- Internal Routing
- VLAN Communication

---

## Result
Successfully enabled communication between VLAN 10 and VLAN 20 using a Layer 3 Switch. :contentReference[oaicite:0]{index=0}
