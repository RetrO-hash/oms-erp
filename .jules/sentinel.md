
## 2024-05-11 - Hardcoded Maintenance Secret and Input Reflection
**Vulnerability:** A hardcoded `secretKey` ("skyer") was embedded in `MaintainProperties.java` and `application.yml` for the gateway's maintenance endpoint, providing a default backdoor. Additionally, when authentication failed in `MaintainEndpoint.java`, the exception message reflected the provided `secretKey` unsanitized.
**Learning:** Hardcoded credentials even as defaults pose a significant security risk, especially in properties used across environments. Reflecting user input in exceptions or logs risks information leakage and log forging/XSS.
**Prevention:** Externalize secrets using environment variables without hardcoded fallbacks (e.g., `${SECRET_KEY:}`). Ensure default field values in Java config classes are null rather than hardcoded strings. Fail securely by using generic error messages ("认证失败") without reflecting user input.
