# OSPF Multi-Router Network with Default Route Propagation

## Overview

This lab demonstrates the configuration of **OSPF Area 0** across a multi-router network. Loopback interfaces are used as stable OSPF router IDs, and R1 is configured as an **ASBR** to advertise the Internet-facing default route into the OSPF domain.

## Key Configuration

### OSPF Configuration on R1

```cisco
router ospf 1
 router-id 1.1.1.1
 log-adjacency-changes
 auto-cost reference-bandwidth 10000
 network 1.1.1.1 0.0.0.0 area 0
 network 10.0.12.0 0.0.0.3 area 0
 network 10.0.13.0 0.0.0.3 area 0
 default-information originate
