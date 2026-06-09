# 09 - Monitoring and Troubleshooting

## Purpose

This section documents host-level monitoring and troubleshooting areas in the ESXi Host Client.

The goal is to understand where to look when troubleshooting ESXi host or virtual machine issues.

## Host Reviewed

| Host                 |  Management IP |
| -------------------- | -------------: |
| vmware01.localdomain | 192.168.50.166 |

## Monitoring Location

Host-level monitoring was reviewed from:

```text
vmware01 > Monitor
```

The following tabs were visible:

- Performance
- Hardware
- Events
- Tasks
- Logs
- Notifications

## Host Performance Categories Reviewed

Host performance was reviewed from:

```text
vmware01 > Monitor > Performance
```

The available performance categories were:

- CPU
- Memory
- Network
- Disk

## CPU Performance

The CPU performance view showed host-level CPU usage for `vmware01`.

Observed values included low CPU usage during the review period.

| Counter              | Average | Maximum | Latest |
| -------------------- | ------: | ------: | -----: |
| vmware01.localdomain |    1.2% |   4.96% |  1.05% |
| PCPU 0               |   1.18% |    4.6% |  1.47% |
| PCPU 1               |   1.21% |   5.31% |  0.63% |
| Package 0            |   2.37% |    4.6% |  1.47% |

### CPU Takeaway

The ESXi host was mostly idle during the observation period.

## Memory Performance

The Memory performance view showed consumed host memory.

| Counter              | Unit | Average | Maximum | Minimum | Latest |
| -------------------- | ---: | ------: | ------: | ------: | -----: |
| Consumed host memory |   GB |    1.61 |    1.62 |    1.61 |   1.61 |

### Memory Takeaway

The host had stable memory usage during the review period.

## Network Performance

The Network performance view showed host-level network usage.

| Counter             | Unit | Average | Maximum | Minimum | Latest |
| ------------------- | ---: | ------: | ------: | ------: | -----: |
| Total network usage | Mbps |    0.95 |   62.05 |    0.19 |   0.44 |
| Total receive rate  | Mbps |    0.91 |   62.05 |    0.19 |   0.44 |
| Total transmit rate | Mbps |    0.04 |     5.5 |       0 |      0 |

### Network Takeaway

The host showed mostly low network usage, with one visible receive traffic spike during the reviewed time period.

The exact cause of the spike was not determined from the chart alone.

## Disk Performance

The Disk performance view showed host-level disk activity.

| Counter          | Unit | Average | Maximum | Minimum | Latest |
| ---------------- | ---: | ------: | ------: | ------: | -----: |
| Total disk usage | MB/s |    0.01 |    0.16 |       0 |   0.01 |
| Total read rate  | MB/s |    0.01 |    0.09 |       0 |   0.01 |
| Total write rate | MB/s |    0.01 |    0.08 |       0 |      0 |

### Disk Takeaway

The host showed low disk activity during the review period.

## Host Events Reviewed

Host-level events were reviewed from:

```text
vmware01 > Monitor > Events
```

Observed event types included:

- SSH access enabled
- SSH access disabled
- Root user login
- Root user logout
- VM log file download activity

## Host Tasks Reviewed

Host-level tasks were reviewed from:

```text
vmware01 > Monitor > Tasks
```

Observed task types included:

- Refresh Services
- Start Service
- Stop Service
- installDate

The service start/stop actions were visible under the host-level Tasks view.

## Logs Reviewed

Host logs were reviewed from:

```text
vmware01 > Monitor > Logs
```

Visible log files included:

| Log File                | Simple Purpose                        |
| ----------------------- | ------------------------------------- |
| /var/log/vpxa.log       | vCenter agent log                     |
| /var/log/vobd.log       | VMware observer daemon log            |
| /var/log/vmkwarning.log | VMkernel warning log                  |
| /var/log/vmkeventd.log  | VMkernel event daemon log             |
| /var/log/vmkernel.log   | VMkernel subsystem log                |
| /var/log/vmkdevmgr.log  | VMkernel device manager log           |
| /var/log/vmauthd.log    | vMotion authentication daemon log     |
| /var/log/syslog.log     | General ESXi system log               |
| /var/log/sysboot.log    | System boot log                       |
| /var/log/shell.log      | ESXi shell activity log               |
| /var/log/hostd.log      | Host agent log                        |
| /var/log/fdm.log        | Fault Domain Manager / HA-related log |
| /var/log/esxupdate.log  | ESXi update log                       |
| /var/log/dhclient.log   | DHCP client log                       |
| /var/log/auth.log       | Authentication subsystem log          |

## Logs to Remember First

| Log            | Why It Matters                                   |
| -------------- | ------------------------------------------------ |
| hostd.log      | Host Client and host management activity         |
| vpxa.log       | vCenter communication later                      |
| vmkernel.log   | Kernel, hardware, storage, and networking issues |
| vmkwarning.log | VMkernel warnings                                |
| auth.log       | Login and authentication activity                |
| shell.log      | ESXi Shell activity                              |
| syslog.log     | General ESXi system messages                     |
| esxupdate.log  | ESXi patch and update troubleshooting            |

## Notifications

The Notifications tab was reviewed.

No visible notifications were present during this lab check.

## Host vs VM Monitoring

| Issue Type              | Correct Monitoring Location     |
| ----------------------- | ------------------------------- |
| Host performance issue  | Host > Monitor > Performance    |
| Host service action     | Host > Monitor > Tasks / Events |
| SSH enabled or disabled | Host > Monitor > Events         |
| VM power operation      | VM > Monitor > Tasks / Events   |
| VM performance issue    | VM > Monitor > Performance      |
| Host log review         | Host > Monitor > Logs           |

## Troubleshooting Order

A practical ESXi troubleshooting order:

1. Check Recent Tasks.
2. Check the correct Monitor view: Host or VM.
3. Review Events.
4. Review Tasks.
5. Review Performance charts.
6. Review Logs.
7. Generate a support bundle only when deeper troubleshooting or vendor support requires it.

## Operational Notes

- Host-level actions should be reviewed from the host monitoring view.
- VM-level actions should be reviewed from the VM monitoring view.
- Performance charts help identify whether resource usage is low, spiking, or sustained.
- Events provide a timeline of activity.
- Tasks show whether an action completed successfully or failed.
- Logs are used for deeper troubleshooting.
- Notifications may be empty when there are no visible warnings or alerts.
- A support bundle was not generated during this section.

## Current State

| Item                      | State |
| ------------------------- | ----- |
| Host Performance reviewed | Yes   |
| Host Events reviewed      | Yes   |
| Host Tasks reviewed       | Yes   |
| Host Logs reviewed        | Yes   |
| Notifications reviewed    | Yes   |
| Notifications present     | No    |
| Support bundle generated  | No    |

