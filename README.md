# ESXi 8 Hands-On Lab

This project documents my hands-on ESXi 8 lab used to practice VMware administration and operational support tasks.

## Lab Goals

- Install and manage ESXi 8 hosts
- Configure local VMFS datastores
- Manage virtual networking with standard port groups
- Create and manage virtual machines
- Use snapshots for lab rollback points
- Practice ESXi operational troubleshooting
- Prepare for vCenter, clustering, and multi-host administration

## Lab Environment

| Host | IP Address | Datastore |
|---|---:|---|
| vmware01.localdomain | 192.168.50.166 | datastore01 |
| vmware02.localdomain | 192.168.50.167 | datastore02 |

## Current Status

- Two ESXi hosts deployed
- Local datastores configured
- Default networking verified
- Fedora Server VM created as a test workload
- Clean powered-off baseline snapshot created