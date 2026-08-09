# Static Routing Lab

## Overview

This lab demonstrates **static routing** between multiple routers to enable communication between separate networks. Static routes are manually configured on the routers to provide paths toward remote networks.

## Files Included

Static-Routing-Configuration.pkt – Complete static routing configuration lab.
Static-Routing-Troubleshooting-Challenge.pkt – Lab containing incorrect static routes and IP addressing errors for troubleshooting practice.
Static-Routing-Troubleshooting-Solution.pkt – Corrected version of the troubleshooting lab with all issues resolved.

## Key Configuration

### Static Route Configuration

```cisco
ip route 192.168.1.0 255.255.255.0 192.168.12.1
ip route 192.168.3.0 255.255.255.0 192.168.13.3


