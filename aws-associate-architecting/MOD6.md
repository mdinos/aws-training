# Networking in AWS (part 2)

#### Recap:
- NAT gateways allow outbound traffic from a private subnet to the general internet
- S3 sits outside the VPC

#### What are we looking at here?

Application requirements that include a need for:
- A large user base
- Variable loads
- AZ level failures

Overview:
- Connecting networks
- VPC endpoints
- Load balancing
- High availability

## Amazon VPN

Establish private connects between an Amazon VPC and another network.

One way to do it:
- Use a VPN connection between your VPCs virtual gateway and your data center
- This can also be configured to allow multiple datacentres to connect to the VPC VGW (Virtual Gateway)

## Connecting VPCs

You might need to transfer data between two or more VPCs.

#### VPC peering:

Using VPC peering, instances can communicate across a peering connection as if they were in the same network.

Stuff to know:
- Uses private IP addresses
- Only one peering resource between any 2 VPCs
- Can be established between different AWS accounts
- Transitive peering relationships are not supported

Caveats:
- IP spaces mustn't overlap
- Direct connections only:
  - If VPCs A and B are connected, and B and C are connected
  - You must have some kind of relay node on B in order to send from A to C
  - Obviously you could just have a connection from A to C in the first place

Cool stuff:
- No internet gateway or virtual gateway is required
- Highly available connections, not a single point of failure
- No bandwidth bottlenecks
- Traffic always stays on the global AWS backbone network

Best practices:
- No overlapping CIDR blocks in private IP addresses
- Only connect essential stuff
- Make sure your solution is scalable

Transit gateways:
- New cool version of VPC peering
- up to 5000 VPCs connects and on premises environments with a single gateway
- Hub for all traffic to flow through

## VPC Endpoints

These privately connect your EC2 instances to services outside your VPC, without leaving AWS.

These:
- Do not require traversal over the internet
- Must be in the same region
- Are horizontally scaled, redundant, and highly available

## Load balancing

ELBs:
- Use HTTP/S TCP/SSL protocols
- Can be external or internal facing
- Each load balancer has a DNS name
- Recognizes and responds to unhealthy instances

Application LB:
- Takes HTTP/S traffic and balances over nodes
- Flexible application management
- Operates at the request level (7)
- Can assign different routes based on Path.
- Can assign different routes based on source Host.

Network LB:
- Takes TCP traffic and balances over nodes
- Extreme performance and static IP for your application
- Operates at the connection level (4)

Why LBs are so great:
- High availability
- Health check response
- Security features (make use of stuff like security groups)
- TLS Termination

Connection draining:
- For if you need to remove an instance from your production fleet, but don't want to affect anything
- Can enable connection draining on a LB, any requests will finish before disconnection

## Route 53

Stuff:
- DNS translates domain names into IP addresses
- Able to purchase and manage domain names and automagically configure DNS settings
- Provides tools for flexible, high-performance, highly available architectures on AWS
- Provides DNS health checks - example make HTTP requests to ensure health

Routing options:
- Round robin
  - Simple
  - Weighted
- Latency based routing
- Health check and DNS failover
- Geolocation routing
- Geoproximity routing with traffic biasing
- Multi-value answers



