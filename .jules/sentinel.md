## 2024-06-27 - Information Leakage in Exception Message
**Vulnerability:** The `MaintainEndpoint` class throws a `RuntimeException` that includes the user-provided `secretKey` when authentication fails: `throw new RuntimeException("认证失败，[secretKey=" + secretKey + "]不通过");`.
**Learning:** This exposes user input in error messages or logs, which can lead to information leakage and potentially Log Forging or Cross-Site Scripting (XSS) if the error is rendered unescaped in a UI.
**Prevention:** Fail securely. Always use generic error messages for authentication or authorization failures (e.g., "Authentication failed"). Never reflect sensitive user input or secrets in exceptions or logs.
