## 2024-05-17 - Removed Hardcoded Cryptographic Keys from Spring ConfigurationProperties

**Vulnerability:** Found hardcoded asymmetric encryption keys (`publicKey` and `privateKey` strings) embedded directly within multiple Java `@ConfigurationProperties` classes (e.g., `ChannelProperties.java`, `AfterSalesProperties.java`, etc.). While there are fallbacks in `application.yml` referencing environment variables like `${SKYER_OAUTH_PASSWORD_PUBLIC_KEY:...}`, the Java class defaults act as an unsecured fallback layer if properties fail to bind or load, exposing sensitive cryptographic material in the source code.

**Learning:** Spring `@ConfigurationProperties` classes that define defaults for sensitive values directly in code pose a risk. If the `application.yml` or environment is misconfigured, the application will silently fall back to the hardcoded keys, meaning any instance could use the identical compromised keys. A secure configuration architecture should enforce that sensitive keys are provided exclusively by the environment and default to `null` to ensure failure if omitted.

**Prevention:** Never provide default values for sensitive properties (passwords, keys, tokens) inside Java code. Initialize these fields to `null` or leave them unassigned so the application fails fast during startup if the environment hasn't provided the necessary secure values.
