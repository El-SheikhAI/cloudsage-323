# Installing CloudSage

Welcome to CloudSage! This guide will help you install our cloud cost optimization tool in under 5 minutes.

## Prerequisites

Before installation:
- Supported operating systems: Linux (Ubuntu 20.04+), macOS (Catalina 10.15+), Windows 10/11 (WSL2 recommended)
- Python 3.8 or newer (`python3 --version`)
- `pip` package manager (comes with Python 3.4+)
- Cloud CLI tools for services you use:
  - [AWS CLI](https://aws.amazon.com/cli/)
  - [Azure CLI](https://learn.microsoft.com/en-us/cli/azure/)
  - [Google Cloud CLI](https://cloud.google.com/sdk/)
- Valid credentials for your cloud provider(s)

## Installation Method

### Standard Install (Recommended)

```bash
pip install cloudsage
```

**Pro Tip:** Create a virtual environment first:
```bash
python3 -m venv sage-env
source sage-env/bin/activate  # Linux/macOS
# sage-env\Scripts\activate   # Windows
pip install cloudsage
```

Verify your installation:
```bash
cloudsage --version
# Expected output: CloudSage vX.X.X
```

## Configuration

After installation, configure your cloud credentials:

1. Create configuration file (`~/.cloudsage/config.yaml`):
```yaml
default_provider: aws  # aws|azure|gcp

aws:
  access_key_id: YOUR_AWS_ACCESS_KEY
  secret_access_key: YOUR_AWS_SECRET_KEY
  region: us-east-1

azure:
  client_id: YOUR_AZURE_CLIENT_ID
  client_secret: YOUR_AZURE_SECRET
  tenant_id: YOUR_AZURE_TENANT_ID

gcp:
  project_id: YOUR_GCP_PROJECT_ID
  credentials_file: /path/to/service-account.json
```

2. Alternatively set environment variables:
```bash
# AWS
export AWS_ACCESS_KEY_ID="YOUR_ACCESS_KEY"
export AWS_SECRET_ACCESS_KEY="YOUR_SECRET_KEY"

# Azure
export AZURE_CLIENT_ID="YOUR_CLIENT_ID"
export AZURE_CLIENT_SECRET="YOUR_CLIENT_SECRET"
export AZURE_TENANT_ID="YOUR_TENANT_ID"

# GCP
export GOOGLE_APPLICATION_CREDENTIALS="/path/to/service-account.json"
```

⚠️ **Security Note:** Never commit credentials to version control. Use secret managers for production environments.

## Running CloudSage

Start with these basic commands:

```bash
# Generate initial infrastructure analysis
cloudsage analyze --provider aws

# Get savings recommendations
cloudsage recommend --output html

# Apply optimization changes (interactive mode)
cloudsage apply --dry-run  # Safety check first!
cloudsage apply --confirm
```

### Common Flags
- `--provider`: Limit to specific cloud (aws|azure|gcp)
- `--region`: Target specific regions
- `--output`: Format results (json|html|csv)
- `--dry-run`: Test changes without applying

## Troubleshooting

Common issues and solutions:

1. **Connection Errors**
   ```bash
   ERROR: Could not validate [AWS] credentials
   ```
   Verify credentials with:
   ```bash
   aws sts get-caller-identity  # AWS
   az account show              # Azure
   gcloud auth list             # GCP
   ```

2. **Missing Dependencies**
   ```bash
   ImportError: No module named 'boto3'
   ```
   Install missing requirements:
   ```bash
   pip install cloudsage[aws]  # AWS support
   pip install cloudsage[azure] # Azure support
   pip install cloudsage[gcp]  # GCP support
   ```

3. **Permission Errors**
   ```bash
   ERROR: AccessDeniedException (code 403)
   ```
   Ensure your credentials have:
   - AWS: `CostExplorerReadOnly`, `EC2ReadOnlyAccess`
   - Azure: Cost Management Reader role
   - GCP: `cloudasset.viewer` and `billing.viewer`

## Next Steps

Now that you're set up, proceed to our [Usage Guide](../usage/analyzing-costs.md) to:
- Interpret optimization recommendations
- Configure custom cost thresholds
- Set up automated savings reports

For advanced configuration options, see our [Configuration Reference](../advanced/configuration-reference.md).