## 2024-04-01 - [Hardcoded Secrets in Configuration]
**Vulnerability:** Hardcoded API keys, JWT secrets, and maintenance secret keys were present in `application.yml` files (e.g., `skyer-order` and `skyer-gateway`).
**Learning:** Spring Boot configurations in this repository were defaulting to hardcoded fallback secrets even when using environment variable syntax (e.g., `${SECRET:hardcoded_value}`). This exposed critical secrets in plain text in the version control system.
**Prevention:** Always use environment variables without sensitive default values for secrets in configuration files (e.g., `${SECRET:}`). Ensure developers and CI/CD pipelines inject these secrets at runtime.
