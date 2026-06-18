## 2024-06-18 - Remove Hardcoded Secrets from Configuration Files
**Vulnerability:** Found hardcoded database passwords, Redis passwords, and OAuth public/private keys in fallback values of `application.yml` across multiple services.
**Learning:** Hardcoded secrets in fallback values (e.g., `${SPRING_DATASOURCE_PASSWORD:123456}`) expose sensitive information if environment variables are not set. This violates the principle of least privilege and secure defaults.
**Prevention:** Always ensure that configuration files use empty strings or fail securely when environment variables are missing (e.g., `${SPRING_DATASOURCE_PASSWORD:}`).
