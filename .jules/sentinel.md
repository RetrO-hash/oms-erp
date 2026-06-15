## 2024-06-15 - [Information Leakage / Log Forging] Reflecting User Input in Errors
**Vulnerability:** The application was throwing an exception (`throw new RuntimeException("认证失败，[secretKey=" + secretKey + "]不通过");`) that directly included unvalidated user input (`secretKey`) in the error message.
**Learning:** This is a classic example of Information Leakage and can lead to Log Forging or XSS (if the error is rendered in a web page without escaping) because it blindly reflects user-provided data back.
**Prevention:** Always use generic error messages (e.g., `"认证失败"`) for authentication failures. Do not reflect sensitive or untrusted user input directly in exceptions or logs without proper sanitization.
