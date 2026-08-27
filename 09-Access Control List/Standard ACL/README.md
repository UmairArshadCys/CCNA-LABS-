## Overview

Configured OSPF between R1 and R2 and applied standard ACLs to control access between the required networks.

## Configurations

```cisco
router ospf 1
 network 172.16.1.0 0.0.0.255 area 0
 network 172.16.2.0 0.0.0.255 area 0
 network 203.0.113.0 0.0.0.3 area 0

access-list 10 deny 172.16.1.0 0.0.0.255
access-list 10 permit any

access-list 11 deny 172.16.2.0 0.0.0.255
access-list 11 permit any

access-list 12 permit host 172.16.1.1
access-list 12 permit host 172.16.2.1
access-list 12 deny any

ip access-list standard BLOCK_VLAN2
 deny 172.16.2.0 0.0.0.255
 permit any
```
