## 2024-05-04 - Hardcoded Secrets in Config Files
**Vulnerability:** Found hardcoded credentials (API keys, secrets, JWT keys) in `skyer-order` and `skyer-gateway` `application.yml` files.
**Learning:** Hardcoding secrets exposes them in version control and can lead to unauthorized access and system compromise. Secrets were present in default configuration files.
**Prevention:** Externalize secrets using environment variables without hardcoded fallbacks (e.g., `${SECRET_KEY:}`) so they can be injected at runtime and are not stored in the repository.
