## 2024-05-18 - Removed hardcoded secrets
**Vulnerability:** Hardcoded database and redis passwords as well as hardcoded public and private RSA keys in the application.yml and values.yaml files across multiple microservices.
**Learning:** Hardcoding secrets in configuration files that are committed to the repository exposes sensitive information to anyone with access to the source code.
**Prevention:** Always use environment variables or external secret management systems for sensitive data. Do not provide default values for secrets in configuration files.
