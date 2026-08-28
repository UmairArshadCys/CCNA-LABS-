# Overview

Configured **extended ACLs** on R1 to enforce network security policies by blocking specific traffic between the internal networks and servers while allowing all other traffic.

# Configuration

```cisco
enable
configure terminal

ip access-list extended BLOCK-PC1
deny ip 172.16.2.0 0.0.0.255 host 172.16.1.2
permit ip any any

interface g0/1
ip access-group BLOCK-PC1 in
exit

ip access-list extended BLOCK-SERVICES
deny udp 172.16.1.0 0.0.0.255 host 192.168.1.100 eq 53
deny tcp 172.16.1.0 0.0.0.255 host 192.168.1.100 eq 53
deny tcp 172.16.1.0 0.0.0.255 host 192.168.2.100 eq 80
deny tcp 172.16.1.0 0.0.0.255 host 192.168.2.100 eq 443
permit ip any any

interface g0/0
ip access-group BLOCK-SERVICES in
exit

end
write memory
```
