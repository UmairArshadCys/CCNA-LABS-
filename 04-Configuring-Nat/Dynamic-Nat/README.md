# Overview

Configured **Dynamic NAT and PAT (NAT Overload)** on R1. Dynamic NAT uses a pool of `100.0.0.1–100.0.0.2`, while PAT allows multiple internal hosts to share R1's public IP `203.0.113.2` using different port numbers.

The screenshots show the NAT translations generated during the lab and the successful PAT configuration.

# Key Configurations

### Dynamic NAT

```cisco
access-list 1 permit 172.16.0.0 0.0.0.255

ip nat pool MYPOOL 100.0.0.1 100.0.0.2 netmask 255.255.255.0

ip nat inside source list 1 pool MYPOOL
```

### PAT / NAT Overload

After removing the Dynamic NAT configuration:

```cisco
no ip nat inside source list 1 pool MYPOOL
no ip nat pool MYPOOL

ip nat inside source list 1 interface g0/0 overload
```

### NAT Interfaces

```cisco
interface g0/1
 ip nat inside

interface g0/0
 ip nat outside
```

### Verification

```cisco
show ip nat translations
show ip nat statistics
```

**Result:** Dynamic NAT is limited by the available address pool, while PAT allows multiple internal hosts to share the single public IP `203.0.113.2`.
