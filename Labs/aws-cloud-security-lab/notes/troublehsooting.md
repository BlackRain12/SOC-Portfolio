# Troubleshooting Notes

## Terraform Deployment Issues

### Problem

Several Terraform resources failed during deployment due to deprecated AWS configurations and unsupported service versions.

### Examples

* Unsupported EKS Kubernetes version
* Deprecated S3 ACL configurations
* RDS engine compatibility issues
* Deprecated Lightsail blueprint versions

### Resolution

* Updated Terraform provider versions
* Modified Terraform configuration files
* Adjusted AWS service configurations
* Ignored unsupported/deprecated resources when necessary

---

## Docker Permission Errors

### Problem

Docker commands returned:

```bash
permission denied while trying to connect to the docker API socket
```

### Resolution

Used:

```bash
sudo docker run ...
```

Alternatively, the Ubuntu user can be added to the Docker group:

```bash
sudo usermod -aG docker $USER
```

---

## AWS Credential Issues

### Problem

Cloud security tools failed to detect AWS credentials properly.

### Resolution

Reconfigured AWS CLI credentials using:

```bash
aws configure
```

Validated credentials using:

```bash
aws sts get-caller-identity
```

---

## ScoutSuite Report Loading Issue

### Problem

The generated ScoutSuite HTML report displayed only:

```text
Loading please wait...
```

### Resolution

The report required the full `scoutsuite-report` directory structure to function correctly.

The entire report folder was copied locally from the EC2 instance using SCP.

---

## SCP File Transfer Issues

### Problem

Initial SCP commands failed due to incorrect remote file paths.

### Resolution

Verified report location using:

```bash
find ~ -type f -name "*.html"
```

Then copied the correct directory structure locally.

---

## Pacu Identity Issues

### Problem

Pacu returned null values during `whoami` checks despite valid AWS credentials.

### Possible Causes

* Session initialization issues
* Credential caching problems
* Compatibility issues with modern AWS APIs

### Resolution Attempted

* Reconfigured AWS CLI credentials
* Restarted Pacu sessions
* Re-entered AWS keys manually
* Tested AWS access independently using AWS CLI

---

## Terraform Cleanup

### Problem

Certain resources did not fully destroy automatically.

### Resolution

Manually verified and removed remaining resources using AWS CLI:

* EC2 instances
* S3 buckets
* EKS clusters
* CloudFormation stacks
* Load balancers

---

## Key Takeaway

Troubleshooting cloud infrastructure and security tooling is an essential part of real-world cloud security operations. Many issues encountered in this lab reflected realistic operational and compatibility challenges faced in production environments.
