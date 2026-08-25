## Overview

Configured IPv6 addressing using EUI-64, IPv6 link-local addresses, and static routing between two networks.

## Configurations

```cisco
ipv6 unicast-routing

interface g0/1
 ipv6 address 2001:db8::/64 eui-64
 no shutdown

interface g0/0
 ipv6 enable
 no shutdown

ipv6 route 2001:db8:0:1::/64 g0/0 <R2-link-local>
```

```cisco
interface g0/1
 ipv6 address 2001:db8:0:1::/64 eui-64
 no shutdown

interface g0/0
 ipv6 enable
 no shutdown

ipv6 route 2001:db8::/64 g0/0 <R1-link-local>
```
