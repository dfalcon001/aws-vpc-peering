# ProxyJump Setup

Move the key to ~/.ssh/ewb-lab.pem in WSL, macOS or Linux. Run chmod 400 ~/.ssh/ewb-lab.pem. Create or edit ~/.ssh/config with the entries below. Keep the private IPs only if they match your instances.

LOCAL FILE / ~/.SSH/CONFIG
AWS ARCHITECT ASSOCIATE
Run all SSH commands on your laptop. ProxyJump uses the bastion as the connection path.

USE COMMANDS TO UBUNTU WSL TO CONFIGURE /.ssh/config
**mkdir -p ~/.ssh**
**chmod 600 ~/.ssh**
**chmod 400 ~/.ssh/ewb-lab.pem**
**nano ~/.ssh/config -> add the text code of ~/.ssh/config**

Test ssh ewb-bastion first. Use exit to return to your laptop, then run ssh ewb-app-a. Both should connect before
peering, using VPC A's local route. Verify the destination host before accepting a first-time host key prompt.
