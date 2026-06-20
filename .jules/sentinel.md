## 2024-05-18 - Hardcoded Baison API Credentials
**Vulnerability:** Hardcoded external API credentials (`baison.key` and `baison.secret`) found in `skyer-order/src/main/resources/application.yml`.
**Learning:** Hardcoded credentials are a severe security risk. If source code or configuration files are exposed, the credentials can be compromised, allowing unauthorized access to the external service.
**Prevention:** Always externalize secrets into environment variables, secret management systems, or secure vaults. Configuration files should define placeholders (e.g., `${BAISON_KEY:}`) without hardcoded default values.
