# CloudSage CLI Command Reference

**Elevate your cloud cost optimization with our command-line interface.**  
Quickly analyze infrastructure, get savings insights, and automate cost controls across AWS, Azure, and GCP.

---

## Table of Contents
1. [Authentication](#authentication)
2. [Configuration](#configuration)
3. [Cost Analysis](#cost-analysis)
4. [Recommendations](#recommendations)
5. [Automation Actions](#automation-actions)
6. [Error Handling](#error-handling)
7. [Glossary](#glossary)

---

## Authentication
Authenticate with your cloud provider before running cost analysis. 

### `cloudsage auth login`
```bash
# Interactive login (opens browser)
cloudsage auth login --provider aws
cloudsage auth login --provider azure
cloudsage auth login --provider gcp

# Non-interactive (service account)
cloudsage auth login --provider gcp --key-file credentials.json
```

**Options:**
- `--provider` : Specify cloud provider (`aws`/`azure`/`gcp`)
- `--key-file` : Path to service account credentials (GCP/Azure)

---

## Configuration
Customize CloudSage behavior with persistent settings.

### `cloudsage configure`
```bash
# Set default output format
cloudsage configure set output.table

# Configure currency and timezone
cloudsage configure set currency EUR
cloudsage configure set timezone "Europe/Berlin"

# View current configuration
cloudsage configure list
```

**Supported Formats:**
- `table` : Human-readable tables (default)
- `json` : Raw JSON output
- `csv` : Comma-separated values

---

## Cost Analysis
Identify spending patterns across resources.

### `cloudsage analyze costs`
```bash
# Analyze last 30 days across all services
cloudsage analyze costs --last-month

# Generate custom time-range report
cloudsage analyze costs --start 2023-11-01 --end 2023-11-30

# Group results by service category
cloudsage analyze costs --group-by service --output csv
```

**Key Options:**  
`--last-week` | `--last-month` | `--days <N>` | `--group-by <service/resource/account>`  

---

## Recommendations
Get actionable savings suggestions.

### `cloudsage recommendations generate`
```bash
# Get instant recommendations
cloudsage recommendations generate

# Filter by specific service and savings threshold
cloudsage recommendations generate --service EC2 --min-savings 30%

# Use analysis ID from previous runs
cloudsage recommendations generate --analysis-id cldsg_7Xy21T
```

**Sample Output:**
```text
┌──────────────┬──────────────────────┬───────────────┬─────────────┐
│ Resource     │ Recommendation       │ Monthly Cost  │ Savings     │
├──────────────┼──────────────────────┼───────────────┼─────────────┤
│ AWS: EC2     │ Switch to t3.large   │ $1,500        │ 35% ($525)  │
│ Azure: VMs   │ Shutdown weekends    │ $890          │ 28% ($249)  │
└──────────────┴──────────────────────┴───────────────┴─────────────┘
```

---

## Automation Actions
Implement savings recommendations safely.

### `cloudsage apply recommendations`
```bash
# Preview changes without execution
cloudsage apply recommendations --dry-run

# Automatically approve low-risk actions
cloudsage apply recommendations --auto-approve low-risk

# Target specific recommendation IDs
cloudsage apply recommendations --ids rec_01HGTA rec_01HGTB
```

**Safety Flags:**  
`--dry-run` | `--auto-approve <low-risk/all>` | `--confirm`

---

## Error Handling
Common issues and resolutions:

| Error Code | Meaning | Solution |
|------------|---------|----------|
| `AUTH-403` | Invalid credentials | Run `cloudsage auth login` |
| `CONFIG-12` | Missing output format | Set with `cloudsage configure set output` |
| `API-504` | Provider API timeout | Retry with `--retries 3` |

---

## Glossary
- **RI (Reserved Instances):** AWS discounted long-term compute commitments  
- **Savings Plans:** Flexible hourly spend commitments (AWS/Azure)  
- **CUDs:** Committed Use Discounts (GCP long-term discounts)  

---

📦 **Need More Help?**  
Run `cloudsage --help` or visit [https://cloudsage/docs/cli](https://cloudsage/docs/cli) for video guides.