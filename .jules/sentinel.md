## 2024-05-24 - Hardcoded Secrets in Application Configurations

**Vulnerability:** Found hardcoded internal API keys and external API secrets (like `baison.key`, `baison.secret` in `skyer-order` and `jwt-key`, `secret-key`, `secrets[0].secretKey` in `skyer-gateway`) checked directly into the codebase in `application.yml` files.
**Learning:** Hardcoding secrets exposes them to everyone who has access to the codebase or its history. It prevents operators from securely changing or rotating credentials without a code deployment. This poses a significant security risk if the codebase is compromised or exposed.
**Prevention:** Externalize secrets using environment variables in Spring `application.yml` configs. Ensure that no hardcoded fallback value is provided (use syntax like `${ENV_VAR_NAME:}`). Secrets should be injected securely at runtime via the environment or a secure secret manager.
