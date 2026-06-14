
## 2024-06-14 - Fix Hardcoded Baison API Credentials
**Vulnerability:** The `baison` configuration block in `skyer-order/src/main/resources/application.yml` contained hardcoded, plaintext API keys (`key` and `secret`) rather than using environment variables.
**Learning:** Hardcoded secrets in Spring Boot configuration files can be exposed when the code is pushed to version control, posing a significant security risk.
**Prevention:** Always use environment variable substitution without hardcoded fallback values for secrets (e.g., `${BAISON_KEY:}`) in configuration files to enforce external, secure secret management.
