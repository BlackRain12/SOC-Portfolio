# deployment-notes.md

# Terraform Deployment Notes

## Overview

This document contains notes, observations, deployment procedures, and issues encountered while deploying the SadCloud vulnerable AWS infrastructure using Terraform.

The goal of the deployment was to create an intentionally insecure cloud environment for security assessment and cloud security learning purposes.

---

# Environment Information

| Component                | Details             |
| ------------------------ | ------------------- |
| Cloud Provider           | AWS                 |
| Region                   | us-east-1           |
| Operating System         | Ubuntu EC2 Instance |
| Infrastructure Tool      | Terraform           |
| Vulnerable Lab           | SadCloud            |
| Security Assessment Tool | ScoutSuite          |

---

# Initial EC2 Setup

An Ubuntu EC2 instance was created to serve as the cloud security workstation.

## Installed Components

### AWS CLI

```bash
sudo apt update
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```

### Terraform

```bash
wget https://releases.hashicorp.com/terraform/<VERSION>/terraform_<VERSION>_linux_amd64.zip
unzip terraform_<VERSION>_linux_amd64.zip
sudo mv terraform /usr/local/bin/
```

### Docker

```bash
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker
```

### Python Virtual Environments

```bash
sudo apt install python3-venv -y
```

---

# SadCloud Deployment

## Clone Repository

```bash
git clone https://github.com/nccgroup/sadcloud.git
cd sadcloud/sadcloud
```

---

# Terraform Initialization

Terraform providers and modules were initialized using:

```bash
terraform init
```

Initialization completed successfully after provider configuration adjustments.

---

# Terraform Configuration Changes

## Provider Version Compatibility

The original provider configuration caused compatibility issues with modern AWS services.

### Original Configuration

```hcl
terraform {
  required_version = ">= 1.0"
  required_providers {
    aws = ">= 2.34.0"
  }
}
```

### Updated Configuration

The provider version was modified to improve compatibility with current AWS APIs.

---

# Deployment Command

The environment was deployed using:

```bash
terraform apply --var="all_findings=true"
```

Terraform planned approximately 80+ resources for deployment.

---

# Deployment Issues Encountered

Several AWS services failed due to deprecated APIs, unsupported versions, or modern AWS restrictions.

---

## 1. EKS Deployment Failure

### Error

```text
unsupported Kubernetes version 1.14
```

### Cause

SadCloud referenced an outdated Kubernetes version no longer supported by AWS.

### Resolution

Updated the Kubernetes version manually within Terraform configuration files.

---

## 2. S3 ACL Issues

### Error

```text
Bucket cannot have ACLs set with ObjectOwnership's BucketOwnerEnforced setting
```

### Cause

Modern AWS S3 defaults enforce BucketOwnerEnforced ownership, conflicting with legacy ACL usage.

### Resolution

Ignored deprecated ACL configurations or adjusted S3 configuration logic.

---

## 3. RDS Deployment Compatibility Issues

### Error

```text
RDS does not support creating a DB instance with the following combination
```

### Cause

Deprecated instance types and unsupported database engine combinations.

### Resolution

Adjusted DB instance classes and engine versions.

---

## 4. Elasticsearch Policy Restrictions

### Error

```text
Apply a restrictive access policy to your domain
```

### Cause

Modern AWS Elasticsearch/OpenSearch services reject insecure policies.

### Resolution

Deployment partially skipped for unsupported insecure configurations.

---

## 5. Glacier API Deprecation

### Error

```text
This API is no longer supported for new accounts
```

### Cause

AWS Glacier APIs used by SadCloud are deprecated.

### Resolution

Resource excluded from deployment.

---

## 6. Lightsail Blueprint Deprecation

### Error

```text
The specified blueprint does not exist or is deprecated
```

### Cause

The referenced Lightsail image blueprint no longer exists.

### Resolution

Updated or skipped outdated blueprint configurations.

---

# Successful Deployment Components

Despite partial failures, several vulnerable resources deployed successfully, including:

* IAM policies
* S3 resources
* EC2 resources
* Load balancer components
* CloudTrail-related activity
* CloudFormation resources

These resources provided sufficient infrastructure for security assessment testing.

---

# ScoutSuite Assessment

ScoutSuite was executed successfully against the deployed AWS environment.

## Assessment Command

```bash
scout aws
```

The tool generated:

* HTML reports
* JavaScript findings files
* Cloud security posture summaries

---

# CloudTrail Monitoring

AWS CloudTrail Event History was used to monitor deployment activity.

Observed events included:

* IAM policy attachments
* S3 bucket policy changes
* CloudFormation stack creation
* ELB modifications
* SNS configuration changes

This provided visibility into Terraform-driven infrastructure actions.

---

# Cleanup Procedure

After testing was completed, Terraform destroy operations were executed to prevent ongoing AWS charges.

## Destroy Command

```bash
terraform destroy --var="all_findings=true" -auto-approve
```

---

# Manual Cleanup Verification

The following AWS services were checked manually after destruction:

## EC2

```bash
aws ec2 describe-instances
```

## RDS

```bash
aws rds describe-db-instances
```

## EKS

```bash
aws eks list-clusters
```

## S3

```bash
aws s3 ls
```

## CloudFormation

```bash
aws cloudformation list-stacks
```

Remaining resources were deleted manually if necessary.

---

# Key Deployment Takeaways

* Older Terraform labs may require modernization for current AWS environments.
* AWS frequently deprecates insecure or legacy configurations.
* Infrastructure-as-Code deployments require continuous compatibility maintenance.
* Logging and monitoring provide critical visibility during cloud deployments.
* Vulnerable lab environments should always be destroyed after testing to prevent unnecessary cost and exposure.

---

# Final Notes

This deployment provided practical hands-on experience with:

* AWS infrastructure deployment
* Terraform troubleshooting
* Cloud security tooling
* Cloud posture assessment
* AWS monitoring and auditing
* Real-world cloud compatibility issues

The project significantly improved operational cloud security and troubleshooting skills.
