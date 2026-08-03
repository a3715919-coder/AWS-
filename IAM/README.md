# AWS IAM (Identity and Access Management)

## WHAT IS A IAM ?

IAM (Identity and Access Management) is an AWS service used to securely manage access to AWS resources. It allows us to create users, groups, roles, and policies. Using IAM, we can control who can access AWS resources and what actions they are allowed to perform. IAM follows the principle of least privilege and supports features like MFA, temporary credentials through roles, permission management.



It helps answer two questions:
- **Who can access AWS?** (Authentication)
- **What can they do?** (Authorization)

---

# IAM User

An IAM User is an identity created for a single person or application.

A user can have:
- Username
- Password (for AWS Console)
- Access Keys (for CLI/API)

### Example

- Abhishek
- Rohit
- Shubham
- Roshan

Each person has their own IAM User account.

---

# IAM Group

An IAM Group is a collection of IAM Users.

Instead of giving permissions to each user one by one, we assign permissions to the group.

### Example

Developers Group

- Rohit
- Aman

If the Developers group has EC2 access, then all users in that group automatically get EC2 access.

**Benefits**
- Easy to manage users
- Same permissions for multiple users
- Saves time

---

# IAM Role

An IAM Role is an identity that provides **temporary permissions**.

A role does not have:
- Username
- Password
- Permanent Access Keys


Example:

EC2
↓
IAM Role
↓
S3 Bucket

The EC2 instance assumes the role and gets temporary credentials to access S3.

---

# User vs Group vs Role

| Feature | User | Group | Role |
|---------|------|-------|------|
| Used for | One person/application | Multiple users | Temporary access |
| Login | Yes | No | No |
| Password | Yes | No | No |
| Access Keys | Yes | No | Temporary credentials |
| Permissions | Directly or through a group | Shared by users | Available after assuming the role |

---

# Summary

- **IAM** → Manages access to AWS resources.
- **User** → Identity for one person or application.
- **Group** → Collection of users with the same permissions.
- **Role** → Temporary permissions for AWS services, users, or AWS accounts.

---

# IAM Policy

An IAM Policy is a JSON document that defines **what actions are allowed or denied** on AWS resources.

Policies are attached to:
- Users
- Groups
- Roles

A policy answers these questions:
- Which action is allowed?
- On which resource?
- Is it Allow or Deny?

### Example Policy

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:ListBucket",
      "Resource": "*"
    }
  ]
}
```
# Common IAM JSON Elements

| Element | Meaning |
|----------|---------|
| Version | Policy language version |
| Statement | Permission rules |
| Effect | Allow or Deny |
| Action | AWS API action |
| Resource | Target AWS resource |
| Condition | Optional conditions for access |

---


# IAM Policy Types

## 1. AWS Managed Policy

- Created and managed by AWS.
- Ready to use.
- Can be attached to multiple users, groups, and roles.

Example:
- AmazonS3ReadOnlyAccess
- AmazonEC2FullAccess

---

## 2. Customer Managed Policy

- Created by you.
- You control the permissions.
- Can be reused for multiple users, groups, and roles.

---

## 3. Inline Policy

- Attached to only one user, group, or role.
- Cannot be shared with others.
- Deleted automatically when the identity is deleted.

---

# IAM Tags

Tags are **key-value pairs** used to organize AWS resources and IAM identities.


### Example

| Key | Value |
|------|-------|
| Department | IT |
| Project | Login-App |
| Environment | Production |
| Owner | Abhishek |



---

## IAM Policy
- Written in JSON format.
- Defines permissions.
- Can Allow or Deny actions.
- Attached to Users, Groups, or Roles.

## Tags
- Key-value pairs.
- Used for organization and management.
- Help with billing, automation, and access control.

## JSON Policy Keywords
- Version
- Statement
- Effect
- Action
- Resource
- Condition