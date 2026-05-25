## 2023-10-27 - Hardcoded Passwords in Configuration Files
**Vulnerability:** Several default configuration files (`application.yml` and `values.yaml`) for databases, Redis, and OAuth keys included hardcoded plaintext passwords as default values.
**Learning:** Hardcoding passwords poses a serious security risk because anyone with access to the source code can view them, and these defaults may unintentionally be used in production environments.
**Prevention:** Always use environment variables for sensitive configuration properties without hardcoded default fallback values (e.g., using `${SECRET_KEY:}` instead of `${SECRET_KEY:default_value}`). This ensures that secure secrets must be explicitly provided in deployment environments.
