
## 2024-05-18 - Hardcoded Keys in ConfigurationProperties
**Vulnerability:** Hardcoded RSA public and private keys were found directly embedded in the `@ConfigurationProperties` classes (`OrderProperties`, `StockProperties`, `GoodsProperties`, `AfterSalesProperties`) across multiple modules.
**Learning:** Providing hardcoded strings as defaults for secure configuration properties can lead to them being used in production if environment variables are not set properly.
**Prevention:** Ensure that default values for sensitive fields (passwords, keys, tokens) in Java configuration classes are set to `null` or left uninitialized, rather than hardcoded string values.
