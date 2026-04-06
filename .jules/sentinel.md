## 2025-02-14 - [Remove Hardcoded Credentials]
**Vulnerability:** Several `application.yml` files contained hardcoded credentials (database passwords, redis passwords, public/private keys, api secrets).
**Learning:** Hardcoding sensitive information in application code violates best practices and can be leaked. Spring Boot configurations should rely on externalized environment variables without hardcoded fallbacks for sensitive data.
**Prevention:** Always use environment variable substitution like `${SECRET_VAR:}` for sensitive information instead of embedding the secret directly in the repository.
