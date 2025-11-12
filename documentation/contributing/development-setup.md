# Development Setup Guide

Welcome to CloudSage development! This guide walks you through setting up your local environment.

## Prerequisites

Install these tools before proceeding:

- **Git** ([Installation guide](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git))
- **Docker** v24.0+ ([Docker Desktop](https://www.docker.com/products/docker-desktop))
- **Node.js** v18+ ([Node.js downloads](https://nodejs.org/en/download))
- **Python** 3.11+ ([Python downloads](https://www.python.org/downloads/))

*Optional but recommended:*
- **AWS CLI** ([Install guide](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html))
- **Azure CLI** ([Install guide](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli))
- **gcloud CLI** ([Install guide](https://cloud.google.com/sdk/docs/install))

## Repository Setup

1. Clone the repository:
```bash
git clone https://github.com/cloudsage/cloudsage.git
cd cloudsage
```

2. Initialize submodules:
```bash
git submodule update --init --recursive
```

## Install Dependencies

### Node.js Packages
```bash
npm ci
```

### Python Packages
```bash
pip install -r requirements.txt
```

## Configuration Setup

1. Create environment file:
```bash
cp .env.example .env
```

2. Update `.env` with your credentials:
```ini
# AWS Credentials
AWS_ACCESS_KEY_ID=your_access_key
AWS_SECRET_ACCESS_KEY=your_secret_key

# Azure Credentials
AZURE_TENANT_ID=your_tenant_id
AZURE_CLIENT_ID=your_client_id
AZURE_CLIENT_SECRET=your_client_secret

# GCP Credentials
GOOGLE_APPLICATION_CREDENTIALS=path/to/your/service-account.json
```

3. Generate initial config:
```bash
npm run config:generate
```

## Run Services

Start core services via Docker:
```bash
docker compose up -d postgres redis
```

Run the main application:
```bash
# Start backend API
npm run api:dev

# Start frontend
npm run ui:dev
```

## Verify Installation

Run unit tests to confirm everything works:
```bash
# Run Python tests
pytest tests/

# Run Playwright tests
npx playwright test
```

## Debugging Tips

Common issues and solutions:

1. **Docker permission errors**  
   Add your user to the docker group:
   ```bash
   sudo usermod -aG docker $USER
   ```

2. **Port conflicts**  
   Check for processes using ports 5432 (Postgres), 6379 (Redis), 8000 (API), or 3000 (UI):
   ```bash
   lsof -i :8000
   ```

3. **Missing dependencies**  
   Reinstall dependencies from lock files:
   ```bash
   npm ci && pip install -r requirements.txt
   ```

4. **Environment variables not loading**  
   Restart your terminal after modifying `.env`

## Additional Tools

We recommend these VS Code extensions:
- Python
- ESLint
- Docker
- Markdown All in One

Our internal CLI tool can help with common tasks:
```bash
npm run tools -- --help
```

## Need Help?

Join the #cloudsage-dev channel in our company Slack workspace for real-time support.