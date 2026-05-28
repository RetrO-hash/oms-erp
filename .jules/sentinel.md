## 2024-05-28 - Removed Hardcoded Secrets in Config Files
**Vulnerability:** Several `application.yml` files contained hardcoded fallback values for sensitive properties: `SPRING_DATASOURCE_PASSWORD`, `SPRING_REDIS_PASSWORD`, `SKYER_OAUTH_PASSWORD_PUBLIC_KEY`, and `SKYER_OAUTH_PASSWORD_PRIVATE_KEY`.
**Learning:** Hardcoded fallbacks in config files expose sensitive credentials if the configuration files are leaked or committed to version control.
**Prevention:** Rely strictly on environment variables without providing hardcoded default fallback values for secrets.
