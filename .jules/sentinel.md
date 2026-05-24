## 2026-05-24 - [Remove Hardcoded External API Keys]
**Vulnerability:** Hardcoded API keys (`baison.key` and `baison.secret`) were found in `skyer-order/src/main/resources/application.yml`. Storing secrets in plain text configuration files risks unauthorized access if the codebase is exposed or shared.
**Learning:** External API credentials were included directly in the application configuration instead of being passed securely from the environment or a secret management system. This is a common oversight that can lead to credential leakage.
**Prevention:** Always use environment variables for sensitive configurations, ensuring no hardcoded fallback values are provided in the source code. For example, use `${BAISON_KEY:}` instead of `${BAISON_KEY:defaultSecret}`.
