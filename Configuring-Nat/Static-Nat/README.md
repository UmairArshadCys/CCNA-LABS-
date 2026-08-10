# Static NAT Configuration

### Overview

This lab demonstrates **Static NAT** on a Cisco router, mapping private IP addresses of internal PCs to fixed public IP addresses and verifying connectivity to an external server.

### Key Configurations

```cisco
interface g0/1
 ip nat inside

interface g0/0
 ip nat outside

ip nat inside source static 172.16.0.1 100.0.0.1
ip nat inside source static 172.16.0.2 100.0.0.2
ip nat inside source static 172.16.0.3 100.0.0.3
```

**Verification:**

```cisco
show ip nat translations
```

**Clear dynamic NAT translations:**

```cisco
clear ip nat translation *
```

**Test connectivity:**

```text
ping 8.8.8.8
```
