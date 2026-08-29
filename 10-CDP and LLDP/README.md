# Overview

This lab focuses on **CDP (Cisco Discovery Protocol)** and **LLDP (Link Layer Discovery Protocol)** for discovering directly connected network devices. CDP was used to identify device IP addresses and interface IDs, then disabled and replaced with LLDP for neighbor discovery.

# Configuration

### CDP Discovery

```cisco
show cdp neighbors
show cdp neighbors detail
show ip interface brief
```

### Disable CDP on PC Interfaces

```cisco
interface fastethernet 0/1
no cdp enable
```

### Disable CDP Globally

```cisco
no cdp run
```

### Enable LLDP Globally

```cisco
lldp run
```

### Enable LLDP Tx/Rx

```cisco
interface gigabitethernet 0/0
lldp transmit
lldp receive
```

### Verify LLDP

```cisco
show lldp neighbors
show lldp neighbors detail
show lldp interface
```
