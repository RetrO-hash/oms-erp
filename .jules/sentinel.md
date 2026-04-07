## 2025-04-07 - Removed Hardcoded Passwords in Fallback Secrets
**Vulnerability:** Found hardcoded fallback passwords for Spring properties `SPRING_DATASOURCE_PASSWORD` and `SPRING_REDIS_PASSWORD` in `application.yml` files (e.g. `Ss110110`, `123456`).
**Learning:** The fallback syntax `${VARIABLE:fallback}` can inadvertently leak local or default credentials if checked into source control, creating a security risk if the environment variables are not set correctly.
**Prevention:** Always use `${VARIABLE:}` without providing hardcoded default passwords in configuration files.
