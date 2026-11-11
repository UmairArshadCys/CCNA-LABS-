# OSPF Multi-Router Configuration

Configured OSPF (Open Shortest Path First) across four routers (R1, R2, R3, and R4) within Area 0. Implemented loopback interfaces, passive interfaces, reference bandwidth, and default route advertisement using R1 as an ASBR.

## Configurations

**OSPF Configuration (R1, R2, R3, R4)**
```cisco
router ospf 1
router-id X.X.X.X
auto-cost reference-bandwidth 10000
```

**Enable OSPF on Interfaces**
```cisco
interface g0/0
ip ospf 1 area 0
```

**Loopback Interfaces**
```cisco
interface loopback 0
ip address X.X.X.X 255.255.255.255
ip ospf 1 area 0
```

**Passive Interface (R4)**
```cisco
router ospf 1
passive-interface g0/0
```

**Default Route Advertisement (R1)**
```cisco
ip route 0.0.0.0 0.0.0.0 203.0.113.2

router ospf 1
default-information originate
```

**Verification Commands**
```cisco
show ip ospf neighbor
show ip route
show ip route ospf
show ip ospf database
```
