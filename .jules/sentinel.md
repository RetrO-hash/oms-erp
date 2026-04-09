## 2024-05-18 - [Hardcoded Secrets Removal in application.yml]
**Vulnerability:** Several `application.yml` files contained hardcoded fallback values for sensitive environment variables like passwords, private keys, and public keys (e.g., `password: ${SPRING_DATASOURCE_PASSWORD:123456}`).
**Learning:** Hardcoded fallbacks in configuration files are often committed to version control, which could lead to unauthorized access if the repository is ever exposed.
**Prevention:** Remove all fallback values for sensitive properties in Spring Boot configuration files, relying strictly on environment variables or external secure configuration management for production.
