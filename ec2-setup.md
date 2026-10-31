# ec2 setup

Add the steps you performed, actual configuration values, and links to genuine evidence screenshots. Mark any uncompleted step clearly.

## 1 Create and store your key pair
  In EC2, create an RSA key pair named ewb-lab and download the .pem file. Store it on your own laptop.
  Use it for all three instances. Never upload or paste the private key onto an EC2 instance.
## 2 Use a consistent instance configuration
  Select Amazon Linux 2023 and an instructor-approved small x86 instance type, such as t3.micro.
  Check the displayed price and your account credits. Keep the root disk small and enable delete-on-termination for that lab volume.
|Instance | Network settings | Security group |
|----|----|----|
|ewb-bastion | VPC A/ewb-a-public Private IP: 10.10.1.10 Auto-assign public IP: Enable | ewb-sg-bastion |
| ewb-app-a | VPC A/ewb-a-private Private IP: 10.10.2.10 Auto-assign public IP: Disable | ewb-sg-app-a |
| ewb-app-b | VPC B/ewb-b-private Private IP: 10.20.1.10 Auto-assign public IP: Disable | ewb-sg-app-b |

Under Network settings > Edit, select the VPC and subnet. In the advanced network interface settings, set
the primary private IPv4 to the address above. Choose the existing security group for that VPC. Launch each
instance and wait for it to run and pass its status checks
