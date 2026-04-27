## 2024-04-27 - [Hardcoded Baison API Secrets]
**Vulnerability:** Hardcoded API keys (`baison.key` and `baison.secret`) were found directly in `skyer-order/src/main/resources/application.yml`.
**Learning:** These sensitive values should never be stored in plaintext within source control. Exposing API secrets in configuration files poses a critical security risk.
**Prevention:** Always use environment variable references (`${VAR_NAME:}`) without default string fallbacks in configuration files to safely inject secrets at runtime.
