# GOS P2P Database

## Distributed culinary review data by country

### Structure

```
sync/                          - Bootstrap peer registry
ingredients/{country}/         - Ingredient data files
dishes/{country}/              - Dish data files
reviews/{COUNTRY}/             - Review data (capped per user)
users/{COUNTRY}/               - User profile stubs (hashed)
products/{COUNTRY}/            - Product data
voters/{COUNTRY}/              - Voter registry
```

### Countries

| Code | Country | Language | API |
|------|---------|----------|-----|
| CO | Colombia | es | - |
| PE | Perú | es | - |
| MX | México | es | - |
| AR | Argentina | es | - |
| US | Estados Unidos | en | - |
| CN | China | zh | - |

### Sync Protocol

- Bootstrap list: `sync/_bootstrap.json`
- Each peer writes: `sync/peers/{peerId}/info.json`
- Sync triggers: X reviews threshold OR daily timeout

### Security

- Only SHA-256 hashes stored (no plain PII)
- Reviews signed with RSA-PSS
- Voter trust scoring (0-100)
- Identity only stored as hashes
