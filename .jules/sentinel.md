## 2023-10-27 - Hardcoded Defaults in Security Properties Configuration

**Vulnerability:**
The `MaintainProperties.java` class had its `secretKey` field initialized with a hardcoded value (`"skyer"`). Because of this hardcoded default, the `MaintainEndpoint` which had logic to securely generate a random key if one was not configured via properties, was bypassed. The endpoint incorrectly assumed that the key was explicitly set to "skyer" by an administrator and continued to use the insecure hardcoded key instead of generating a random one.

**Learning:**
Security-critical properties in Java Configuration classes (`@ConfigurationProperties`) must default to `null` unless there is a strong, secure, and documented reason otherwise. If a hardcoded default is set, it overrides the fallback behavior (such as secure random generation) designed to protect unconfigured systems. Additionally, `application.yml` files should never contain hardcoded secrets, even as fallback values, they should reference environment variables exclusively (e.g. `${SECRET:}`).

**Prevention:**
1. Ensure fields in `@ConfigurationProperties` classes that represent credentials, secrets, or keys have `null` as their default value.
2. In `application.yml` files, externalize secrets and ensure no hardcoded values exist for secrets, credentials, or JWT keys. Use `${VAR:}` syntax.
3. Review configuration logic to ensure that "lack of configuration" is distinguishable from "intentional weak configuration", commonly achieved by checking for `null` or empty values.
