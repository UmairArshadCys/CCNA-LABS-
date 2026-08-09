# EIGRP Unequal-Cost Load Balancing Lab

## Overview

This lab demonstrates **EIGRP configuration** and **unequal-cost load balancing**. EIGRP is configured between multiple routers, and R1 is configured with a variance value to allow the use of multiple feasible paths toward the destination network.

## Key Configuration

### EIGRP Configuration

```cisco
router eigrp 1
 router-id 2.2.2.2
 network 10.0.0.0
 no auto-summary
router eigrp 1
 variance 2
