# VLAN Lab

## Objective
Configure VLANs on Cisco switch and assign ports to different VLANs.

---

## Devices Used
- 1 Cisco Switch
- 6 PCs

---

## VLAN Configuration

| VLAN ID | Name  |
|---------|-------|
| 10      | IT    |
| 20      | SALES |
| 30      | HR    |

---

## Port Assignment

| Interface | VLAN |
|-----------|------|
| Fa0/1     | 10   |
| Fa0/2     | 10   |
| Fa0/3     | 20   |
| Fa0/4     | 20   |
| Fa0/5     | 30   |
| Fa0/6     | 30   |

---

## Commands Used

```bash
enable
configure terminal

vlan 10
name IT

vlan 20
name SALES

vlan 30
name HR
```

### Interface Configuration

```bash
interface FastEthernet0/1
switchport mode access
switchport access vlan 10
no shutdown

interface FastEthernet0/2
switchport mode access
switchport access vlan 10
no shutdown

interface FastEthernet0/3
switchport mode access
switchport access vlan 20
no shutdown

interface FastEthernet0/4
switchport mode access
switchport access vlan 20
no shutdown

interface FastEthernet0/5
switchport mode access
switchport access vlan 30
no shutdown

interface FastEthernet0/6
switchport mode access
switchport access vlan 30
no shutdown
```

---

## Verification Commands

```bash
show vlan brief
```

---

## PC IP Configuration

| PC  | IP Address     | Subnet Mask     | VLAN |
|-----|----------------|----------------|------|
| PC1 | 192.168.10.1  | 255.255.255.0  | 10   |
| PC2 | 192.168.10.2  | 255.255.255.0  | 10   |
| PC3 | 192.168.20.1  | 255.255.255.0  | 20   |
| PC4 | 192.168.20.2  | 255.255.255.0  | 20   |
| PC5 | 192.168.30.1  | 255.255.255.0  | 30   |
| PC6 | 192.168.30.2  | 255.255.255.0  | 30   |

## Result
Successfully created VLANs and assigned switch ports to respective VLANs.
