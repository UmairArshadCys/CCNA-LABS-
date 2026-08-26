## Overview

Configured IPv6 routing using **SLAAC** for PCs and **static routes** between routers. A floating static route was added as a backup path using a higher administrative distance.

## Configurations

```cisco
! Enable IPv6 routing
ipv6 unicast-routing

! Primary route
ipv6 route 2001:db8:0:3::/64 2001:db8:0:13::2

! Backup/floating route
ipv6 route 2001:db8:0:3::/64 s0/0/0 200

! R3 routes
ipv6 route 2001:db8:0:1::/64 2001:db8:0:13::1
ipv6 route 2001:db8:0:1::/64 s0/0/0 200

! R2 routes
ipv6 route 2001:db8:0:1::/64 s0/0/0
ipv6 route 2001:db8:0:3::/64 s0/0/1
```
