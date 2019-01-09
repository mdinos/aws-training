# Microservices and Serverless Architectures

The problem:
- Your monolithic architecture is decoupled, individual comonents are managed by sepereate teams, which can lead to conflicts as teams change their components

In this doc:
- Building microservices
- Container services
- Going serverless

## Microservices

Microservices:
- Seperate out functionality into seperate independent services
- Communicate over well-defined APIs
- Are autonomous:
  - Each microservice/component can be deployed, developed, operated, and scaled without affecting other serivces
  - Any communication happens over APIs
- Are specialized:
  - Each service has a set of capabilitied and focuses on one thing essentially
  - If something is large and complicated, it should be seperated out into many microservices

## Containers

Are:
- Repeatable
- Self-contained execution environments
- Faster to wind up and down than virtual machines
- Share the host OS kernal

## Amazon Elastic Container Service (ECS)

It:
- Is a highly scalable, performant container management system
- Supports Docker
- Allows you to easily run applications on a managed cluster of EC2s
- Is extensible by using APIs
- Is compatible with Application Load Balancers for outward scaling

## Going Serverless

Can we use Lambdas instead of EC2s? Just use Lambdas like a microservice?
- Yeah.

Can either use cloudwatch events or anything that you put in an SNS or SQS to drive the lambda

#### Amazon API Gateway
- Allows you to create APIs that act as front doors for your applications
- Can handle up to hundreds of thousands of concurrent events
- Can handle workloads running on EC2, Lambda, or any web-app


