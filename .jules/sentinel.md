## 2024-06-02 - Hardcoded API Key and Secret
**Vulnerability:** Found hardcoded third-party API key and secret in skyer-order's application.yml (baison.key and baison.secret). Exposing these secrets can lead to unauthorized API access.
**Learning:** Hardcoding sensitive values in application configuration files is a critical vulnerability.
**Prevention:** Always use environment variables for sensitive properties (e.g., ${BAISON_KEY:}) without providing default hardcoded values in fallback.
