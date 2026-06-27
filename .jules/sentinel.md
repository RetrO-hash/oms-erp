## 2024-07-04 - Hardcoded External API Credentials (Baison)
**Vulnerability:** Hardcoded external API keys and secrets for Baison integration in `skyer-order/src/main/resources/application.yml`.
**Learning:** External API credentials should not be hardcoded in standard `application.yml` files, as they can be easily leaked. They should be loaded via environment variables with default values left empty or as placeholders to prevent overriding external secure configuration, and they should be externalized.
**Prevention:** Always use `${ENV_VAR}` syntax for secrets in configuration files, and avoid hardcoding sensitive values like keys and passwords.
