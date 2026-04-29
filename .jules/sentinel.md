## 2024-04-29 - [Fix hardcoded Baison API secrets]
**Vulnerability:** Hardcoded external API credentials (baison.key and baison.secret) found in `skyer-order/src/main/resources/application.yml`.
**Learning:** Third-party integration credentials should never be committed directly to version control. They were stored in plain text configuration files.
**Prevention:** Always externalize API credentials to environment variables using placeholders like `${BAISON_KEY:}` without hardcoded fallbacks in configuration files.
