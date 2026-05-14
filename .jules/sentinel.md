## 2024-05-15 - Remove Hardcoded Secrets from Spring Boot application.yml

**Vulnerability:** Several Spring Boot `application.yml` files contained hardcoded database passwords, Redis passwords, and RSA public/private keys as fallback values in environment variable placeholders (e.g., `${SPRING_DATASOURCE_PASSWORD:Ss110110}`).
**Learning:** Fallback values in Spring configuration files are often committed to version control, which leads to secrets exposure if the repository is accessible. Spring Boot evaluates these properties at startup, and providing a hardcoded fallback bypasses the security intent of using environment variables.
**Prevention:** Always leave fallback values empty for secrets (e.g., `${SPRING_DATASOURCE_PASSWORD:}`) or omit the fallback entirely so the application fails to start securely if the environment variable is not provided.
