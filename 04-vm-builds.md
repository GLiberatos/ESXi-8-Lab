# 04 - Virtual Machine Builds

## Purpose

This section documents virtual machines created in the ESXi 8 lab.

The goal is to track VM configuration, placement, networking, storage, and operational status from the ESXi perspective.

## VM Summary

| VM Name | Host | Datastore | Guest OS | Network | Status |
|---|---|---|---|---|---|
| fedora01 | vmware01.localdomain | datastore01 | Fedora Server | VM Network | Powered off baseline |

## VM Configuration

### fedora01

| Setting | Value |
|---|---|
| VM Name | fedora01 |
| ESXi Host | vmware01.localdomain |
| Datastore | datastore01 |
| Guest OS | Fedora Server |
| vCPU | 2 |
| Memory | 2 GB |
| Virtual Disk | 20 GB |
| Network Adapter | VM Network |
| ISO Used | Fedora-Server-dvd-x86_64-41-1.7.iso |
| VMware Tools | Running |
| Hostname inside guest | fedora01 |

## Build Steps Completed

The following ESXi-level tasks were completed:

- Created a new virtual machine named `fedora01`.
- Placed the VM on `datastore01`.
- Connected the VM to the `VM Network` port group.
- Attached the Fedora Server ISO from the datastore ISO folder.
- Powered on the VM through the ESXi Host Client.
- Used the VM console to complete the guest OS installation.
- Verified that the VM received network connectivity.
- Verified that VMware Tools was running.
- Disconnected the installation ISO after installation.
- Shut down the VM cleanly.
- Created a clean powered-off baseline snapshot.

## Operational Notes

- Fedora Server is used only as a lightweight test workload for ESXi operations.
- Linux administration is not the focus of this section.
- The VM is used to practice ESXi tasks such as power operations, snapshots, console access, networking validation, and datastore usage.

## Current State

| Item | State |
|---|---|
| VM Power State | Powered off |
| ISO Connected | No |
| Snapshot Created | Yes |
| Snapshot Name | Clean install - powered off baseline |
| Network Verified | Yes |
| VMware Tools Verified | Yes |

## Important Notes

- VM settings should be changed through the ESXi Host Client.
- Installation ISOs should be disconnected after guest OS installation.
- Snapshots are useful for lab rollback points but should not be treated as backups.
- VM configuration, disk, and snapshot files should not be manually deleted from the datastore browser unless their purpose is fully understood.