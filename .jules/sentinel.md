## 2024-05-18 - Remove Hardcoded Secrets from Configuration Files
**Vulnerability:** Hardcoded credentials (database passwords, redis passwords, and OAuth keys) were found in both `application.yml` and Helm `values.yaml` files.
**Learning:** Default values in Spring `@ConfigurationProperties` and Helm charts can inadvertently expose sensitive information. Hardcoding sensitive default values like `${SPRING_DATASOURCE_PASSWORD:Ss110110}` bypasses external secret management.
**Prevention:** Always set default fallback values for secrets to empty strings (e.g. `${SECRET:}`) in configuration files, and ensure deployment environments explicitly provide these secrets via environment variables or secret managers.
