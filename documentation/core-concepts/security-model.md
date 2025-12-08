# Security Model

CloudSage is designed with security at its core. We protect your data and cloud infrastructure through multiple layers of security controls, strict access management, and continuous monitoring—without compromising ease of use.

## Data Protection
- **Encryption in Transit**: All communications are secured via TLS 1.2+ encryption.
- **Encryption at Rest**: Data stored by CloudSage (metrics, configurations) is encrypted using AES-256.
- **Key Management**: Encryption keys are managed through cloud-native solutions (AWS KMS, Azure Key Vault, GCP Cloud KMS).

## Authentication & Access Control
- **Multi-Factor Authentication (MFA)**: Supported for all accounts.
- **Role-Based Access Control (RBAC)**: Granular permissions (Viewer, Editor, Admin) to limit actions based on user roles.
- **Single Sign-On (SSO)**: SAML 2.0 support for enterprise customers.
- **Audit Logs**: All user actions are logged for security reviews.

## Cloud Provider Integrations
CloudSage adheres to strict security principles when interacting with your cloud environments:
- **Zero Write Permissions**: CloudSage *never* modifies your cloud resources. All operations are read-only.
- **Least Privilege Access**: 
  - **AWS**: IAM roles with `ReadOnlyAccess` or custom scoped policies.
  - **Azure**: Read-only Azure RBAC roles (e.g., Reader).
  - **GCP**: Predefined `Viewer` role or custom roles.
- **Credential Security**: 
  - Short-lived access tokens are used where possible.
  - Customer-provided keys/secrets are encrypted and never stored in logs.

## Compliance & Auditing
- **Certifications**: SOC 2 Type II, ISO 27001 compliant.
- **Third-Party Testing**: Regular penetration tests and vulnerability scans conducted by independent auditors.
- **GDPR/CCPA Compliance**: Data residency controls and opt-out mechanisms for personal data.

## Incident Response
- **24/7 Security Monitoring**: Anomalies and threats are detected in real-time.
- **Automated Alerts**: Admins are notified immediately of suspicious activity.
- **Response Playbooks**: Documented procedures for containment, investigation, and remediation of incidents.

## Shared Responsibility Model
Security is a partnership. While CloudSage manages the security *of* the platform, customers are responsible for:
- Securely managing cloud provider credentials.
- Configuring role-based access within their organization.
- Monitoring their CloudSage audit logs regularly.

---

We continuously enhance our security practices to meet evolving threats. For detailed compliance reports or security inquiries, contact [security@cloudsage.com](mailto:security@cloudsage.com).