# Subnet CIDRs and Route Tables

Record all actual subnet CIDRs and the three route tables, including explicit and main subnet associations.

| Route table | Route table ID | VPC | Associated subnet(s) | Destination | Target | State |
|---|---|---|---|---|---|---|
| ewb-rt-a-public | rtb-0c55c61fc500b748f | vpc-069b48ebe177469f5/ewb-vpc-a | subnet-0a35f8f2e927d5a39/ewb-a-public | 0.0.0.0/0 10.10.0.0/16 10.20.0.0/16 | igw-0532ee0cdbca4b2d2/ewb-igw-a local pcx-05244f4be3c4af375/ewb-a-b-peer | Active |
| ewb-rt-a-private | rtb-0714de5f6dc05cd64 | vpc-069b48ebe177469f5/ewb-vpc-a | subnet-044129b0cb3bbfb91/ewb-a-private | | | |
| ewb-rt-b-private | rtb-02a33dcbb416d2209 | vpc-0fd6036c734df033a/ewb-vpc-b | subnet-03e3a7d66d52ce3c3/ewb-b-private | | | |

Attach screenshots showing each route table's Routes and Subnet associations tabs.
