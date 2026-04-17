## 2026-04-17 - Removed Hardcoded MaintainProperties Secret Key
**Vulnerability:** A hardcoded `secretKey` ("skyer") was embedded directly into the `@ConfigurationProperties` bean `MaintainProperties.java` for the `/maintain` endpoint.
**Learning:** Hardcoding default secrets in ConfigurationProperties Java classes overrides null checks. When the endpoint `MaintainEndpoint.java` checked if the secret key was blank to substitute it with a secure random UUID, the hardcoded string prevented this safeguard from executing.
**Prevention:** Always leave default values for security-sensitive `@ConfigurationProperties` fields as `null` in Java, relying on Spring to inject properties from environment variables, configuration files, or falling back to dynamically generated secure random values.
