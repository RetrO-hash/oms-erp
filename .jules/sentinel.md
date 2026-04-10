## 2024-05-18 - [CRITICAL] Hardcoded External API Secrets in Configuration
**Vulnerability:** Found hardcoded third-party API credentials (`baison.key` and `baison.secret`) in `application.yml`. Committing these secrets to the repository exposes them to anyone with repository access.
**Learning:** Configurations for external integrations (like third-party ERP/WMS systems) are often copy-pasted with development or testing credentials directly into Spring Boot YAML files. This is a common but dangerous pattern in enterprise apps.
**Prevention:** Always externalize API keys, secrets, and passwords using Spring Boot's environment variable placeholders (e.g., `${SERVICE_KEY:}`). Ensure no fallback values are provided for production secrets.
