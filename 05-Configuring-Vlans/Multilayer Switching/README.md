# Overview

Configured **Multilayer Switching** by replacing the Router-on-a-Stick (ROAS) connection between R1 and SW2 with a **Layer 3 point-to-point connection**. Configured SVIs on SW2 for inter-VLAN routing and a default route toward R1, then tested inter-VLAN and Internet connectivity.

# Configuration

### SW2

```bash
enable
configure terminal

ip routing

vlan 10
exit
vlan 20
exit
vlan 30
exit

interface gigabitEthernet 1/0/2
 no switchport
 ip address 10.0.0.193 255.255.255.252
 no shutdown
 exit

interface vlan 10
 ip address 10.0.0.62 255.255.255.192
 no shutdown
 exit

interface vlan 20
 ip address 10.0.0.126 255.255.255.192
 no shutdown
 exit

interface vlan 30
 ip address 10.0.0.190 255.255.255.192
 no shutdown
 exit

ip route 0.0.0.0 0.0.0.0 10.0.0.194

end
write memory
```

### R1

```bash
enable
configure terminal

interface gigabitEthernet 0/0
 no ip address
 no shutdown
 exit

no interface gigabitEthernet 0/0.10
no interface gigabitEthernet 0/0.20
no interface gigabitEthernet 0/0.30

interface gigabitEthernet 0/0
 ip address 10.0.0.194 255.255.255.252
 no shutdown
 exit

end
write memory
```

### Connectivity Tests

```bash
SW2#ping 10.0.0.126 source 10.0.0.62
SW2#ping 10.0.0.190 source 10.0.0.62
SW2#ping 1.1.1.1 source 10.0.0.62
```
