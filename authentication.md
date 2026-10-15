# Authentication

Every request needs your API key in the `Authorization` header:

```
Authorization: Bearer YOUR_CHEAPAIMODEL_KEY
```

## Keeping your key safe

- Store it in an environment variable or a secrets manager, never in source code.
- Never call the API directly from a browser or mobile app — your key would be visible to users. Call it from your own backend instead.
- Add `.env` to your `.gitignore`.
- If a key leaks, revoke it in your dashboard and create a new one right away.
