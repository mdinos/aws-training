# Elasticity, Monitoring, and Scaling

What are we looking at:
- "Your organization is experiencing extreme growth, and your architecture needs to handle significant changes in capacity

#### High availability factors:
- Fault tolerent: built in redundancy of components
- Scalable: can accomodate growth without changing design
- Recoverable: solid restoring failsafes after catastrophic events

## Elasticity:

Inelasticity:
- Pay for resources up front and hope they cover demand, or
- Too many resources, wasting money, burning power

Elasticity: 
- Time based
  - Turning off resources when they aren't being used
- Volume based
  - Matching scale to intensity of your demand

## Monitoring:

Reasons for doing so:
- Operational health
- Resource utilization
- Application performance
- Security auditing

To understand cost, cost explorer exists:
- Generates reports
- 13 months of data history
- Provides future estimates
- See patterns in spending

## Cloudwatch

Cloudwatch:
- Collects and tracks metrics for your resources
- Enables you to create alarms and send notifications
- Can trigger changes in capacity in a resource, based on rules you set

Cloudwatch Metrics:
- Metrics are data about the performance of your systems
- Kept for 15 months

Cloudwatch Logs:
- Allows you to monitor, store and access log files from AWS services
- ie. VPC flow logs, ec2 log files

Cloudwatch Alarms:
- Can configure actions for different states of AWS resources
- Can do stuff like sending notifications, or adding another EC2 to handle additional load

Cloudwatch Events:
- Basicly anything that happens on AWS is an event
- Any kind of state change, and API call, any new service starting up

Cloudwatch Rules:
- A rule matches incoming events, and routes them to targets for processing
- Not processed in a particular order
- JSON

Cloudwatch Targets:
- These are things that can act on events that have happened
- ie. a lambda might be a target if it's fired after an event happens

#### VPC flow logs

These:
- Capture traffic flow details in your VPC
- Accepted, rejected, or all traffic
- Can be enabled for VPCs, subnets, and ENIs
- Logs published to Cloudwatch logs

## Auto Scaling for Elasticity

Auto scaling:
- Launches or terminates instances based on specific conditions
- Automatically registers new instances with load balancers when specified
- Works across AZs

How?:
- Scheduled
  - Based on time of day
  - Can change minimum and maximum instances in ASG
  - ie. removing dev instances at night
- Dynamic
  - General use case
  - ie. scaling based on CPU utilization of other instaces
- Predictive
  - Uses machine learning to figure out when new instances will be needed

General principles:
- Might need to combine multiple types of autoscaling
- Scale out early and fast, then scale in slowly
- Use lifecycle hooks

