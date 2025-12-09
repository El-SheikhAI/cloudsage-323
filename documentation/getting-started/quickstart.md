# CloudSage Quickstart Guide

Welcome to CloudSage! This guide will get you up and running with our AI-driven cloud cost optimization tool in less than 5 minutes.

## Prerequisites
- An active AWS, Azure, or Google Cloud Platform account
- Administrator access or equivalent permissions to create service principals/roles
- Node.js v16+ installed (for CLI-based installations)

## Installation
### Step 1: Install the CloudSage CLI
```bash
npm install -g cloudsage-cli
```

### Step 2: Verify Installation
```bash
cloudsage --version
# Should return: cloudsage-cli/1.0.0
```

## Configuration

### AWS Setup
1. Create an IAM user with:
   - Cost Explorer read access
   - EC2, RDS, S3 read-only permissions
2. Run configuration:
```bash
cloudsage config aws \
  --access-key-id YOUR_AWS_ACCESS_KEY \
  --secret-access-key YOUR_AWS_SECRET_KEY \
  --region YOUR_PRIMARY_REGION
```

### Azure Setup
1. Create a Service Principal with:
   - Cost Management Reader role
2. Run configuration:
```bash
cloudsage config azure \
  --tenant-id YOUR_TENANT_ID \
  --client-id YOUR_CLIENT_ID \
  --client-secret YOUR_CLIENT_SECRET \
  --subscription-id YOUR_SUBSCRIPTION_ID
```

### Google Cloud Setup
1. Create a Service Account with:
   - Billing Viewer role (roles/billing.viewer)
   - Compute Viewer role (roles/compute.viewer)
2. Run configuration:
```bash
cloudsage config gcp \
  --project-id YOUR_PROJECT_ID \
  --credentials-file path/to/service-account-key.json
```

## Basic Usage

### Run Initial Analysis
```bash
cloudsage analyze --time-range=last-7-days
```

### Understanding Your Report
CloudSage will output:
1. **Current Spend Overview**: Breakdown by service/resource
2. **Immediate Savings**: Identified waste with fix commands
3. **Strategic Recommendations**: Architecture improvements
4. **Predicted Savings**: 30-day forecast with optimizations

Example output snippet:
```markdown
## Immediate Savings Opportunities
- [AWS] Unattached EBS Volumes: $127/mo saved
  `aws ec2 delete-volume --volume-id vol-0abcdef12345`
- [GCP] Idle VM Instances: $489/mo saved
  `gcloud compute instances stop instance-name`
```

## Next Steps
- [Schedule Regular Analyses](automation-guide.md)
- [Configure Savings Auto-Apply](auto-remediation.md)
- [Explore Advanced Reporting](dashboard-guide.md)

Need help? Join our [Community Slack](https://cloudsage.io/slack) or email support@cloudsage.io