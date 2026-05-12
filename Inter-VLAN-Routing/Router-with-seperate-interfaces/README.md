
# Inter-VLAN Routing using Separate Router Interfaces

## Objective

Configure Inter-VLAN Routing using separate physical router interfaces.

---

# Topology

* 1 Router
* 1 Switch
* 4 PCs

---

# VLAN Configuration

| VLAN ID | Name  |
| ------- | ----- |
| 10      | IT    |
| 20      | SALES |

---

# IP Addressing

| Device | IP Address   | Default Gateway |
| ------ | ------------ | --------------- |
| PC1    | 192.168.10.2 | 192.168.10.1    |
| PC2    | 192.168.10.3 | 192.168.10.1    |
| PC3    | 192.168.20.2 | 192.168.20.1    |
| PC4    | 192.168.20.3 | 192.168.20.1    |

---

# Router Configuration

```bash
enable
configure terminal

interface GigabitEthernet0/0
ip address 192.168.20.1 255.255.255.0
no shutdown

interface GigabitEthernet0/1
ip address 192.168.10.1 255.255.255.0
no shutdown
```

---

# Switch VLAN Configuration

```bash
enable
configure terminal

vlan 10
name IT

vlan 20
name SALES
```

---

# Switch Port Configuration

## VLAN 10 Ports

```bash
interface FastEthernet0/1
switchport mode access
switchport access vlan 10

interface FastEthernet0/2
switchport mode access
switchport access vlan 10

interface FastEthernet0/3
switchport mode access
switchport access vlan 10
```

## VLAN 20 Ports

```bash
interface FastEthernet0/4
switchport mode access
switchport access vlan 20

interface FastEthernet0/5
switchport mode access
switchport access vlan 20

interface FastEthernet0/6
switchport mode access
switchport access vlan 20
```

---

# Verification Commands

## Router Verification Output

```bash
Router#show ip interface brief

Interface              IP-Address      OK? Method Status                Protocol
GigabitEthernet0/0     192.168.20.1    YES manual up                    up
GigabitEthernet0/1     192.168.10.1    YES manual up                    up
GigabitEthernet0/2     unassigned      YES unset  administratively down down
Vlan1                  unassigned      YES unset  administratively down down
```

## Switch Verification Output

```bash
Switch#show vlan brief

VLAN Name                             Status    Ports
---- -------------------------------- --------- -------------------------------
1    default                          active    Fa0/7, Fa0/8, Fa0/9, Fa0/10
                                                Fa0/11, Fa0/12, Fa0/13, Fa0/14
                                                Fa0/15, Fa0/16, Fa0/17, Fa0/18
                                                Fa0/19, Fa0/20, Fa0/21, Fa0/22
                                                Fa0/23, Fa0/24, Gig0/1, Gig0/2

10   IT                               active    Fa0/2, Fa0/3, Fa0/6

20   SALES                            active    Fa0/1, Fa0/4, Fa0/5
```

# Features

* Separate physical router interfaces
* VLAN communication
* Basic Inter-VLAN routing
* Layer 3 packet forwarding

---

# Result

Successfully enabled communication between VLAN 10 and VLAN 20 using separate router interfaces.

---

# Author

Vikas Kumar
