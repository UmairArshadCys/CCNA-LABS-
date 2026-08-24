## Overview

Configured an IPv4/IPv6 dual-stack network by enabling IPv6 routing on R1, assigning IPv6 addresses to the router interfaces and PCs, and verifying connectivity between the PCs.

## Configuration

### R1

```cisco
ipv6 unicast-routing

interface g0/0
 ipv6 address 2001:DB8:0:1::1/64
 no shutdown

interface g0/1
 ipv6 address 2001:DB8:0:2::1/64
 no shutdown

interface g0/2
 ipv6 address 2001:DB8:0:3::1/64
 no shutdown
```

### PCs

```text
PC1: 2001:DB8:0:1::2/64
Gateway: 2001:DB8:0:1::1

PC2: 2001:DB8:0:2::2/64
Gateway: 2001:DB8:0:2::1

PC3: 2001:DB8:0:3::2/64
Gateway: 2001:DB8:0:3::1
```

### Verification

```text
ping 2001:DB8:0:1::2
ping 2001:DB8:0:2::2
ping 2001:DB8:0:3::2
```
