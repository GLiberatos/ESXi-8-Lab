# 07 - VM Resource Management

## Purpose

This section documents basic virtual machine resource management in the ESXi Host Client.

The goal is to practice changing VM hardware settings, verifying the changes, and reviewing how ESXi records configuration changes through Tasks and Events.

## VM Used

| VM       | Host                 | Datastore   | Network    |
| -------- | -------------------- | ----------- | ---------- |
| fedora01 | vmware01.localdomain | datastore01 | VM Network |

## Starting Configuration

| Resource          | Starting Value |
| ----------------- | -------------: |
| CPU               |         2 vCPU |
| Memory            |           2 GB |
| Hard Disk 1       |          20 GB |
| Network Adapter 1 |     VM Network |

## Resource Changes Performed

| Resource | Change                                | Result                                    |
| -------- | ------------------------------------- | ----------------------------------------- |
| Memory   | 2 GB to 3 GB                          | Successful                                |
| CPU      | 2 vCPU to 1 vCPU, then back to 2 vCPU | Successful                                |
| Disk     | Not changed                           | Skipped because an active snapshot exists |

## Memory Reconfiguration

The `fedora01` VM was powered off before changing memory.

Memory was changed from:

```text
2 GB
```

to:

```text
3 GB
```

The change was confirmed in the VM Hardware Summary.

ESXi recorded the action as:

* Task: `Reconfig VM`
* Target: `fedora01`
* Initiator: `root`
* Result: `Completed successfully`

The VM Events tab also showed:

* `Reconfigured fedora01 on vmware01.localdomain in ha-datacenter`

The event did not display the exact memory value change in the main event list, so the specific value was verified from the Hardware Summary.

## CPU Reconfiguration

The `fedora01` VM was powered off before changing CPU settings.

CPU reconfiguration was tested by changing the VM CPU count from:

```text
2 vCPU
```

to:

```text
1 vCPU
```

and then back to:

```text
2 vCPU
```

The VM could not be increased above 2 vCPU because the nested ESXi host is configured with 2 CPUs available.

The change was confirmed in the VM Hardware Summary.

ESXi recorded the action as:

* Task: `Reconfig VM`
* Target: `fedora01`
* Initiator: `root`
* Result: `Completed successfully`

The VM Events tab also showed:

* `Reconfigured fedora01 on vmware01.localdomain in ha-datacenter`

## Disk Expansion Decision

Disk expansion was not performed in this section.

Reason:

* The `fedora01` VM currently has an active snapshot.
* Snapshot name: `Clean install - powered off baseline`
* Disk changes should be handled carefully when snapshots exist.
* The disk will be expanded later after a deliberate snapshot decision is made.

## Operational Notes

* VM resource changes should be made while the VM is powered off unless hot-add features are intentionally configured and tested.
* Hardware Summary / Edit Settings should be used to confirm the actual assigned CPU and memory values.
* Tasks and Events may show only a general `Reconfig VM` or `Reconfigured VM` entry.
* The exact setting changed may not appear in the main task/event list.
* Disk expansion should be planned carefully, especially when snapshots exist.
* Snapshot files should not be manually deleted from the datastore browser.

## Current State

| Item                     | State                                |
| ------------------------ | ------------------------------------ |
| VM memory                | 3 GB                                 |
| VM CPU                   | 2 vCPU                               |
| VM disk                  | 20 GB                                |
| Active snapshot          | Yes                                  |
| Snapshot name            | Clean install - powered off baseline |
| Disk expansion performed | No                                   |
