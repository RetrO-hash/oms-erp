
## 2024-05-18 - [Hardcoded Secrets Removal]
**Vulnerability:** Found hardcoded passwords and private keys (e.g. `SPRING_DATASOURCE_PASSWORD`, `SKYER_OAUTH_PASSWORD_PRIVATE_KEY`) in Spring Boot `application.yml` and Helm `values.yaml` files.
**Learning:** Hardcoded fallbacks in environment variable substitution can expose sensitive credentials in source control, even if they're default or sample values.
**Prevention:** Remove all hardcoded default secrets and rely solely on the environment variables provided by the deployment environment. Provide empty defaults `${VAR:}` if necessary, but never real credentials.
