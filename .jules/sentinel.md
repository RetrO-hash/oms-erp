## 2024-05-18 - Hardcoded Baison API Keys in application.yml
**Vulnerability:** Hardcoded `baison.key` and `baison.secret` found in `skyer-order/src/main/resources/application.yml`.
**Learning:** Third-party API credentials should never be committed to source code or configuration files, as this can lead to unauthorized access and data breaches. Spring Boot provides mechanisms to externalize configuration.
**Prevention:** Always use environment variables or a secrets management system (e.g., Vault, AWS Secrets Manager) for sensitive credentials. In Spring Boot, use `${ENV_VAR_NAME:}` to inject these values, ensuring no hardcoded fallback is provided.
