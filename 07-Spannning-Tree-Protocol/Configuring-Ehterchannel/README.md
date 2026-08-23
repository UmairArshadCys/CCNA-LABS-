Absolutely. Since you completed all 6 tasks, here is a clean GitHub README with **only the two headings** you wanted: **Overview** and **Configuration**.

# Overview

This lab demonstrates EtherChannel configuration using LACP, PAgP, and static EtherChannel. Layer 2 EtherChannels are configured as trunks between access and distribution switches, while a Layer 3 EtherChannel is configured between the distribution switches. Static routing is then configured to provide connectivity between the PC and server networks. Finally, EtherChannel load balancing is configured using source and destination IP addresses.

# Configuration

## Task 1 — Layer 2 EtherChannel Between ASW1 and DSW1 Using LACP

### ASW1

```cisco
enable
configure terminal

interface range gigabitEthernet 0/1-2
 channel-group 1 mode active
exit

interface port-channel 1
 switchport mode trunk
exit
```

### DSW1

```cisco
enable
configure terminal

interface range gigabitEthernet 1/0/3-4
 channel-group 1 mode active
exit

interface port-channel 1
 switchport mode trunk
exit
```

## Task 2 — Layer 2 EtherChannel Between ASW2 and DSW2 Using PAgP

### ASW2

```cisco
enable
configure terminal

interface range gigabitEthernet 0/1-2
 channel-group 2 mode desirable
exit

interface port-channel 2
 switchport mode trunk
exit
```

### DSW2

```cisco
enable
configure terminal

interface range gigabitEthernet 1/0/3-4
 channel-group 2 mode desirable
exit

interface port-channel 2
 switchport mode trunk
exit
```

## Task 3 — Layer 3 EtherChannel Between DSW1 and DSW2 Using Static EtherChannel

### DSW1

```cisco
enable
configure terminal

ip routing

interface range gigabitEthernet 1/0/1-2
 no switchport
 channel-group 3 mode on
exit

interface port-channel 3
 no switchport
 ip address 10.0.0.1 255.255.255.252
 no shutdown
exit
```

### DSW2

```cisco
enable
configure terminal

ip routing

interface range gigabitEthernet 1/0/1-2
 no switchport
 channel-group 3 mode on
exit

interface port-channel 3
 no switchport
 ip address 10.0.0.2 255.255.255.252
 no shutdown
exit
```

## Task 4 — Configure Routes to Allow PCs to Reach SRV1

### DSW1

```cisco
ip route 172.16.2.0 255.255.255.0 10.0.0.2
```

### DSW2

```cisco
ip route 172.16.1.0 255.255.255.0 10.0.0.1
```

### Verification

```cisco
show ip route
show ip interface brief
ping 10.0.0.2
```

On DSW2:

```cisco
show ip route
show ip interface brief
ping 10.0.0.1
```

## Task 5 — Check the Default EtherChannel Load-Balancing Method

```cisco
show etherchannel load-balance
```

The default load-balancing method on the switches is based on the source MAC address (`src-mac`).

## Task 6 — Configure Load Balancing Using Source and Destination IP Addresses

### DSW1

```cisco
configure terminal
port-channel load-balance src-dst-ip
exit
```

### DSW2

```cisco
configure terminal
port-channel load-balance src-dst-ip
exit
```

### Verification

```cisco
show etherchannel load-balance
```

Expected result:

```text
EtherChannel Load-Balancing Configuration:
        src-dst-ip
```

### EtherChannel Verification Commands

```cisco
show etherchannel summary
show etherchannel load-balance
show interfaces port-channel 1
show interfaces port-channel 2
show interfaces port-channel 3
show ip route
```
