# Automation

Infrastructure as Code! Whoop:
- Automating infrastructure
- Automating deployment

#### Manual process:
- It kinda sucks still
- Doesn't scale well
- No version control
- Lack of audit trails
- Inconsistent data management
- It's pretty risky
- Just automate it (whoop terraform)

## AWS CloudFormation

It is:
- A common language which you can use to describe your AWS infrastructure
- Creates and builds those described resources in an automated manner

Templates:
- JSON or YAML
- You can store it in a repo for VC

Benefits:
- Repeatable
- Reusable
- Iterable

Conditional:
- ie. If environment == development, could reduce size to one AZ to save $$

#### AWS Quick Start
- You can start off with cloudformation templates which provide a base infrastructure for you to start with
- Split by use case