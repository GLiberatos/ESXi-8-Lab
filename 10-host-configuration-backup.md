# 10 - ESXi Host Configuration Backup

## Objective

The objective of this section was to perform a configuration backup of the ESXi host `vmware01.localdomain`.

This backup is intended to protect the ESXi host configuration, not the virtual machines running on the host.

## Host Backed Up

| Item          | Value                                   |
| ------------- | --------------------------------------- |
| ESXi Host     | `vmware01.localdomain`                  |
| Management IP | `192.168.50.166`                        |
| Backup Type   | ESXi host configuration backup          |
| Backup File   | `configBundle-vmware01.localdomain.tgz` |
| Backup Date   | `2026-06-08`                            |

## Commands Used

The backup was performed from an SSH session to the ESXi host.

Before creating the backup bundle, the current host configuration was synchronized:

```bash
vim-cmd hostsvc/firmware/sync_config
```

Then the host configuration backup bundle was generated:

```bash
vim-cmd hostsvc/firmware/backup_config
```

The backup command generated a downloadable `.tgz` configuration bundle.

## Backup Result

The ESXi host generated a configuration bundle named:

```text
configBundle-vmware01.localdomain.tgz
```

The file was downloaded successfully and stored outside of the GitHub repository.

The backup file was not uploaded to GitHub because it may contain host-specific configuration details.

## SSH Usage

SSH was temporarily enabled only for the backup procedure.

After the backup was completed and downloaded, the `TSM-SSH` service was stopped again.

| Service   | Final State |
| --------- | ----------- |
| `TSM-SSH` | Stopped     |

## Important Notes

This backup protects the ESXi host configuration only.

It does not back up:

- Virtual machine disks
- Guest operating systems
- Application data
- VM snapshots
- Datastore contents

A VM backup solution would still be required to protect virtual machines and their data.

## Cluster Consideration

In a multi-host VMware environment, ESXi configuration backups are host-specific.

Each ESXi host should have its own configuration backup.

Example:

```text
vmware01-config-backup.tgz
vmware02-config-backup.tgz
```

An ESXi host configuration backup does not replace:

- vCenter backup
- VM backup
- Shared storage backup
- vSphere HA
- vMotion
- DRS

## Operational Understanding

This task demonstrated how to:

- Temporarily enable SSH for host administration
- Use `vim-cmd` to synchronize the ESXi host configuration
- Generate an ESXi host configuration backup bundle
- Download the configuration backup file
- Disable SSH after completing the administrative task
- Separate host configuration backup from VM-level backup

## Interview Explanation

I backed up an ESXi host configuration using SSH and the `vim-cmd` utility.

I first synchronized the current host configuration with `sync_config`, then generated a downloadable configuration bundle with `backup_config`.

I understand that this type of backup protects the ESXi host configuration, not the virtual machines or their virtual disks.

After completing the backup, I disabled SSH again to return the host to a safer operational state.
