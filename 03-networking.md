# 03 - ESXi Networking

## Purpose

This section documents the basic ESXi networking configuration used in the lab.

The current configuration uses the default ESXi standard switch and default port groups.

## Network Summary

| Host | VMkernel NIC | Management IP | Port Group | Services |
|---|---|---:|---|---|
| vmware01.localdomain | vmk0 | 192.168.50.166 | Management Network | Management, PTP |
| vmware02.localdomain | vmk0 | 192.168.50.167 | Management Network | Management, PTP |

## Port Groups

Both ESXi hosts have matching default port groups.

| Port Group | VLAN ID | vSwitch | Purpose |
|---|---:|---|---|
| Management Network | 0 | vSwitch0 | ESXi host management traffic |
| VM Network | 0 | vSwitch0 | Virtual machine network traffic |

## Current Network Design

```text
Physical / Outer Network
        |
ESXi Standard Switch: vSwitch0
        |
        |-- Management Network
        |     |-- vmk0
        |     |-- ESXi Host Client access
        |
        |-- VM Network
              |-- Virtual machine network adapters
```
## Current Validation

The following items were verified:

- Both ESXi hosts are reachable through the ESXi Host Client.
- Both hosts use separate management IP addresses.
- Both hosts use the same gateway: 192.168.50.1.
- Both hosts use the same DNS server: 192.168.50.1.
- Both hosts have matching port group names.
- The fedora01 VM successfully connected to the VM Network port group.
- The fedora01 VM received an IP address and successfully reached the gateway and internet.

## Important Notes

- VLAN tagging is not currently configured.
- Both port groups use VLAN ID 0.
- The current design is appropriate for a beginner ESXi lab.
- Future networking labs may include additional port groups, VLANs, and VMkernel adapters.
- VMkernel networking should be changed carefully because incorrect changes can break ESXi management access.

