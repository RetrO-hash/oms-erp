## 2024-05-06 - Hardcoded Credentials in Configuration

**Vulnerability:** Found hardcoded database passwords, Redis passwords, and OAuth public/private keys in multiple `application.yml` files (e.g., `skyer-channel`, `skyer-order`, `skyer-goods`) and their corresponding Spring Boot `@ConfigurationProperties` classes (e.g., `ChannelProperties.java`). The secrets were exposed as default fallback values in configuration placeholders (`${SECRET_KEY:hardcoded_value}`) and as default field values in Java classes.

**Learning:** Spring Boot's placeholder syntax `${PROPERTY:default_value}` is often misused to embed development or production secrets directly into the codebase. When paired with `@ConfigurationProperties`, if the property is missing from the environment, the application silently falls back to the hardcoded default, posing a severe security risk if the repository is compromised.

**Prevention:** Ensure that all sensitive configuration placeholders do not provide hardcoded default values (e.g., use `${PROPERTY:}` instead of `${PROPERTY:secret}`). In `@ConfigurationProperties` classes, sensitive fields must not be initialized with string literals; they should remain uninitialized (null) so that the application fails fast or requires the environment variable to be explicitly provided during deployment.
