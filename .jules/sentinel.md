## 2024-05-18 - [Hardcoded Secrets Fallback in Configuration Classes]
**Vulnerability:** Spring Boot `@ConfigurationProperties` classes using hardcoded string defaults for secret keys (e.g., `private String secretKey = "skyer";`).
**Learning:** Hardcoded fallbacks in configuration properties classes can silently override null or missing configurations, leaving the system using a known, weak default key, even if environment variable injection is configured but fails or is missing.
**Prevention:** Ensure default field values for secrets in Java config classes are `null` rather than hardcoded strings, so that missing configurations fail securely or generate secure random defaults at runtime (as intended by `MaintainEndpoint.java`).
