
# Inter-VLAN Routing Labs

## Objective
Configure communication between different VLANs using multiple Inter-VLAN Routing methods.

---

# Methods Included

## 1. Router using Separate Interfaces
Inter-VLAN communication using separate physical router interfaces for each VLAN.

### Features
- Dedicated router interfaces
- Basic Inter-VLAN Routing
- Simple configuration

---

## 2. Router-on-a-Stick
Inter-VLAN Routing using a single router interface with multiple subinterfaces and VLAN trunking.

### Features
- Router Subinterfaces
- Dot1Q Encapsulation
- Trunk Configuration
- Single Physical Link

---

## 3. Layer 3 Switch
Inter-VLAN Routing using SVI (Switched Virtual Interfaces) on a Layer 3 switch.

### Features
- Internal Routing
- SVI Configuration
- Faster Switching and Routing
- No External Router Required

---

# VLANs Used

| VLAN ID | Name |
|----------|------|
| 10 | IT |
| 20 | SALES |

---

# IP Addressing

| VLAN | Network | Gateway |
|------|----------|----------|
| 10 | 192.168.10.0/24 | 192.168.10.1 |
| 20 | 192.168.20.0/24 | 192.168.20.1 |

---

# Comparison of Methods

| Method | Router Required | Trunk Required | Difficulty |
|--------|-----------------|----------------|------------|
| Separate Interfaces | Yes | No | Easy |
| Router-on-a-Stick | Yes | Yes | Medium |
| Layer 3 Switch | No | No | Advanced |

---

# Verification Commands

```bash
show vlan brief
show interfaces trunk
show ip interface brief
show ip route
```

---

# Skills Learned
- VLAN Segmentation
- Inter-VLAN Communication
- Router Subinterfaces
- VLAN Trunking
- SVI Configuration
- Layer 3 Switching
- Network Routing

---

# Repository Structure

```text
Inter-VLAN-Routing/
│
├── Router-Separate-Interfaces/
├── Router-on-a-Stick/
└── Layer3-Switch/
```

---

# Result
Successfully configured Inter-VLAN Routing using all three methods and verified communication between VLANs.
