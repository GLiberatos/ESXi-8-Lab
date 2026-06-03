# 06 - VM Power Operations and Task/Event Review

## Purpose

This section documents basic virtual machine power operations in the ESXi Host Client.

The goal is to understand how ESXi records VM actions through Recent Tasks, VM Tasks, VM Events, and basic Performance views.

## VM Used

| VM | Host | Datastore | Network |
|---|---|---|---|
| fedora01 | vmware01.localdomain | datastore01 | VM Network |

## Power Operations Practiced

| Operation | Result |
|---|---|
| Power On VM | Completed successfully |
| Shut down guest OS | Completed successfully |

## Task Review

The following task records were reviewed in the ESXi Host Client:

| Task | Target | Initiator | Result |
|---|---|---|---|
| Power On VM | fedora01 | root | Completed successfully |
| Shutdown Guest | fedora01 | root | Completed successfully |

## Event Review

The following VM event types were observed:

- VM starting
- VM powered on
- Guest OS shut down
- VM powered off
- VM reconfigured
- Nested ESXi performance warning

## Performance Views Reviewed

Performance data was reviewed from:

```text
fedora01 > Monitor > Performance
```

Available categories reviewed:

- CPU
- Memory
- Disk
- Network

## CPU Performance Notes

Observed counters included:

- CPU
- Ready

CPU usage was low while the VM was mostly idle. CPU Ready was also low, indicating no visible CPU scheduling pressure during the observation period.

## Memory Performance Notes

Observed memory consumption was low relative to the VM's assigned memory.

The VM is configured with:

```text
2 GB RAM
```

Observed memory usage was approximately:

- 0.61 GB latest
- 0.64 GB maximum

## Disk Performance Notes

Observed disk counters included:

- Disk I/O rate
- Total read rate
- Total write rate
- Maximum latency

Disk activity showed brief spikes during VM activity, with low current disk usage while idle.

## Network Performance Notes

Observed network counters included:

- Total network usage
- Total receive rate
- Total transmit rate

Network activity was low while the VM was idle.

## Operational Notes

- Recent Tasks provide quick confirmation after an action.
- VM Tasks show task history for the selected VM.
- VM Events show a timeline of VM activity.
- Performance views are most useful while the VM is powered on.
- A powered-off VM may show limited or unavailable live performance data.
- Historical troubleshooting should use Tasks, Events, and logs rather than live performance charts.

## Important Power Operation Notes

| Action             | Meaning                              | Recommended Use                                                  |
| ------------------ | ------------------------------------ | ---------------------------------------------------------------- |
| Shut down guest OS | Graceful shutdown using VMware Tools | Normal maintenance                                               |
| Power off          | Hard power cut to the VM             | Only when the guest is frozen or unresponsive                    |
| Reset              | Hard reboot                          | Only when needed for recovery                                    |
| Suspend            | Pauses VM state                      | Usually avoided for server workloads unless specifically testing |

## Current State

| Item                       | State |
| -------------------------- | ----- |
| VM power operations tested | Yes   |
| Recent Tasks reviewed      | Yes   |
| VM Events reviewed         | Yes   |
| VM Tasks reviewed          | Yes   |
| Performance views reviewed | Yes   |

