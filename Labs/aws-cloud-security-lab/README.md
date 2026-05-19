# AWS Cloud Security Assessment Lab

## Overview

This project documents a hands-on AWS cloud security assessment lab built using intentionally vulnerable cloud infrastructure. The purpose of the lab was to gain practical experience deploying, auditing, monitoring, and troubleshooting AWS environments using industry-recognized cloud security tools.

The lab environment was deployed on AWS using Terraform and SadCloud, while ScoutSuite was used to perform cloud posture assessments against the vulnerable infrastructure. AWS CloudTrail was then used to monitor and review infrastructure activity and security-related events.

---

## Objectives

* Deploy intentionally vulnerable AWS infrastructure
* Perform AWS cloud security assessments
* Analyze IAM, S3, and network security misconfigurations
* Monitor AWS events using CloudTrail
* Gain hands-on experience with Terraform and cloud security tooling
* Improve troubleshooting and infrastructure debugging skills

---

## Tools & Technologies Used

| Tool                        | Purpose                                  |
| --------------------------- | ---------------------------------------- |
| Terraform                   | Infrastructure as Code deployment        |
| SadCloud                    | Vulnerable AWS infrastructure lab        |
| ScoutSuite                  | Cloud security posture assessment        |
| AWS CloudTrail              | Event logging and monitoring             |
| AWS EC2 Ubuntu              | Security workstation                     |
| Docker                      | Containerized tooling                    |
| Python Virtual Environments | Tool isolation and dependency management |

---

## Lab Workflow

```text
EC2 Ubuntu Instance
        ↓
Install AWS CLI, Terraform & Security Tools
        ↓
Deploy Vulnerable Infrastructure with SadCloud
        ↓
Run ScoutSuite Security Assessment
        ↓
Analyze Findings & Misconfigurations
        ↓
Monitor Events in CloudTrail
        ↓
Destroy Infrastructure to Prevent Costs
```

---

## Environment Setup

### 1. EC2 Deployment

An Ubuntu EC2 instance was launched in AWS and configured as the primary cloud security workstation.

### 2. Tool Installation

Installed:

* AWS CLI
* Terraform
* Docker
* Python virtual environments
* ScoutSuite
* Prowler
* Pacu

### 3. Vulnerable Infrastructure Deployment

Terraform was used with SadCloud modules to deploy intentionally insecure AWS resources for testing and assessment purposes.

### 4. Security Assessment

ScoutSuite was executed against the AWS environment to identify:

* Public S3 buckets
* IAM privilege issues
* Exposed network configurations
* Logging and monitoring weaknesses
* Public attack surfaces

### 5. Monitoring & Logging

AWS CloudTrail Event History was used to monitor:

* IAM policy modifications
* CloudFormation events
* S3 bucket policy changes
* Infrastructure provisioning activity
* Load balancer modifications

---

## Key Findings

The environment exposed several intentionally insecure configurations, including:

* Publicly accessible S3 configurations
* Weak IAM permissions
* Overly permissive security groups
* Logging gaps
* Publicly exposed resources

These findings provided practical insight into how cloud misconfigurations can increase organizational risk.

---

## Challenges Encountered

Several real-world deployment and troubleshooting challenges were encountered during the lab:

* Deprecated Terraform resources
* Unsupported AWS service versions
* Terraform provider compatibility issues
* Docker permission errors
* AWS IAM credential troubleshooting
* Tool compatibility limitations with modern AWS APIs

These troubleshooting experiences significantly improved practical cloud engineering and security skills.

---

## Lessons Learned

* Cloud security assessments require strong understanding of IAM, networking, and logging.
* Infrastructure-as-Code deployments often require version compatibility troubleshooting.
* AWS logging and monitoring are essential for visibility and incident analysis.
* Misconfigured cloud resources can significantly expand an organization's attack surface.
* Troubleshooting is a critical part of real-world cloud security operations.

---

## Screenshots

Add screenshots to the `/screenshots` folder:

* ScoutSuite dashboard
* CloudTrail event history
* Terraform deployment output
* Security findings
* AWS resource configurations

---

## Cleanup

After testing and assessments were completed, Terraform destroy operations were executed to remove deployed infrastructure and prevent unnecessary AWS costs.

---

## References

* ScoutSuite
* SadCloud
* Terraform
* AWS CloudTrail
* AWS IAM Documentation

---

## Disclaimer

This project was created strictly for educational and defensive security learning purposes within a controlled AWS environment.
