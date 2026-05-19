# Lessons Learned

## 1. Cloud Security Requires Both Security and Infrastructure Skills

This project reinforced that cloud security is closely tied to infrastructure engineering. Successfully deploying and assessing AWS environments required understanding:

* IAM
* Networking
* Terraform
* AWS services
* Logging and monitoring

---

## 2. Troubleshooting is a Major Part of Security Work

Many tools and Terraform modules encountered compatibility issues due to AWS API changes and deprecated services. Troubleshooting became one of the most valuable learning experiences during the project.

Examples included:

* Unsupported EKS versions
* Deprecated S3 ACL configurations
* Terraform provider compatibility issues
* Docker permission errors

---

## 3. Misconfigurations Create Large Attack Surfaces

The ScoutSuite assessment demonstrated how simple cloud misconfigurations can expose environments to risk.

Examples:

* Public S3 buckets
* Weak IAM policies
* Open security groups
* Missing logging controls

This highlighted the importance of:

* least privilege
* secure defaults
* continuous monitoring

---

## 4. Logging and Monitoring Are Critical

Using AWS CloudTrail provided visibility into:

* Infrastructure changes
* IAM policy updates
* Terraform deployment activity
* Resource modifications

This demonstrated how logging supports:

* auditing
* incident response
* threat detection
* accountability

---

## 5. Cloud Security Tools Have Strengths and Limitations

Different tools served different purposes:

* ScoutSuite performed effective posture assessment
* Prowler focused on auditing and compliance
* Pacu required more troubleshooting and compatibility work

This showed the importance of selecting the right tool for the right task.

---

## 6. Infrastructure Cleanup Is Essential

Deliberately vulnerable cloud environments can quickly generate costs and security risks if left running.

Terraform destroy operations and manual AWS checks became an important final step in responsible cloud lab management.

---

## 7. Hands-On Labs Accelerate Learning

Deploying and testing insecure infrastructure provided much deeper understanding than theory alone. Working directly with AWS services, Terraform, and security tools significantly improved practical cloud security skills.
