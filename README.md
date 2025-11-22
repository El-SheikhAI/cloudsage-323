# CloudSage

## AI-Powered Cloud Cost Optimization for AWS, Azure, and GCP

CloudSage is an intelligent cloud management tool that automatically analyzes your infrastructure usage patterns and delivers actionable recommendations to reduce spending across AWS, Azure, and Google Cloud Platform.

![License](https://img.shields.io/badge/License-Apache_2.0-blue)
![Python Version](https://img.shields.io/badge/python-3.10%2B-blue)

<img src="docs/cloudsage-dashboard-preview.png" alt="CloudSage Dashboard Preview" width="800">

## Key Features

✔️ **AI-Driven Cost Analysis**  
Identifies spending patterns and anomalies using machine learning

✔️ **Automated Savings Recommendations**  
Provides customized optimizations:
- Rightsizing instances
- Identifying idle resources
- Optimizing commitment discount purchases
- Storage tier optimization

✔️ **Multi-Cloud Support**  
Unified dashboard for AWS, Azure, and GCP environments

✔️ **Security-First Approach**  
Read-only access to your cloud infrastructure

## Installation

### Prerequisites
- Python 3.10+
- Access credentials for at least one cloud provider
- Docker (optional)

### Quick Start
```bash
# Clone repository
git clone https://github.com/yourorg/cloudsage.git
cd cloudsage

# Create virtual environment
python3 -m venv venv
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Configure environment variables
cp .env.example .env  # Update with your credentials
```

### Docker Installation
```bash
docker build -t cloudsage .
docker run -it --env-file .env cloudsage
```

## Configuration

Configure your cloud providers in `.env`:
```ini
AWS_ACCESS_KEY_ID=your_aws_key
AWS_SECRET_ACCESS_KEY=your_aws_secret

AZURE_TENANT_ID=your_azure_tenant
AZURE_CLIENT_ID=your_azure_client
AZURE_CLIENT_SECRET=your_azure_secret

GCP_SERVICE_ACCOUNT_KEY_PATH=/path/to/gcp_key.json
```

## Basic Usage

Analyze current infrastructure:
```bash
python cloudsage.py analyze --all-providers
```

Generate recommendations:
```bash
python cloudsage.py recommend --output html
```

Automated savings implementation (dry-run):
```bash
python cloudsage.py optimize --dry-run
```

Start the web dashboard:
```bash
python cloudsage.py dashboard
```

## Documentation

Full documentation is available at:  
[https://cloudsage-docs.yourdomain.com](https://cloudsage-docs.yourdomain.com)

Includes:
- Detailed configuration options
- Architecture overview
- Security model
- API reference
- Tutorials

## Contributing

We welcome contributions! Please see our [CONTRIBUTING.md](CONTRIBUTING.md) for:
- Issue reporting guidelines
- Development setup instructions
- Code style requirements
- Pull request process

Before contributing major changes, please open an issue to discuss your proposed changes.

## Support

Having trouble? Try these resources:
- [GitHub Issues](https://github.com/yourorg/cloudsage/issues)
- Community Forum: [forum.cloudsage.com](https://forum.cloudsage.com)
- Support Email: support@cloudsage.com

Business hours support: Mon-Fri 9AM-5PM PST

## License

CloudSage is licensed under the Apache License 2.0 - see [LICENSE](LICENSE) for details.

---
> [!NOTE]
> **Portfolio Demonstration**: This project is a showcase of technical writing and documentation methodology. It is intended to demonstrate capabilities in structuring, documenting, and explaining complex technical systems. The code and scenarios described herein are simulated for portfolio purposes.