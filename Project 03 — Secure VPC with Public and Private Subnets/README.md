# Project 03 — Secure VPC with Public and Private Subnets

## Overview

A hands-on AWS networking project that demonstrates how to design a secure Amazon VPC containing both public and private subnets.

The project deploys one EC2 instance in each subnet, configures an Internet Gateway for public-subnet connectivity, and uses a NAT Gateway to provide internet access for the private subnet.

## Architecture

```text
                         Internet
                            │
                            ▼
                    Internet Gateway
                            │
             ┌──────────────┴──────────────┐
             │            VPC              │
             │                             │
             │   Public Subnet             │
             │        │                    │
             │   Public EC2                │
             │                             │
             │   Private Subnet            │
             │        │                    │
             │   Private EC2               │
             │        │                    │
             │   NAT Gateway               │
             │        │                    │
             └────────┼────────────────────┘
                      │
                      └────── Internet Gateway
```

## AWS Services Used

- Amazon VPC
- Amazon EC2
- Internet Gateway
- NAT Gateway
- Route Tables
- Security Groups

## Project Objective

The objective is to design and demonstrate a secure VPC architecture containing:

- One public subnet
- One private subnet
- One EC2 instance in the public subnet
- One EC2 instance in the private subnet
- An Internet Gateway for public-subnet internet access
- A NAT Gateway for private-subnet internet access
- Appropriate route tables
- Security group rules demonstrating the intended connectivity and security behavior

## Project Workflow

1. Created an Amazon VPC.
2. Created a public subnet.
3. Created a private subnet.
4. Configured an Internet Gateway and attached it to the VPC.
5. Created a NAT Gateway for private-subnet internet access.
6. Configured public and private route tables.
7. Deployed one EC2 instance in the public subnet.
8. Deployed one EC2 instance in the private subnet.
9. Configured security groups for the instances.
10. Tested connectivity and internet access.
11. Verified the security behavior of the public and private instances.

## Network Components

### VPC

The VPC provides the isolated network environment containing the public and private subnets.

### Public Subnet

The public subnet contains the public EC2 instance and uses a route through the Internet Gateway for internet connectivity.

### Private Subnet

The private subnet contains the private EC2 instance.

The private subnet does not directly route through the Internet Gateway. Outbound internet access is provided through the NAT Gateway.

### Internet Gateway

The Internet Gateway provides internet connectivity for resources in the public subnet.

### NAT Gateway

The NAT Gateway provides outbound internet access for the private subnet while keeping the private EC2 instance from requiring direct inbound internet access.

### Route Tables

Separate route tables are configured for the public and private subnets.

The public route table directs internet-bound traffic through the Internet Gateway.

The private route table directs internet-bound traffic through the NAT Gateway.

### Security Groups

Security group rules are configured to demonstrate the intended security behavior between the public and private EC2 instances.

## Testing

The project was tested by verifying:

1. Public subnet connectivity.
2. Private subnet connectivity.
3. Internet access from the private subnet through the NAT Gateway.
4. Security group behavior for the public and private instances.

Expected network flow:

```text
Public EC2
    │
    ▼
Internet Gateway
    │
    ▼
Internet
```

```text
Private EC2
    │
    ▼
NAT Gateway
    │
    ▼
Internet Gateway
    │
    ▼
Internet
```

## Key Learning Outcomes

- Understanding Amazon VPC architecture
- Creating public and private subnets
- Configuring Internet Gateways
- Configuring NAT Gateways
- Working with VPC route tables
- Deploying EC2 instances into different subnets
- Configuring security groups
- Understanding public versus private network connectivity
- Testing private-subnet internet access through NAT

## Cleanup

After completing the testing, the AWS resources used for the project were cleaned up to avoid unnecessary AWS charges.

## Project Status

**Completed**
