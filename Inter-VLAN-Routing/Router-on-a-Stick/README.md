
# Router-on-a-Stick Lab

## Objective
Configure Inter-VLAN Routing using the Router-on-a-Stick method.

---

## Topology
- 1 Router
- 1 Switch
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
interface fa0/2
switchport mode access
switchport access vlan 10

interface fa0/3
switchport mode access
switchport access vlan 10

interface fa0/4
switchport mode access
switchport access vlan 20

interface fa0/5
switchport mode access
switchport access vlan 20
```

---

## Trunk Port Configuration

```bash
interface fa0/1
switchport mode trunk
no shutdown
```

---

# Router Configuration

```bash
enable
configure terminal

interface gig0/0
no shutdown

interface gig0/0.10
encapsulation dot1Q 10
ip address 192.168.10.1 255.255.255.0

interface gig0/0.20
encapsulation dot1Q 20
ip address 192.168.20.1 255.255.255.0
```

---

## Verification Commands

```bash
show vlan brief
show interfaces trunk
show ip interface brief
```

## Switch Verification

```bash
Switch>enable
Switch#show vlan brief

VLAN Name                             Status    Ports
---- -------------------------------- --------- -------------------------------
1    default                          active    Fa0/6, Fa0/7, Fa0/8
10   IT                               active    Fa0/2, Fa0/3
20   SALES                            active    Fa0/4, Fa0/5
```
## Router Verification

```bash
Router>enable
Router#show ip interface brief

Interface              IP-Address      OK? Method Status                Protocol
GigabitEthernet0/0     unassigned      YES unset  up                    up
GigabitEthernet0/0.10  192.168.10.1    YES manual up                    up
GigabitEthernet0/0.20  192.168.20.1    YES manual up                    up
GigabitEthernet0/1     unassigned      YES unset  administratively down down
GigabitEthernet0/2     unassigned      YES unset  administratively down down
Vlan1                  unassigned      YES unset  administratively down down
```
## Trunk Verification

```bash
Switch#show interfaces trunk

Port        Mode         Encapsulation  Status        Native vlan
Fa0/1       desirable    n-802.1q       trunking      1

Port        Vlans allowed on trunk
Fa0/1       1-1005

Port        Vlans allowed and active in management domain
Fa0/1       1,10,20

Port        Vlans in spanning tree forwarding state and not pruned
Fa0/1       1,10,20
```
---

## Features
- Inter-VLAN Routing
- VLAN Trunking
- Router Subinterfaces
- Dot1Q Encapsulation

---

## Result
Successfully enabled communication between VLAN 10 and VLAN 20 using Router-on-a-Stick configuration.
