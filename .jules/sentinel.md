## 2024-04-04 - [Hardcoded Credentials in Application Config]
**Vulnerability:** Found hardcoded API keys and secrets directly inside Spring Boot application.yml files (e.g., baison.key, baison.secret, skyer.gateway.helper.signature.secrets.secretKey).
**Learning:** Configurations in this codebase occasionally commit raw strings for sensitive keys instead of dynamically evaluating from the environment, leading to high-severity leakage risks in source control.
**Prevention:** All secrets should be externalized using environment variable patterns (e.g., `${ENV_VAR_NAME:}`). Do not specify default fallback values that contain real secrets in these configuration placeholders.
