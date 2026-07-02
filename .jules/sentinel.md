## 2024-05-18 - [Timing Attack, Information Leakage & Hardcoded Secret in MaintainEndpoint]
**Vulnerability:** Found a hardcoded `secretKey = "skyer"` in `MaintainProperties.java`. The `MaintainEndpoint.java` performed standard string comparison `configKey.equals(secretKey)` which is vulnerable to timing attacks. Finally, if the key was invalid, it was reflected back in the `RuntimeException` message `认证失败，[secretKey=" + secretKey + "]不通过`, leading to information leakage / potential log forging.
**Learning:** Default properties for credentials should be null instead of hardcoded strings to ensure proper generation behavior. String matching for secrets must always use constant-time operations to avoid timing attacks. Error messages should never reflect unvalidated input, especially sensitive elements.
**Prevention:**
- Externalize all secrets using secure stores or environment variables; default field values in Java configs should be null for secrets.
- Use `java.security.MessageDigest.isEqual()` on byte arrays for secure string comparisons.
- Fail securely by replacing input reflection with generic error messages.