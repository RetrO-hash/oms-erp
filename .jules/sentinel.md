## 2024-05-15 - Hardcoded Secret and Timing Attack in Gateway MaintainEndpoint
**Vulnerability:** A hardcoded secret (`"skyer"`) was set as the default for `skyer.maintain.secretKey` in `MaintainProperties`. The `MaintainEndpoint` also compared the user-provided `secretKey` against this property using `String.equals()`, making it susceptible to timing attacks. Furthermore, the authentication failure exception message reflected the user-provided `secretKey`, creating an information leakage/log forging risk.
**Learning:** Hardcoded default secrets bypass the intent of secure configuration properties, creating a known attack vector across all deployments if not overridden. Comparing strings with `.equals()` allows an attacker to guess secrets byte-by-byte by observing response times. Reflecting user input in exceptions/logs can expose sensitive data or allow log forging.
**Prevention:**
1. Default sensitive properties in `@ConfigurationProperties` to `null`.
2. Use `java.security.MessageDigest.isEqual(a.getBytes(), b.getBytes())` (with null checks) for constant-time comparisons of secrets.
3. Always fail securely with generic error messages (e.g., "Authentication failed") and never reflect untrusted or sensitive input back in errors or logs.
