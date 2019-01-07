# Mod 2 - The simplest architectures

## Storage

S3 Standard -> S3 Standard IA -> S3 One Zone IA -> Amazon Glacier (deep archive)

Quickest -> slowest access

Most expensive -> cheapest

IA -> "Infrequent access"

## S3

2 things mainly to know:
- object based storage - you have to reupload the file to change it
- accessed over http(s)

Has versioning.
Not necessarily within a VPC.

Good use cases:
- Write once - read lots
- spiky data access
- large number of users and diverse amounts of content
- growing data sets

Less than good use cases:
- block storage
- frequently changing data
- long term archival storage

Pay for:
- GB per month
- Transfer out to other regions or the internet
- http requests

Don't pay for:
- Transfer in to s3
- transfer out to ec2 in same region, or to cloudfront

## Amazon Glacier

Slightly longer term data storage:
- archival or backup storage
- very low cost, lower availability

Retrieving data:
- Expedited retrieval - 1 - 5 mins for less money
- Buld retrievals in 5-12 hours for much less money  

Lifecycle policies:
S3 lifecycle policies allow you to move data / objects based on their age, ie.
- Object (file) moved from s3 standard to s3 IA in 30 days;
- Object moved from s3 IA to amazon glacier in 60 days;
- Object deleted after 365 days.



