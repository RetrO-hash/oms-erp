## 2024-05-13 - [Hardcoded Public/Private Keys in application.yml]
**Vulnerability:** Public and private keys for oauth password encryption are hardcoded in application.yml files across multiple microservices.
**Learning:** Keys and secrets should not be hardcoded in codebase files, even if they are default or dummy values, as they can be mistakenly used in production or leaked. They should be externalized to environment variables and injected at runtime.
**Prevention:** Use environment variables for sensitive data in application properties, without providing hardcoded default fallback values.
