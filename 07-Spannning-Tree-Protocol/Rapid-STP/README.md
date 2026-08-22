# Overview

RSTP uses **two tie-breakers** to elect the Root Bridge:

* **Lower Priority number** wins.
* If the priority is the same, **lower MAC address** wins.

After selecting the Root Bridge:

* All ports on the Root Bridge are **Designated Ports**.
* Ports leading toward the Root Bridge are **Root Ports**.
* Root Port tie-breakers: **lower path cost → lower Bridge ID → lower port number**.
* **Always remember: every link has one Designated Port.**
* `Bridge ID = Priority Number + MAC Address`

# Configuration

Enable Rapid PVST+ on all switches:

```cisco
spanning-tree mode rapid-pvst
```

Configure switch-to-switch interfaces as point-to-point:

```cisco
interface f0/x
 spanning-tree link-type point-to-point
```

Configure interfaces connected to the hub as shared:

```cisco
interface f0/24
 spanning-tree link-type shared
```
