## 2024-05-15 - [Gateway Security Enhancements]
**Vulnerability:**
1. The `MaintainEndpoint.java` reflected unsanitized user input (`secretKey`) in a `RuntimeException` message. This could lead to log forging, Cross-Site Scripting (XSS) (if the error is displayed to the user), or information leakage.
2. The `MaintainProperties.java` class had a hardcoded default fallback value `"skyer"` for the `secretKey` field. If this was not overridden in `application.yml`, the system would use this well-known key instead of securely generating a random one at startup, allowing unauthorized access to the `/maintain` endpoint.
**Learning:**
Default hardcoded fallback values in configuration property classes and files override random generation logic, resulting in insecure defaults. Exception messages must be generic and never reflect user-supplied data to maintain application security.
**Prevention:**
1. Default values in configuration property classes should be `null` or uninitialized to force either explicit configuration or secure random generation at startup. Externalize all secrets in `application.yml` using environment variables without hardcoded fallbacks (e.g., `${SECRET_KEY:}`).
2. Fail securely by ensuring error and exception messages use generic responses and do not reflect user input.
