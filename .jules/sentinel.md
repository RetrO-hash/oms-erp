## 2026-05-23 - Hardcoded Baison API Secrets

**Vulnerability:** Found hardcoded third-party API credentials (`baison.key` and `baison.secret`) in `skyer-order/src/main/resources/application.yml`.
**Learning:** Hardcoded credentials for external services expose systems to unauthorized access and potential data leaks if the repository is compromised. These should always be fetched securely from the environment.
**Prevention:** Externalize secrets using environment variables without hardcoded fallbacks (e.g. `${BAISON_KEY:}`). Ensure proper configurations in secrets management systems in all environments.
