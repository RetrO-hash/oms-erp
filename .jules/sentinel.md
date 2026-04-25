## 2024-05-18 - Hardcoded MaintainEndpoint Secret

**Vulnerability:** The `MaintainProperties` class in `skyer-gateway` had a hardcoded default value for `secretKey` ("skyer"). This allowed attackers to hit the `/maintain` endpoint and potentially pause/stop gateway services using the known default secret. The `MaintainEndpoint` also reflected the provided user input (`secretKey`) directly into the Exception message when authentication failed, creating a log forging and potential XSS/Info Leak risk.

**Learning:** Hardcoded secrets in `@ConfigurationProperties` classes can lead to severe operational and security incidents if default configs are not securely overridden in production. We should always use random generation (like UUID) for missing security properties when possible, rather than fallback strings. Exception messages should not directly reflect user input.

**Prevention:** Ensure default field values in Java config classes representing credentials are `null` or omitted rather than hardcoded strings. This enables the codebase to detect the missing config and fall back to secure random generation logic instead of an insecure default. Always sanitize or remove user input from exceptions or logs.
