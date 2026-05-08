## 2024-05-08 - Hardcoded Third-Party API Secrets in application.yml
**Vulnerability:** Hardcoded third-party Baison API credentials (`key`, `secret`) and `url` were found in `skyer-order/src/main/resources/application.yml`.
**Learning:** In a microservices architecture, hardcoded third-party secrets in configuration files expose sensitive credentials and can be accessed by anyone with source code read permissions, leading to potential unauthorized access or API abuse.
**Prevention:** Always externalize API secrets using environment variables (e.g., `${BAISON_KEY:}`) without hardcoded fallback values in configuration files to prevent credential leakage.
