# Spanning Tree Protocol

This lab demonstrates the **Spanning Tree Protocol (STP)** and the election of the Root Bridge and port roles. 
The switch with the **lowest Bridge ID** (priority first, then MAC address if needed) becomes the Root Bridge, 
and all of its active ports are **Designated Ports**. The ports on other switches that provide the best path directly 
toward the Root Bridge are **Root Ports**. On every other network segment, STP elects one **Designated Port**, while the
redundant port becomes **Non-Designated/Alternate** and is placed in a blocking state to prevent loops. Port-role elections
use the relevant STP tie-breakers, including **lowest root path cost, lowest Bridge ID, and lowest Port ID**.

Use the provided Packet Tracer file for practice: **draw or recreate the topology yourself, determine the
Root Bridge and every port role before checking the CLI output, and then use `show spanning-tree` to verify your answers.** 
Try creating different topologies as well and repeat the process.
