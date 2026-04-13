# Sentinel Journal

## Security Learnings specific to this codebase

## $(date +%Y-%m-%d) - Externalize Hardcoded Keys and Secrets in Configuration Files
**Vulnerability:** Found multiple instances of hardcoded sensitive information like `secretKey` and `baison.key`, `baison.secret` in `skyer-gateway/src/main/resources/application.yml` and `skyer-order/src/main/resources/application.yml`.
**Learning:** Hardcoding secrets directly in configuration files (even if they're default values or development keys) poses a security risk because they can easily end up in version control systems and become exposed to anyone who has access to the repository.
**Prevention:** Always externalize secrets using environment variables with the `${ENV_VAR:default_value}` syntax or completely without a fallback if it is a truly sensitive secret, delegating the actual values to an external configuration provider (e.g., Vault, Kubernetes Secrets).
