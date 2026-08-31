# Overview

This lab focuses on configuring **Network Time Protocol (NTP)** on R1, R2, and R3. R1 synchronizes with an external NTP server and then acts as a Stratum 8 NTP master for R2 and R3 using authentication. Time zones and hardware calendar updates are also configured.

# Configuration

### R1

```cisco
clock set 12:00:00 Dec 30 2020
clock timezone PKT 5 0
ntp server 1.1.1.1
ntp master 8
ntp authenticate
ntp authentication-key 1 md5 cisco
ntp trusted-key 1
ntp update-calendar
```

### R2

```cisco
clock set 12:00:00 Dec 30 2020
clock timezone PKT 5 0
ntp authenticate
ntp authentication-key 1 md5 cisco
ntp trusted-key 1
ntp server 192.168.12.1 key 1
ntp update-calendar
```

### R3

```cisco
clock set 12:00:00 Dec 30 2020
clock timezone PKT 5 0
ntp authenticate
ntp authentication-key 1 md5 cisco
ntp trusted-key 1
ntp server 192.168.13.1 key 1
ntp update-calendar
```

### Verification

```cisco
show clock
show ntp status
show ntp associations
```
