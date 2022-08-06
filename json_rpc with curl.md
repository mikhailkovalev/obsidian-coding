#curl #json #jsonrpc #json-rpc

```bash
curl \
    -u invest:${CRYPTO_MS_PASSWORD} \
    -X POST $CRYPTO_MS_ADDR/api/v3/internal \
    -H 'Content-Type: application/json' \
    -d '
    {
        "jsonrpc": "2.0",
        "method": "users_get_by_customer_code",
        "id": "fd50524a-9c61-4246-91cc-f3dd9378db5f",
        "params": {
            "customer_code": "301348318"
        }
    }
    '
```