# Inter-VLAN Routing Lab

## Overview

This lab demonstrates **inter-VLAN routing using three separate physical connections between R1 and SW1**. Three VLANs are configured for Engineering, HR, and Sales, with each VLAN using a dedicated physical router interface as its default gateway.

Unlike **Router-on-a-Stick**, this topology does not use router subinterfaces or a trunk link between R1 and SW1.

## Key Configuration

### VLAN Configuration

```cisco
vlan 10
 name Engineering
vlan 20
 name HR
vlan 30
 name Sales
```

### Router Interface Configuration

```cisco
interface GigabitEthernet0/0
 ip address 10.0.0.62 255.255.255.192
 no shutdown

interface GigabitEthernet0/1
 ip address 10.0.0.126 255.255.255.192
 no shutdown

interface GigabitEthernet0/2
 ip address 10.0.0.190 255.255.255.192
 no shutdown
```

### Switch Port Configuration

```cisco
interface GigabitEthernet0/1
 switchport access vlan 10
 switchport mode access

interface GigabitEthernet1/1
 switchport access vlan 20
 switchport mode access

interface GigabitEthernet2/1
 switchport access vlan 30
 switchport mode access
```

### Verification

```cisco
show ip interface brief
show vlan brief
```
