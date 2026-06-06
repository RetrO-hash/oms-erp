## 2024-05-20 - Remove Hardcoded Passwords/Secrets in Configuration Files
**Vulnerability:** Hardcoded database passwords, Redis passwords, OAuth keys, and other secrets within `application.yml` files.
**Learning:** Storing secrets in plain text configuration files poses a critical security risk as it can easily lead to credential exposure when code is shared or accidentally leaked. Relying on default fallbacks that are also valid secrets bypasses security best practices.
**Prevention:** Rely entirely on environment variables for sensitive data configuration. Do not provide sensitive default values (like "123456", "Ss110110", or default keys) in the fallback syntax (`${VAR:default}`).
