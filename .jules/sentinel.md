## 2024-04-23 - [Hardcoded Secrets in Gateway Configuration]
**Vulnerability:** Found residual hardcoded secrets (`SPRING_DATASOURCE_PASSWORD`, `jwt-key`, `secretKey`, `secret-key`) in `skyer-gateway/src/main/resources/application.yml` left over as fallback values (e.g. `${SPRING_DATASOURCE_PASSWORD:123456}`).
**Learning:** Spring Boot configurations often leak sensitive information if default fallback values are left in place during development or testing, making it easy for an attacker to obtain database credentials or JWT keys.
**Prevention:** Externalize all secrets using environment variables without specifying default fallback values for secrets (e.g., use `${SECRET:}`).
