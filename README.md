# AWS VPC Peering - Private Connectivity Between Two VPCs

**Student:** Devesh Chak  
**Batch:** October 2026  
**Region:** `ap-south-1`  
**Completion date on report:** 31 October 2026

> Resource IDs, CIDRs, private IPs, and peering details below are transcribed from the updated student report. They are not independently verified against the live AWS account. Test outcomes and cleanup remain evidence-required; do not represent expected results as completed tests.

## Project objective
Build private IPv4 connectivity between two non-overlapping VPCs using VPC Peering, with a bastion host in VPC A for administration and two private application instances.

## Architecture and addressing

| Component | CIDR / address | Resource ID / detail |
|---|---|---|
| VPC A (`ewb-vpc-a`) | `10.10.0.0/16` | `vpc-069b48ebe177469f5` |
| Public subnet A (`ewb-a-public`) | `10.10.1.0/24` | `subnet-0a35f8f2e927d5a39` |
| Private subnet A (`ewb-a-private`) | `10.10.2.0/24` | `subnet-044129b0cb3bbfb91` |
| VPC B (`ewb-vpc-b`) | `10.20.0.0/16` | `vpc-0fd6036c734df033a` |
| Private subnet B (`ewb-b-private`) | `10.20.1.0/24` | `subnet-03e3a7d66d52ce3c3` |
| Internet Gateway (`ewb-igw-a`) | Attached to VPC A | `igw-0532ee0cdbca4b2d2` |
| Bastion (`ewb-bastion`) | Private `10.10.1.10`; public `15.206.159.22` | `i-07a7a12b96900c8b7` |
| App-A (`ewb-app-a`) | Private `10.10.2.10`; no public IP intended | `i-0541cfdd36d4faa0a` |
| App-B (`ewb-app-b`) | Private `10.20.1.10`; no public IP intended | `i-034f2ef1196e215a8` |
| VPC Peering (`ewb-a-b-peer`) | VPC A <-> VPC B; reported Active | `pcx-05244f4be3c4af375` |

See [`docs/resource-inventory.md`](docs/resource-inventory.md) for the expanded inventory and remaining resource IDs to record.

## Route tables and subnet associations

| Route table | Explicit subnet association | Destination | Target |
|---|---|---|---|
| `ewb-rt-a-public` | `ewb-a-public` (`10.10.1.0/24`) | `10.10.0.0/16` | `local` |
| | | `0.0.0.0/0` | `ewb-igw-a` (`igw-0532ee0cdbca4b2d2`) |
| | | `10.20.0.0/16` | `ewb-a-b-peer` (`pcx-05244f4be3c4af375`) |
| `ewb-rt-a-private` | `ewb-a-private` (`10.10.2.0/24`) | `10.10.0.0/16` | `local` |
| | | `10.20.0.0/16` | `ewb-a-b-peer` (`pcx-05244f4be3c4af375`) |
| `ewb-rt-b-private` | `ewb-b-private` (`10.20.1.0/24`) | `10.20.0.0/16` | `local` |
| | | `10.10.0.0/16` | `ewb-a-b-peer` (`pcx-05244f4be3c4af375`) |

Actual route-table IDs and screenshots of the Routes and Subnet associations tabs should be added to `docs/subnets-and-route-tables.md`.

## Peering and security

The updated report states the peering connection is Active, with requester VPC `vpc-069b48ebe177469f5` and accepter VPC `vpc-0fd6036c734df033a`. The inbound rules specified are documented in [`docs/security-groups.md`](docs/security-groups.md). Actual security-group IDs and console evidence are still needed.

## SSH administration
The report uses a local private key and SSH ProxyJump through the bastion. See [`03-bastion-host/ssh-config.example`](03-bastion-host/ssh-config.example). Never upload the real `.pem` key.

## Validation status
The report contains acceptance criteria, not terminal proof. The supplied workbook expects:
- Baseline App-A -> App-B ping before peering/routes: no replies.
- Forward and reverse ping after routes and security rules: 4 replies, 0% loss each.
- `ssh ewb-app-b` from the laptop: shell on App-B through the bastion.
- Controlled ICMP test: remove only App-B's inbound ICMP Echo Request rule sourced from `10.10.2.10/32`, verify failure, restore it, verify recovery.

**Actual outputs and screenshots have not been supplied in the updated report.** Add them under `screenshots/` and record them in `docs/connectivity-tests.md` before claiming these tests passed.

## Cleanup
The updated report describes a cleanup sequence but does not provide proof that cleanup has been completed. Record actual final states and billing review in `docs/cleanup-and-lessons.md`.

## Repository contents
- `docs/` - updated report and expanded implementation evidence documents.
- Numbered directories - implementation notes for each lab phase.
- `screenshots/` - add genuine AWS console and terminal evidence.
- `architecture/` - add/export the final architecture diagram.

## Author
Devesh Chak
