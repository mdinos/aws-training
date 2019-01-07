# Adding compute

What we're using:
- EC2
- instance types/families
- EBS
- Compliance options

## EC2

What can it do?
- Web hosting
- Databases
- Auth
- Anything a server can do

VMs vs. Physical servers
- VMs are disposable:
  - data driven decisions
  - quick iteration
  - free to make mistakes
  - short feedback loops on mistakes

#### EC2 Instance sizes

EXAMPLE: m5.large
- m is the family name
- 5 is the generation number
- large is the size of the instance

#### EC2 Instance Types

Different types:
- On-demand instances
  - Pay for compute capacity per second (linux/ubuntu), or by the hour (other OS)
  - No long term commitment
  - No upfront payment
  - Elastic - scale up or down capacity depending on minute-by-minute demand

- Reserved instaces
  - Pre-pay for capacity - usually at a lesser price
  - Good for if you have a baseline requirement for your EC2 usage
  - Can be up to 75% off the on-demand price
  - 3 types:
    - Standard: ready state usage
    - Convertible: Able to change the attributes of the RI as long as the change results in the creation of RIs of equal or greater value
    - Schedule: launch in a time window of your choice, allowing you to match to capacity requirements
  - 1 or 3 year terms for RIs.

- Spot instances
  - Purchase unused EC2 capacity
  - Prices controlled by AWS based on supply and demand
  - Termination notice provided 2 minutes prior to termination
  - Spot blocks - Launch spot instances with a duration lasting 1 - 6 hours
  - Can save you a bit of money if the market is right.

#### EC2 tagging best practices

- Standardised, case sensitive formats.
- Implement automated tools to manage tags
- Too many is better than too few
- Easy to modify

#### Architectural configurations



#### AMIs

AMIs are essentially just the state in which your instance is launched.

## EBS

It is essentially a drive for ec2 which persists through terminations and shutdowns.

What problems does it solve?
- Applications might need block level storage
- It persists through ec2 shutdowns
- Instance storage is ephemeral, so you will probably need an ebs for this.

EBS is linked to only 1 instance at a time.

You can have SSDs or HDDs, with different kinds:
- General purpose SSD: pretty much fine for anything
- Provisioned IOPS SSD: Very high performance - pay for IOPS.
- Throughput optimized HDD: Low cost HDD volume for frequently accessed throughput intensive workloads.
- Cold HDD: Even lower cost HDD volume designed for less frequently accessed workloads.

## EFS (Elastic file system)

EFS for linux (NFSv4)
Shared across:
- AZ
- Region
- VPC
- Account

FSx for windows (NTFS)
Shared across:
- AZ



