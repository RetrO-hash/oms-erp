## 2024-06-25 - Hardcoded Secret in ConfigurationProperties Class
**Vulnerability:** A hardcoded secret (`private String secretKey = "skyer";`) was found in the `MaintainProperties` class inside `skyer-gateway`.
**Learning:** Hardcoded default values for `@ConfigurationProperties` fields can act as insecure fallbacks if external configuration (like environment variables or `application.yml`) is missing. This exposes the secret string directly in the source code.
**Prevention:** Always initialize sensitive fields (like passwords, keys, and tokens) to `null` or omit the default initialization entirely in configuration classes. This enforces external configuration and prevents sensitive data leakage in the repository.
