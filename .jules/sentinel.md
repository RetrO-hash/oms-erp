## 2025-05-09 - [Hardcoded Maintain Properties Secret]
**Vulnerability:** Hardcoded `secretKey` value ("skyer") found in `MaintainProperties.java` and `application.yml` for skyer-gateway.
**Learning:** Hardcoded default credentials allow attackers easy access to maintenance interfaces if the configuration is overlooked in production. Removing the hardcoded value enables the secure-by-default behavior (generating a random key).
**Prevention:** Avoid defining fallback values for secure properties in `@ConfigurationProperties` and remove such hardcoded entries from `application.yml`.
