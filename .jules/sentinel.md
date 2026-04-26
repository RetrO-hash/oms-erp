## 2026-04-26 - Prevent Hardcoded Secret Fallback and User Input Reflection in Exceptions
**Vulnerability:**
The `MaintainProperties` class contained a hardcoded fallback string for `secretKey`. Additionally, the `application.yml` property default value effectively locked the secret, overriding a random UUID generation process explicitly meant to run when the property is absent. The application also directly reflected untrusted user input in the exception string in `MaintainEndpoint`, leading to potential log forging and XSS if logged/rendered.
**Learning:**
Hardcoded defaults in `@ConfigurationProperties` and application property files can silently override protective behavior (like random token generation), making the system trivially bypassable if these config objects represent sensitive tokens/keys. Reflecting untrusted input in standard `RuntimeException` objects can leak information and enable injection vulnerabilities depending on how the error handler surfaces or logs the message.
**Prevention:**
1. Leave the default of secret-related configuration property fields as `null` or undefined.
2. In YAML configurations, use `${SECRET_KEY:}` rather than `${SECRET_KEY:hardcoded_value}` to allow applications to recognize when a value is omitted and correctly fall back to generating secure defaults.
3. Fail securely by ensuring error messages contain generic context rather than reflecting potentially malicious input values.
