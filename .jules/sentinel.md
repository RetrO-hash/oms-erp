## 2024-05-24 - Hardcoded Secrets Removed
**Vulnerability:** Widespread use of hardcoded secrets across multiple microservices including:
- Database credentials (`SPRING_DATASOURCE_PASSWORD`)
- Redis credentials (`SPRING_REDIS_PASSWORD`)
- OAuth Public/Private Keys in `application.yml` and `*Properties.java` files
- Third-party API keys (Baison `key` and `secret`)
- JWT/Gateway maintain secrets

**Learning:** Relying on default hardcoded fallbacks like `${SECRET_KEY:hardcoded_value}` inside configuration files and Java code leads to massive secret sprawl across the codebase. Even if these are meant as "dev" defaults, they can easily leak into production environments if environment variables are accidentally omitted.

**Prevention:** Ensure secrets are strictly externalized. Use `${SECRET_KEY:}` pattern without hardcoded fallbacks in configuration. In Java configuration classes (`@ConfigurationProperties`), initialize secret fields to `null` instead of hardcoded strings to prevent secure configs from being overridden by insecure defaults.
