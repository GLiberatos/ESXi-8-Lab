# 08 - ESXi Host Services

## Purpose

This section documents ESXi host services reviewed in the ESXi Host Client.

The goal is to understand common ESXi services, their purpose, current state, and how service actions appear in the Host Client.

## Host Reviewed

| Host                 |  Management IP |
| -------------------- | -------------: |
| vmware01.localdomain | 192.168.50.166 |

## Services Reviewed

The following services were reviewed from:

```text
vmware01 > Manage > Services
```

| Service   | Observed Status                           | Simple Purpose                              |
| --------- | ----------------------------------------- | ------------------------------------------- |
| DCUI      | Running                                   | Local ESXi console interface                |
| TSM       | Stopped                                   | Local ESXi Shell                            |
| TSM-SSH   | Stopped before testing                    | Remote SSH access to ESXi                   |
| ntpd      | Stopped                                   | NTP time synchronization                    |
| ptpd      | Stopped                                   | Precision Time Protocol service             |
| vmsyslogd | Running                                   | ESXi logging/syslog service                 |
| snmpd     | Stopped                                   | SNMP monitoring service                     |
| slpd      | Stopped                                   | Service discovery service                   |
| lwsmd     | Stopped                                   | Active Directory/domain integration service |
| vpxa      | Running                                   | vCenter agent on the ESXi host              |
| hostd     | Not visible in Host Client service search | Core ESXi host management service           |

## Simple Service Explanations

### DCUI

`DCUI` is the local ESXi console interface.

It is the yellow/gray console screen used to perform basic host actions such as configuring the management network, restarting the management network, and accessing local troubleshooting options.

### TSM

`TSM` is the local ESXi Shell.

It provides command-line access directly from the ESXi host console.

### TSM-SSH

`TSM-SSH` provides remote SSH access to the ESXi host.

Example:

```text
ssh root@192.168.50.166
```

SSH should normally remain stopped unless it is needed for a planned administrative or troubleshooting task.

### ntpd

`ntpd` is the Network Time Protocol service.

It is used to synchronize ESXi host time with an NTP server.

### ptpd

`ptpd` is the Precision Time Protocol service.

It is used for environments that require more precise time synchronization.

### vmsyslogd

`vmsyslogd` is the ESXi syslog/logging service.

It supports ESXi host logging.

### snmpd

`snmpd` is the SNMP service.

It is used when an external monitoring system collects host information through SNMP.

### slpd

`slpd` is the Service Location Protocol service.

It is commonly kept stopped unless specifically required.

### lwsmd

`lwsmd` is related to Active Directory/domain integration.

This may become relevant later because the lab environment includes Active Directory and hybrid cloud components, but it was not enabled during this section.

### hostd

`hostd` is the main ESXi host management service.

Simple explanation:

```text
hostd = helps manage the ESXi host directly
```

It supports direct ESXi host management tasks such as Host Client access, VM operations, host configuration, storage, networking, and task handling.

During this lab, `hostd` was searched for in the Host Client services list, but it was not visible in the service search results.

No action was taken on `hostd`.

### vpxa

`vpxa` is the vCenter agent on the ESXi host.

Simple explanation:

```text
vpxa = helps vCenter communicate with the ESXi host
```

This becomes more important later when vCenter is deployed and ESXi hosts are added to vCenter.

## TSM-SSH Start/Stop Test

`TSM-SSH` was started and stopped from:

```text
vmware01 > Manage > Services
```

The start/stop actions appeared in the bottom Recent Tasks pane.

After checking:

```text
vmware01 > Monitor > Tasks
vmware01 > Monitor > Events
```

no historical entries for the TSM-SSH start/stop actions were visible during this lab check.

## Observed Behavior

| Area Checked            | Result                                              |
| ----------------------- | --------------------------------------------------- |
| Recent Tasks            | TSM-SSH start/stop actions were visible immediately |
| Host > Monitor > Tasks  | No visible historical TSM-SSH start/stop entries    |
| Host > Monitor > Events | No visible historical TSM-SSH start/stop entries    |

## Operational Notes

- Recent Tasks is useful for immediate confirmation after a service action.
- In this lab, the TSM-SSH start/stop action was not visible later in Host Monitor Tasks or Events.
- Not every action shown in Recent Tasks was visible later in the Host Client historical task/event views.
- SSH should normally remain stopped unless needed.
- If deeper troubleshooting is required later, ESXi logs may need to be reviewed.
- No host services were restarted except for the temporary TSM-SSH start/stop test.
- No changes were made to `hostd` or `vpxa`.

## Current State

| Item                                 | State |
| ------------------------------------ | ----- |
| Host services reviewed               | Yes   |
| TSM-SSH tested                       | Yes   |
| TSM-SSH left running long-term       | No    |
| hostd modified                       | No    |
| vpxa modified                        | No    |
| Active Directory integration enabled | No    |
