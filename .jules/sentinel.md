## 2024-03-24 - Default Secret Key Hardcoded in Gateway

**Vulnerability:** The MaintainEndpoint in `skyer-gateway` allows enabling/disabling of services using a `secretKey`. The configuration for this (`MaintainProperties`) defaults the secret key to the string `"skyer"`. This hardcoded secret could be abused by an attacker who knows the default value to stop or pause services via the `/maintain` endpoint.

**Learning:** Developers often hardcode default secrets in `@ConfigurationProperties` classes to make local development easier or to avoid application startup failures, without realizing these defaults can leak into production if not explicitly overridden.

**Prevention:** Ensure `@ConfigurationProperties` properties that represent secrets default to `null`. If a fallback is necessary, generate a secure random value at runtime instead of hardcoding a predictable string.
