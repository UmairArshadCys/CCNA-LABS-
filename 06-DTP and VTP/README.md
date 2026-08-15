## Overview

This Cisco Packet Tracer lab focuses on **VTP and DTP configuration** between multiple switches. SW1 is configured as the VTP server, SW2 as transparent, and SW3 as a VTP client. Switch-to-switch links are configured as static trunk ports with DTP disabled. VLANs are also configured and assigned to the appropriate access ports.

## Key Configurations

* Configured switch-to-switch links as **static trunk ports**.
* Disabled DTP using:

  ```cisco
  switchport nonegotiate
  ```
* Configured **SW1 as VTP Server**.
* Configured **SW2 as VTP Transparent**.
* Configured **SW3 as VTP Client**.
* Created and verified VLANs **10, 20, 30, and 40**.
* Configured host-facing interfaces as **access ports** and assigned them to the correct VLANs.
* Verified trunking and interface modes using:

  ```cisco
  show interfaces trunk
  show interfaces switchport
  ```
* Verified VTP configuration using:

  ```cisco
  show vtp status
  ```
* Verified VLAN configuration using:

  ```cisco
  show vlan brief
  ```
