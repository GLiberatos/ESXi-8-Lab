# 02 - Storage and Datastores

## Purpose

This section documents the local storage configuration used in the ESXi 8 lab.

Each ESXi host has a local VMFS datastore used for virtual machines, ISO storage, and lab testing.

## Datastore Summary

| Host | Datastore | Type | Capacity | Free Space | Access |
|---|---|---|---:|---:|---|
| vmware01.localdomain | datastore01 | VMFS6 | 39.75 GB | 38.34 GB | Single |
| vmware02.localdomain | datastore02 | VMFS6 | 39.75 GB | 38.34 GB | Single |

## Storage Notes

- Each ESXi host uses local storage.
- Each datastore is formatted as VMFS6.
- Datastore access is single-host access.
- Thin provisioning is supported.
- Local datastores are sufficient for VM creation and basic ESXi operations.
- Shared storage is not configured yet.

## Current Datastore Usage

### vmware01.localdomain

The `datastore01` datastore is currently used for:

- ISO storage
- Fedora Server ISO upload
- `fedora01` virtual machine
- Clean powered-off baseline snapshot

### vmware02.localdomain

The `datastore02` datastore is currently empty and ready for future lab use.

## Important Notes

- Local storage does not provide shared access between ESXi hosts.
- vMotion and cluster features may require additional configuration later.
- No datastore files should be manually deleted unless their purpose is understood.
- VM folders, VMDK files, VMX files, and snapshot files should be managed through the ESXi Host Client whenever possible.