## 2024-06-10 - [CRITICAL] Hardcoded Third-Party API Credentials
**Vulnerability:** Hardcoded `baison.key` and `baison.secret` were found in `skyer-order/src/main/resources/application.yml`. These are credentials for third-party Baison integration.
**Learning:** Hardcoding credentials for third-party systems exposes the application to credential theft and unauthorized access if the codebase is compromised. These secrets must be injected from the deployment environment securely.
**Prevention:** Always use environment variable placeholders (e.g., `${BAISON_KEY:}`) in configuration files for secrets without providing default fallback values that contain sensitive data. Ensure the deployment environment securely injects these values.
