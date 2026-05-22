## 2024-05-18 - Remove Hardcoded Secrets in Config Files
**Vulnerability:** Hardcoded database and redis passwords as well as OAuth public and private keys were found in `application.yml` default fallback values (e.g., `${SPRING_DATASOURCE_PASSWORD:123456}`).
**Learning:** Default fallback values in Spring configuration files can inadvertently expose sensitive secrets if left populated with production or actual test credentials.
**Prevention:** Externalize secrets completely using environment variables, and ensure the default value is empty (e.g., `${SPRING_DATASOURCE_PASSWORD:}`) to prevent unintentional exposure in the codebase.
