# Networking in AWS

#### In this module: ####
- VPC
- Subnets
- Gateways
- Network Security

## VPC

What is it?:
- A private network space in your AWS cloud.
- Can provide logical isolation for your workloads
  - ie. between development environments and production environments
- A framework for security
- IPv4 mandated, IPv6 if you want it
- Can create specific CIDR ranges for your resources to sit
- Provide strict access rules for in/outbound traffic

There is a hard limit of 5 VPCs per region per account.

####Use cases:####
One VPC:
- Small single applications managed by 1 person or a small team
- High performance computing
- Identity management

Most use cases will be best served with multiple VPCs:
- Single team or single organisations, such as managed service providers
- Limited teams, which make it easier to maintain standards and manage access
- Exception:
  - Governance and compliance standards may require greater workload isolation.
and multiple accounts:
- Large organisations that may have multiple IT teams
- Medium-sized organisations which anticipate large growth
  - Managing access and standards can be trickier in comples organisations

Private ranges can be allocated for IP addressing in your VPC.

### CIDR Example

0.0.0.0/0	= All IPs
10.22.33.44/32  = 10.22.33.44
10.22.33.0/24   = 10.22.33.*
10.22.0.0/16    = 10.22.*.*

## Subnets

Primary purpose of subnets is to determine what talks to the internet and what doesn't.
- Public vs Private vs Protected (for extreme privacy requirements)

Key attributes:
- Subnets are a subset of the VPCs CIDR block
- Subnet CIDR blocks cannot overlap
- Each subnet resides entirely in one AZ
- An AZ can contain multiple subnets

Public subnets:
- Include a routing table entry to an internet gateway to support in/outbound traffic to/from the public internet

Private subnets:
- Do not have a routing table entry to an internet gateway
- Are not directly accessible from the public internet
- Typically use a NAT gateway to support restricted, outbound public internet access.
  - NAT gateways can be used to make outbound calls to the general internet, for example to download stuff you need to run your server
  - (see below)

Recommendations:
- Larger subnets
- Public & private subnet minimum in each AZ.
- Make as much stuff private as possible

#### Route tables:
- Required to direct traffic between VPC resources
- Each VPC has a main route table
- You can also create custom route tables
- All subnets must have an associated route table

Best practice:
- Use custom route tables for each subnet

## Internet Gateways

They:
- Allow communication between instances in your VPC and the general internet
- Are horizontally scaled, redundant, and highly available by default
- Provide a target in your subnet route tables for internet-routable traffic
- Silently scaled - will just work

#### Nat Gateways:

They:
- Enable instances in the private subnet to initiate outbound traffic to the internet or other AWS services
- Prevent private instances from recieving inbound traffic from the general internet.
- Sit in a public subnet, then pass traffic to the private subnet

## Elastic Network Interfaces (ENIs)

It is:
- A virtual network interface that can be moved across EC2 instances
- In the same availability zone

This:
- Maintians Private IP, Elastic IP, and Mac address.

## Elastic IPs

These:
- Can be associated with an instaces or network interfaces
- Able to re-associate and direct traffic immediately
- Five allowed per AWS region (by standard)

## Security Groups

They are:
- Virtual firewalls, that control in/outbound traffic into AWS resources
- Traffic can be restricted by IP protocol, port, or IP address
- Rules are stateful

By default, they:
- Block all inbound traffic
- Allow all outbound traffic

Can daisy chain:
- Allowing access to a security group, only from another security group.
- As you have been doing Marcus.

## Network Access Control Lists (Network ACLs)

They are:
- Firewalls at the subnet boundary
- Will allow inbound and outbound traffic (default NACL in a VPC)
- Are stateless, requiring explicit rules for both in and outbound traffic

They:
- Don't do anything by default - have no rules
- To get function, you could block all 0.0.0.0/0 IN, then allow specific IPs.

## So... how do I get traffic into my VPC?

- Attach an internet gateway to your VPC
- Point your route tables to the internet gateway
- Make sure your instances have public/elastic IP addresses
- Ensure your NACLs and SGs allow the relevant traffic through




