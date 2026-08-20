# Configuring Spanning Tree

## Overview

This lab focuses on configuring and verifying **Spanning Tree Protocol (STP)**, including root bridge selection, STP path cost, port priority, PortFast, and BPDU Guard.

## Configuration

### Task 2 — Configure Root Bridges

**SW1 — Primary Root for VLAN 1, Secondary Root for VLAN 2**

```cisco
enable
configure terminal

spanning-tree vlan 1 root primary
spanning-tree vlan 2 root secondary

end
```

**SW2 — Primary Root for VLAN 2, Secondary Root for VLAN 1**

```cisco
enable
configure terminal

spanning-tree vlan 2 root primary
spanning-tree vlan 1 root secondary

end
```

### Task 3 — Increase VLAN 1 Cost on SW4 Fa0/2

**SW4**

```cisco
enable
configure terminal

interface fastEthernet 0/2
spanning-tree vlan 1 cost 100

end
```

### Task 4 — Increase VLAN 1 Port Priority on SW1 Fa0/1

**SW1**

```cisco
enable
configure terminal

interface fastEthernet 0/1
spanning-tree vlan 1 port-priority 240

end
```

### Task 5 — Configure PortFast and BPDU Guard

**SW3**

```cisco
enable
configure terminal

interface fastEthernet 0/3
spanning-tree portfast
spanning-tree bpduguard enable

end
```

**SW4**

```cisco
enable
configure terminal

interface fastEthernet 0/3
spanning-tree portfast
spanning-tree bpduguard enable

end
```

### Verification

```cisco
show spanning-tree
show spanning-tree vlan 1
show spanning-tree vlan 2
```
