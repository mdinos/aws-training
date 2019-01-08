# Identity and Access Management (IAM)

Overview:
- IAM users, groups, and roles
- Federated Identity Management
- Amazon Cognito
- AWS Organisations

## Root User

This account has full access to all AWS services and resources:
- Billing
- Personal data
- All architecture and components

It cannot be limited in its power.

Safer way to administrate:
- Root user creates IAM user
- Lock away root user creds in a safe
- Use IAM admin user

#### Key IAM Principles:
- IAM Users
  - IAM users are not seperate accounts, they are users within your account
  - Each of which has their own creds
  - Authorized to perform specific actions based on their permissions
  - No default permissions
  - Access to the AWS Management Console or CLI must be granted explicitly
- Federated Users
- IAM Role
- Identity provider

Permissions:
- Have to make a policy that when attached to an identity or resource, defines its permissions
- Evaluated at the time of request
- Deny rules trump allow rules:
  - Something must not be explicitly denied
  - Then it must be specifically allowed

