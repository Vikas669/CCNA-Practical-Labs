# Numbered Standard ACL Lab

## Objective
Configure a Numbered Standard Access Control List (ACL) to block a specific host from accessing another network.

---

## Devices Used
- 2 Routers
- 2 Switches
- 2 PCs
- 1 Server

---

# Network Topology

| Device | Interface | IP Address |
|--------|------------|-------------|
| Router0 | Fa0/0 | 1.1.1.1 |
| Router0 | Fa0/1 | 192.168.1.1 |
| Router1 | Fa0/0 | 1.1.1.2 |
| Router1 | Fa0/1 | 192.168.2.1 |
| PC0 | Fa0 | 192.168.1.2 |
| PC1 | Fa0 | 192.168.1.3 |
| Server | Fa0 | 192.168.2.2 |

---

# Router0 Configuration

```bash
enable
configure terminal

interface FastEthernet0/0
ip address 1.1.1.1 255.0.0.0
no shutdown

interface FastEthernet0/1
ip address 192.168.1.1 255.255.255.0
no shutdown

router rip
version 2
no auto-summary

network 1.1.1.0
network 192.168.1.0
```

---

# Router1 Configuration

```bash
enable
configure terminal

interface FastEthernet0/0
ip address 1.1.1.2 255.0.0.0
no shutdown

interface FastEthernet0/1
ip address 192.168.2.1 255.255.255.0
no shutdown

router rip
version 2
no auto-summary

network 1.1.1.0
network 192.168.2.0
```

---

# Standard Numbered ACL Configuration

## Block Host 192.168.1.2

```bash
access-list 10 deny host 192.168.1.2
access-list 10 permit any
```

---

# Apply ACL on Interface

```bash
interface FastEthernet0/0
ip access-group 10 in
```

---

# Verification Commands

```bash
show access-lists
show running-config
show ip route
```

---

# Verification Output

```bash
Router#show access-lists

Standard IP access list 10
    10 deny host 192.168.1.2
    20 permit any
```

---

# Connectivity Test

## Blocked Host

```bash
PC0> ping 192.168.2.2
```

❌ Request timed out

---

## Allowed Host

```bash
PC1> ping 192.168.2.2
```

✅ Successful replies

---

# Features
- Numbered Standard ACL
- Source Host Filtering
- Inbound ACL
- Traffic Control
- Basic Network Security

---

# Result
Successfully configured a Numbered Standard ACL to block traffic from host 192.168.1.2 while allowing all other traffic.
