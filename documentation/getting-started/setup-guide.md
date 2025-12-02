# CloudSage Setup Guide

Welcome to CloudSage! Let's get your environment configured so you can start optimizing cloud costs across AWS, Azure, and GCP. This guide takes **<10 minutes** to complete.

## Prerequisites
Before you begin, ensure you have:
- **User accounts** with Admin permissions in:
  - AWS IAM
  - Azure Active Directory
  - Google Cloud IAM
- **Node.js v18+** installed (for CLI operations)
- **Network access** to cloud provider APIs

---

## 1. Install CloudSage

```bash
npm install -g cloudsage-cli
```

Or via Docker:

```bash
docker pull cloudsage/agent:stable
```

---

## 2. Configure Cloud Providers

### AWS Setup
1. Create IAM Policy:
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "ce:GetCostAndUsage",
        "ec2:DescribeInstances",
        "rds:DescribeDBInstances"
      ],
      "Resource": "*"
    }
  ]
}
```
2. Attach policy to IAM user/role  
3. Set environment variables:
```bash
export AWS_ACCESS_KEY_ID="your_access_key"
export AWS_SECRET_ACCESS_KEY="your_secret_key"
export AWS_REGION="your_primary_region"
```

### Azure Setup
1. Create Service Principal:
```bash
az ad sp create-for-rbac --name CloudSageServicePrincipal
```
2. Grant **Cost Management Reader** and **Reader** roles  
3. Set environment variables:
```bash
export AZURE_CLIENT_ID="appId"
export AZURE_CLIENT_SECRET="password"
export AZURE_TENANT_ID="tenant"
```

### GCP Setup
1. Enable APIs:
   - Cloud Billing API
   - Compute Engine API
2. Create Service Account with **Billing Account Viewer** and **Compute Viewer** roles  
3. Set environment variables:
```bash
export GOOGLE_APPLICATION_CREDENTIALS="path/to/service-account-key.json"
```

---

## 3. Initialize Configuration

Create `cloudsage-config.yaml`:

```yaml
# Basic Configuration
environment: production
monitored_services:
  - ec2
  - vm
  - cloud-sql
  - kubernetes_engine

# Analysis Preferences
cost_savings:
  weekly_report: true
  auto_apply_threshold: 25%  # Apply recommendations saving ≥25%

# Optional: Resource Exclusions
exclusions:
  - tag:env=production
  - project_id:critical-project-123
```

---

## 4. Verify Connections

Run diagnostic check:

```bash
cloudsage diagnose --full
```

Expected output:
```
[✓] AWS Connection Valid (us-east-1)
[✓] Azure Connection Valid (eastus)
[✓] GCP Connection Valid (us-central1)
[✓] Configuration Valid
[✓] Permission Checks Passed
```

---

## 5. Start Analysis

Run initial cost assessment:

```bash
cloudsage analyze --full-scan
```

---

## First-Time Optimization

After setup completes (usually 2-4 hours for initial scan):

1. View recommendations:
```bash
cloudsage recommendations list
```
2. Apply suggestions:
```bash
cloudsage optimize apply --all-safe
```

---

## What's Next?
- [Schedule daily scans](https://docs.cloudsage/scheduling)
- [Configure Slack/Teams alerts](https://docs.cloudsage/integrations)
- [Explore API integration](https://docs.cloudsage/api-reference)

Need help? Contact support@cloudsage.com or join our [community forum](https://forum.cloudsage.com).

> You're all set! CloudSage typically identifies 15-40% savings in the first week. Watch your `savings` dashboard evolve!