## 2024-05-18 - [Fix Hardcoded Secrets in Config Files]
**Vulnerability:** Hardcoded API keys (`baison.key`, `baison.secret`) were found in `skyer-order/src/main/resources/application.yml`. Committing these secrets to version control is a critical vulnerability that risks unauthorized access to external Baison services.
**Learning:** Third-party API credentials were directly embedded in configuration files instead of being injected via environment variables. This pattern exposes sensitive data to anyone with repository access.
**Prevention:** Always use environment variable substitution without hardcoded fallbacks (e.g., `${SECRET_KEY:}`) in Spring Boot configuration files for any sensitive credentials, keys, or passwords.
