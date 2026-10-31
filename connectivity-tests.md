# Connectivity Test Evidence

Paste actual terminal output and reference screenshot filenames. Do not mark a test successful based only on the expected lab outcome.

## Baseline: before peering/routes
Command: `ping -c 4 <App-B-private-IP>` from App-A.
Actual output: `[PASTE OUTPUT]`
Evidence: `[FILENAME]`

## Forward ping: App-A to App-B
Command: `ping -c 4 <App-B-private-IP>` from App-A.
Actual output: `[PASTE OUTPUT]`
Evidence: `[FILENAME]`

## Reverse ping: App-B to App-A
Command: `ping -c 4 <App-A-private-IP>` from App-B.
Actual output: `[PASTE OUTPUT]`
Evidence: `[FILENAME]`

## App-B SSH proof
From laptop, connect via the configured bastion/ProxyJump. Record the exact command and a terminal screenshot showing the remote host identity (do not show secrets).
Command: `[PASTE COMMAND]`
Actual proof: `[PASTE OUTPUT]`
Evidence: `[FILENAME]`

## Controlled ICMP failure and recovery
1. Record a successful ping.
2. Temporarily remove/deny the relevant ICMP permission in the intended security group.
3. Repeat ping and capture the failure.
4. Restore the original ICMP rule.
5. Repeat ping and capture recovery.

Failure output/evidence: `[FILL IN]`
Recovery output/evidence: `[FILL IN]`

Explanation: Security groups are stateful virtual firewalls. If the relevant ICMP traffic is not permitted, echo requests/replies are blocked. Restoring the required ICMP rule allows the test to succeed again, assuming routes and network ACLs also permit the traffic.
