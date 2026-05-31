## 2026-05-31 - Hardcoded Baison API Secrets in Application Configuration

**Vulnerability:** Found hardcoded API keys/secrets (`baison.key` and `baison.secret`) in `skyer-order/src/main/resources/application.yml` directly checked into version control.

**Learning:** Spring Boot application.yml files are commonly used to store configurations, but they are tracked in version control, making any hardcoded sensitive credentials accessible to anyone with repository access.

**Prevention:** Always externalize secrets to environment variables (e.g. `${BAISON_KEY:}`) and avoid putting fallback hardcoded secret strings in the config file.
