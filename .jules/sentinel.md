## 2024-05-14 - Hardcoded Secrets in Configuration Defaults
**Vulnerability:** Found hardcoded fallback values for sensitive properties (SPRING_DATASOURCE_PASSWORD, SPRING_REDIS_PASSWORD, SKYER_OAUTH_PASSWORD_PUBLIC_KEY, SKYER_OAUTH_PASSWORD_PRIVATE_KEY) in multiple `application.yml` files across the repository.
**Learning:** Hardcoding default values for secrets in configuration files can expose these secrets if the environment variables are not properly set, leading to potential unauthorized access to databases, caches, and potentially compromising OAuth.
**Prevention:** Remove fallback values for all sensitive properties in configuration files. Secrets should be exclusively injected via environment variables without hardcoded defaults in the codebase.
