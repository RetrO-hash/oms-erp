## 2024-11-20 - Ensure Secure Configuration Defaults

**Vulnerability:** Hardcoded encryption secrets (publicKey and privateKey) were found as default values in multiple Java `@ConfigurationProperties` classes (e.g. `ChannelProperties.java`). This poses a risk because if properties are not securely externalized and properly overridden in the application runtime environment, the insecure default hardcoded keys will be used, compromising cryptographic security.

**Learning:** When using Spring Boot's `@ConfigurationProperties`, relying on fallbacks defined in code with hardcoded sensitive strings is dangerous. Furthermore, empty string properties (like `${SECRET_KEY:}`) injected from external environments can bypass null-checks, leading to bugs or unintended defaults.

**Prevention:** Ensure default field values for sensitive settings (like passwords, secret keys) in Java configuration classes are set to `null` rather than hardcoded strings. This forces a secure configuration strategy and prevents overriding with unsafe static defaults.
