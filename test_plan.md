1. **Remove hardcoded Baison credentials in `skyer-order`:**
   - Modify `./skyer-order/src/main/resources/application.yml` to remove the hardcoded `key` and `secret` for `baison`.
   - Use environment variables with null defaults instead: `key: ${BAISON_KEY:}` and `secret: ${BAISON_SECRET:}`.
2. **Remove hardcoded gateway secrets in `skyer-gateway`:**
   - Modify `./skyer-gateway/src/main/resources/application.yml` to remove the hardcoded `secretKey` and `jwt-key`.
   - Update `secretKey` to `${SKYER_GATEWAY_SECRET_KEY:}` and `jwt-key` to `${SKYER_GATEWAY_JWT_KEY:}`.
   - Update `secret-key` (运维接口密钥) to `${SKYER_GATEWAY_MAINTAIN_SECRET_KEY:}`.
3. **Verify changes:**
   - Ensure the application loads properly and tests pass without exposing these secrets in the configuration files.
4. **Pre-commit checks:**
   - Run the pre-commit instructions to ensure everything is verified and proper checks are done.
5. **Submit PR:**
   - Commit the changes and create a PR with the security fixes.
