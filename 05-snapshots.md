# 05 - Snapshot Management

## Purpose

This section documents snapshot usage in the ESXi 8 lab.

Snapshots are used as temporary rollback points during lab exercises. They are not treated as backups.

## Snapshot Summary

| VM | Host | Datastore | Snapshot Name | Snapshot Type | Purpose |
|---|---|---|---|---|---|
| fedora01 | vmware01.localdomain | datastore01 | Clean install - powered off baseline | Powered-off baseline | Rollback point after initial VM build |

## Snapshot Details

### fedora01

| Item | Value |
|---|---|
| VM Name | fedora01 |
| ESXi Host | vmware01.localdomain |
| Datastore | datastore01 |
| Snapshot Name | Clean install - powered off baseline |
| VM Power State at Snapshot | Powered off |
| Memory Snapshot | No |
| Guest File System Quiescing | No |
| ISO Connected | No |
| VMware Tools Status | Running before shutdown |
| Network Status | Verified before shutdown |

## Snapshot Description

The snapshot was created after the following tasks were completed:

- Fedora Server was installed as a lightweight test workload.
- The VM was connected to the `VM Network` port group.
- The VM received an IP address.
- Gateway connectivity was verified.
- DNS and internet connectivity were verified.
- VMware Tools was confirmed running.
- The Fedora ISO was disconnected.
- The VM was shut down cleanly.
- The VM was powered off before taking the snapshot.

## Operational Notes

- This snapshot provides a clean rollback point for future ESXi practice.
- The snapshot was taken while the VM was powered off.
- No memory state was captured.
- Guest file system quiescing was not used because the VM was powered off.
- The snapshot should be deleted later after a proper backup or after the lab no longer requires the rollback point.

## Important Snapshot Rules

- Snapshots are not backups.
- Snapshots should not be kept long-term.
- Snapshots can grow over time if the VM continues running after the snapshot.
- Snapshot growth can consume datastore space.
- Snapshot actions should be performed through the ESXi Host Client.
- Snapshot files should not be manually deleted from the datastore browser.

## Current State

| Item | State |
|---|---|
| Snapshot exists | Yes |
| Snapshot verified in Snapshot Manager | Yes |
| VM currently powered off | Yes |
| Rollback point available | Yes |
