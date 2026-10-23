# ewb-aws-vpc-peering-project
AWS VPC Peering project demonstrating secure private communication between two VPCs using EC2 instances, route tables, security groups, and a bastion host on AWS.

# AWS VPC Peering Project

## Project Overview
This project demonstrates how to establish secure private communication between two Amazon Virtual Private Clouds (VPCs) using AWS VPC Peering. It includes VPC configuration, subnet creation, route tables, security groups, EC2 instances, and connectivity testing.

## Objectives
- Create and configure two AWS VPCs.
- Establish a VPC Peering connection.
- Configure routing between both VPCs.
- Secure EC2 instances using security groups.
- Access private EC2 instances through a bastion host.
- Test connectivity using ping and SSH.
- Troubleshoot network connectivity issues.

## AWS Architecture

### VPC A
- **VPC Name:** `ewb-vpc-a`
- **CIDR Block:** `10.10.0.0/16`
- **Public Subnet:** `10.10.1.0/24`
- **Private Subnet:** `10.10.2.0/24`
- **Bastion Host:** `ewb-bastion`
- **App Instance:** `ewb-app-a`
- **Internet Gateway:** `ewb-igw-a`

### VPC B
- **VPC Name:** `ewb-vpc-b`
- **CIDR Block:** `10.20.0.0/16`
- **Private Subnet:** `10.20.1.0/24`
- **App Instance:** `ewb-app-b`
- **Internet Gateway:** None

### VPC Peering
- **Connection Name:** `ewb-a-b-peer`
- **Purpose:** Enable private communication between VPC A and VPC B using private IP addresses.

## Technologies Used
- Amazon Web Services (AWS)
- Amazon VPC
- EC2 Instances
- VPC Peering
- Route Tables
- Security Groups
- Amazon Linux 2023
- SSH and ICMP (ping)
- macOS Terminal

## Implementation Steps
1. Create VPC A and VPC B with non-overlapping CIDR blocks.
2. Create the required public and private subnets.
3. Configure the internet gateway and public route table for VPC A.
4. Launch the bastion host and application EC2 instances.
5. Configure security groups to restrict SSH and ICMP traffic.
6. Create and accept the VPC Peering connection.
7. Add routes to both VPCs' route tables for communication through the peering connection.
8. Connect to private instances through the bastion host using SSH.
9. Test connectivity and troubleshoot any failures.

## Connectivity Testing
The following tests should be performed and documented with actual results:

| Test | Expected Result |
|---|---|
| Ping App-B before adding peering routes | Failure |
| Ping App-B after configuring routes and security rules | Success |
| Ping App-A from App-B | Success |
| SSH to App-B through the bastion host | Success |
| Verify App-A and App-B have no public IP addresses | Confirmed |
| Temporarily block ICMP traffic | Ping fails |
| Restore the ICMP rule | Ping succeeds |

*Note: These are expected results. Replace them with your actual results and screenshots after testing.*

## Security Considerations
- Allow SSH to the bastion host only from your current public IP address.
- Restrict SSH access to private instances to the bastion host's private IP.
- Allow only the required ICMP traffic between application instances.
- Do not expose SSH or ICMP to `0.0.0.0/0`.
- Keep private instances without public IP addresses.
- Never upload private SSH keys, passwords, access keys, or other secrets to GitHub.

## Key Learnings
- Learned how to configure AWS VPCs, subnets, and route tables.
- Understood how VPC Peering enables private communication between VPCs.
- Learned the importance of forward and return routes.
- Practiced secure SSH access through a bastion host.
- Learned to troubleshoot connectivity using ping and security-group rules.
- Understood the importance of AWS resource cleanup to avoid unnecessary costs.

## Project Screenshots
Add your screenshots to the `screenshots/` directory and link them here.

Examples:
- VPC configuration
- VPC Peering status showing **Active**
- Route table entries
- Security-group inbound rules
- Successful ping tests
- SSH connection through the bastion host
- Controlled failure and recovery test
- AWS resource cleanup

## Repository Structure

```text
aws-vpc-peering-project/
├── README.md
├── report/
│   └── EWB_VPC_Peering_Report.pdf
├── architecture/
│   └── architecture.png
└── screenshots/
    ├── vpc-configuration.png
    ├── peering-active.png
    ├── route-tables.png
    ├── ping-success.png
    └── ssh-test.png
```

## Cost Management
AWS resources may incur charges depending on account eligibility, region, resource type, and usage. Review AWS pricing before launching resources. Avoid creating a NAT Gateway unless required, and terminate instances and delete unused resources when testing is complete.

## Conclusion
This project demonstrates how AWS VPC Peering can connect two VPCs privately using appropriate routing and security configurations. It also highlights the importance of secure administration, connectivity testing, troubleshooting, and cost management.

## Author
**Name:** Sanyukta Chewale    
**Course:** EWB AWS Architect Associate    
**Project:** AWS VPC Peering  
**Region:** Asia Pacific (Mumbai) — `ap-south-1`

