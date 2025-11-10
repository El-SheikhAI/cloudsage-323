# CloudSage Authentication Guide

Welcome to CloudSage! This guide walks you through authenticating with our API and CLI. Choose the method that matches your workflow.

---

## 🔐 Obtaining Your API Key
1. **Log in** to your CloudSage account at [app.cloudsage.io](https://app.cloudsage.io)
2. Navigate to **Account Settings > Security**
3. Click **Generate API Key** in the API Access section
4. Securely store your key (it will only be shown once!)

---

## 🤖 API Authentication
Authenticate by including your API key in all requests as a header:

```bash
curl -X GET "https://api.cloudsage.io/v1/recommendations" \
  -H "X-API-Key: cs_live_1234567890abcdefghijKL"
```

### Python Example
```python
import requests

headers = {
    "X-API-Key": "cs_live_1234567890abcdefghijKL"
}

response = requests.get(
    "https://api.cloudsage.io/v1/recommendations", 
    headers=headers
)
```

---

## ⌨️ CLI Authentication
1. **Install** the CloudSage CLI
2. Run the auth command:
```bash
cloudsage auth login
```
3. When prompted, paste your API key

### Alternative CLI Setup (non-interactive)
Configure credentials via environment variables:
```bash
export CLOUDSAGE_API_KEY='cs_live_1234567890abcdefghijKL'
```

---

## 🔒 Security Best Practices
1. **Never commit** API keys to version control
2. Rotate keys quarterly via Account Settings
3. Use environment variables instead of hardcoding
4. Restrict keys using RBAC policies where available
5. Immediately revoke compromised keys

---

## 🛠️ Troubleshooting
Common authentication issues and solutions:
- **Invalid API Key**  
  → Verify no typos in key  
  → Check for leading/trailing spaces  
  → Confirm key hasn't been revoked

- **403 Forbidden**  
  → Verify account is active  
  → Check your permission assignments  
  → Ensure your plan includes this feature

- **CLI Auth Failures**  
  → Run `cloudsage auth reset` and re-authenticate  
  → Verify `~/.cloudsage/config` file permissions (chmod 600)

---

Need help? Contact our support team at support@cloudsage.io or via in-app chat. Never share your API key with unauthorized parties!