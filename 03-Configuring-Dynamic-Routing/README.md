# EIGRP Unequal-Cost Load Balancing Lab

## Overview
A Cisco Packet Tracer lab focused on configuring EIGRP and implementing unequal-cost load balancing using the `variance` command.

## Objectives
- Configure EIGRP AS 1 on the routers.
- Configure loopback interfaces and advertise networks.
- Disable EIGRP auto-summary.
- Configure appropriate passive interfaces.
- Configure R1 for unequal-cost load balancing toward `192.168.4.0/24`.
- Use the EIGRP `variance` command to allow an alternate path.

## Files Included
- `EIGRP Configuration.pkt` — Cisco Packet Tracer lab file.

## Outcome
Configured EIGRP unequal-cost load balancing on R1 using `variance 2`, allowing R1 to use both qualifying paths toward `192.168.4.0/24`.
