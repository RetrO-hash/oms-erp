## 2024-05-24 - [Remove Hardcoded Secrets from Spring Boot Configs]
**Vulnerability:** Found hardcoded fallback values for database passwords, redis passwords, and OAuth public/private keys in `application.yml` files across multiple microservices.
**Learning:** Spring Boot property placeholders with fallbacks (e.g., `${SECRET:hardcoded_value}`) can easily leak secrets if committed to version control. It exposes credentials to anyone with access to the source code.
**Prevention:** Always use environment variables without fallback values for sensitive information (e.g., `${SECRET:}`). Ensure these variables are provided by the deployment environment securely.
