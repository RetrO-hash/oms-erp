## 2024-05-17 - [Remove Hardcoded Credentials in Spring Boot Configs]
**Vulnerability:** Found hardcoded `key` and `secret` strings for an external API (`baison`) directly embedded in `skyer-order/src/main/resources/application.yml`.
**Learning:** In Spring Boot, putting secrets in `application.yml` directly exposes them to anyone who can read the source code. It is critical to never hardcode credentials.
**Prevention:** Externalize configurations that contain sensitive data. Always use environment variable placeholders with no hardcoded fallback (e.g., `${BAISON_KEY:}` instead of `mysecretkey` or `${BAISON_KEY:mysecretkey}`) in Spring YAML properties to fetch secrets at runtime.
