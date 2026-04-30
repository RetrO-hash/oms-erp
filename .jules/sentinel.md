## 2024-05-18 - Hardcoded API Keys in Spring Configuration
**Vulnerability:** Hardcoded API keys, URLs, and secrets found in Spring application.yml configuration (baison integration).
**Learning:** Hardcoding credentials in version-controlled config files exposes sensitive data to all developers with repository access and makes credential rotation difficult. Fallback default strings in @Value or ${ENV:default} format should also not contain sensitive secrets.
**Prevention:** Always use environment variable injections (e.g., `${BAISON_KEY:}`) with no hardcoded fallback value. Pass secrets via secure orchestration platforms or CI/CD pipelines instead of committing them to the repository.
