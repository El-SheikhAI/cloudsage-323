# CloudSage Security Practices

We prioritize the security of your data and systems throughout CloudSage. This document outlines our practices to protect your infrastructure analytics and cloud cost optimization workflows.

## **Data Protection**
- **Encryption in Transit**: All communications with CloudSage use TLS 1.2+ (HTTPS, WebSockets, and API endpoints).
- **Encryption at Rest**: Customer data is encrypted using AES-256. Infrastructure usage metadata is stored with strict access controls in isolated environments.
- **Credential Storage**: Cloud provider access keys are encrypted using KMS services (AWS KMS/Azure Key Vault/GCP Cloud KMS) and never stored in plaintext logs.

## **Access Control**
- **Authentication**: Supported via OAuth 2.0 (Google, Azure AD, AWS IAM Identity Center) or SAML 2.0 SSO.
- **Authorization**: Role-Based Access Control (RBAC) tied to your cloud provider’s IAM roles. Principle of Least Privilege enforced for all service accounts.
- **Multi-Factor Authentication (MFA)**: Mandatory for all administrative access to CloudSage control planes.

## **Vulnerability Management**
- **Regular Scanning**: Infrastructure undergoes weekly vulnerability scans (using Snyk and Nessus).
- **Patch Management**: Critical security patches applied within 24 hours of vendor release; high-risk patches within 7 days.
- **Automated Dependency Checks**: Dependencies monitored via Renovate Bot and GitHub Dependabot with manual review gates.

## **Incident Response**
1. **Detection**: 24/7 SIEM monitoring (AWS GuardDuty + Splunk)
2. **Containment**: Isolate affected systems within 15 minutes of confirmed incident
3. **Notification**: Affected customers notified via email within 72 hours of incident classification
4. **Forensics**: Retain relevant logs for 90 days post-resolution
5. **Post-Mortem**: Internal review published within 14 business days

**Report Security Issues**: security@cloudsage.com (PGP Key: [LINK_TO_PUB_KEY])

## **Compliance & Audits**
- **SOC 2 Type II**: Annually audited report available under NDA
- **GDPR Ready**: Data processing agreements (DPAs) available upon request
- **Third-Party Pentests**: Biannual external penetration tests by Cure53 & NCC Group
- **Employee Training**: Mandatory annual security training for all engineering staff

## **Data Retention Controls**
- Infrastructure usage metadata: 13 months rolling retention
- Cost optimization recommendations: Retained until manually purged
- Audit logs: 90-day minimum retention (configurable to 7 years)

## **Your Responsibilities**
While CloudSage handles security within our platform, you maintain responsibility for:
- Rotating cloud provider API keys quarterly
- Managing IAM permissions for CloudSage integrations
- Securing access to your CloudSage account credentials

---

*Last updated: Month DD, YYYY*  
*We continually evolve our security practices – subscribe to security advisories at security-updates@cloudsage.com*