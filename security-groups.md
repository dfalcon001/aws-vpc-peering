# Security Groups – Inbound Rules

List every security group used by the bastion, App-A, and App-B. Include protocol, port/range, source, and purpose. Record actual group IDs.

| Security group/name | SG ID | Type/protocol | Port | Source (CIDR or SG) |
|---|---|---|---|---|---|---|
| Bastion SG | sg-0aea8da1e6529b557 | SSH | 22 | 117.219.91.136/32 | 
| App-A SG | sg-07e1f8d002012033d | Custom ICMP - IPv4(Echo Request) SSH | N/A 22 | 10.20.1.10/32 10.10.1.10/32 |
| App-B SG | sg-0163248d847b1a05a | Custom ICMP - IPv4(Echo Request) SSH | N/A 22 | 10.10.2.10/32 10.10.1.10/32 |

Use least privilege. Do not publish rules that expose SSH or other services broadly unless explicitly required and approved for the lab.
