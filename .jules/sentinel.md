## 2026-05-26 - [Hardcoded Baison API Secrets]
**Vulnerability:** Hardcoded external API keys/secrets for Baison system in `skyer-order/src/main/resources/application.yml`.
**Learning:** Application config files should not contain clear-text secrets. Using environment variables without hardcoded fallbacks avoids exposing secrets when configs are checked into version control.
**Prevention:** Always use environment variables (`${SECRET_KEY:}`) for external API keys, database passwords, and other sensitive information in Spring Boot configuration files.
