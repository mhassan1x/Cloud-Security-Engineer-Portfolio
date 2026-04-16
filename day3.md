# Day 3 – Cloud Networking (VPC, Subnets, Security Groups, NACLs, EC2)

## Concepts Learned.
- VPC with CIDR `10.0.0.0/16`
- Public subnet `10.0.1.0/24` with Internet Gateway and route table
- Security Group (stateful) allowed SSH and HTTP
- Launched EC2 instance (`t3.micro` in Sydney region) and connected via SSH

## Key Differences
- **Security Group**: Stateful, attached to instance, allow rules only.
- **NACL**: Stateless, attached to subnet, allow + deny rules.

## Lab Completed
- Created custom VPC with public subnet.
- Launched Amazon Linux 2023 EC2 instance.
- Connected via SSH from Windows PowerShell using `ssh -i key.pem ec2-user@<ip>`.
- Terminated instance to avoid charges.

## Next Steps
- Day 4: DDoS Protection, WAF, and Cloud Security Standards.
