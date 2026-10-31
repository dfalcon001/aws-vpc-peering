# proxyjump setup

Move the key to ~/.ssh/ewb-lab.pem in WSL, macOS or Linux. Run chmod 400 ~/.ssh/ewb-lab.pem. Create or edit ~/.ssh/config with the entries below. Keep the private IPs only if they match your instances.

LOCAL FILE / ~/.SSH/CONFIG
AWS ARCHITECT ASSOCIATE
Run all SSH commands on your laptop. ProxyJump uses the bastion as the connection path.

LOCAL FILE / ~/.SSH/CONFIG
*Host ewb-bastion*
    HostName 15.206.159.22
    User ec2-user
    IdentityFile ~/.ssh/ewb-lab.pem
    IdentitiesOnly yes
*Host ewb-app-a*
    HostName 10.10.2.10
    User ec2-user
    IdentityFile ~/.ssh/ewb-lab.pem
    IdentitiesOnly yes
    ProxyJump ewb-bastion
*Host ewb-app-b*
    HostName 10.20.1.10
    User ec2-user
    IdentityFile ~/.ssh/ewb-lab.pem
    IdentitiesOnly yes
    ProxyJump ewb-bastion

USE COMMANDS TO UBUNTU WSL TO CONFIGURE /.ssh/config
**mkdir -p ~/.ssh**
**chmod 600 ~/.ssh**
**chmod 400 ~/.ssh/ewb-lab.pem**
**nano ~/.ssh/config -> add the above code of ~/.ssh/config**

Test ssh ewb-bastion first. Use exit to return to your laptop, then run ssh ewb-app-a. Both should connect before
peering, using VPC A's local route. Verify the destination host before accepting a first-time host key prompt.
