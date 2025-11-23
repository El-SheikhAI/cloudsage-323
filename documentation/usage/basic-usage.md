# Basic Usage - CloudSage Documentation

Welcome to CloudSage! This guide will help you start optimizing your cloud costs with basic workflows. 

## 1. Installation
Install the CloudSage CLI using pip:
```bash
pip install cloudsage-cli
```

Verify installation:
```bash
cloudsage --version
```

## 2. Initial Configuration
Connect your first cloud account:

```bash
cloudsage configure
```
Follow prompts to:
1. Select cloud provider (AWS/Azure/GCP)
2. Provide credentials (key/secret for AWS, service principal for Azure, etc.)
3. Name your configuration profile (e.g. "prod-aws-us-east")

CloudSage stores encrypted credentials locally using AES-256 encryption.

## 3. Running Your First Analysis
Scan resources across all connected regions:
```bash
cloudsage analyze --profile prod-aws-us-east
```

Typical first-run output:
```
Analyzing 4,372 resources across 7 AWS regions...
✅ Identified $12,380/month potential savings
📄 Full report generated: cloudsage-report-2023-08-15.html
```

## 4. Review Recommendations
View findings in either format:

**CLI Quick View**
```bash
cloudsage recommendations --summary
```

**Web Dashboard**
1. Upload report: 
```bash
cloudsage report upload cloudsage-report-2023-08-15.html
```
2. Access interactive dashboard at:
```
https://dashboard.cloudsage.ai/reports/2023-08-15
```

## 5. Apply Savings
Execute recommended actions:

```bash
cloudsage execute --recommendation-id R457 --dry-run  # Test first
cloudsage execute --recommendation-id R457 --confirm  # Apply changes
```

Common automatable actions:
- Right-sizing underutilized EC2 instances
- Deleting orphaned storage volumes
- Scheduling non-production resources

## 6. Continuous Monitoring
Set up daily scans:

```bash
cloudsage schedule --frequency daily --time "23:00"
```

Receive alerts via:
```bash
cloudsage alerts enable --channel email --address team@company.com
cloudsage alerts enable --channel slack --webhook YOUR_SLACK_URL
```

## Next Steps
You're now ready to:
1. [Connect additional cloud accounts](/documentation/advanced/multi-cloud)
2. [Set custom optimization rules](/documentation/advanced/custom-rules)
3. [Configure team access controls](/documentation/security/access-control)

## Need Help?
- Run `cloudsage help` for CLI reference
- Visit our [Support Portal](https://support.cloudsage.ai)
- Join community discussions on [Discord](https://discord.cloudsage.ai)