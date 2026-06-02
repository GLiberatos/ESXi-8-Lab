# 01 - ESXi Host Baseline

## Hosts

| Hostname | Management IP | DNS Server | Gateway |
|---|---:|---:|---:|
| vmware01.localdomain | 192.168.50.166 | 192.168.50.1 | 192.168.50.1 |
| vmware02.localdomain | 192.168.50.167 | 192.168.50.1 | 192.168.50.1 |

## Hardware Summary

| Host | CPU | Memory | Notes |
|---|---|---:|---|
| vmware01.localdomain | 2 CPUs x 13th Gen Intel Core i7-13700 | 4 GB | Nested ESXi VM |
| vmware02.localdomain | 2 CPUs x 13th Gen Intel Core i7-13700 | 4 GB | Nested ESXi VM |

## Baseline Notes

- Both hosts are reachable through the ESXi Host Client.
- Both hosts use separate management IP addresses.
- Both hosts use the same DNS server and gateway.
- Both hosts have matching default port groups:
  - Management Network
  - VM Network

## Security Notes

- No passwords, license keys, serial numbers, or sensitive credentials are stored in this repository.
- Private RFC1918 lab IP addresses are used for documentation only.
- Screenshots are reviewed before upload to avoid exposing sensitive information.