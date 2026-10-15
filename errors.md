# Errors & rate limits

Errors use standard HTTP status codes and an OpenAI-style body:

```json
{ "error": { "message": "Invalid API key", "type": "invalid_request_error", "code": 401 } }
```

| Status | Meaning | What to do |
| --- | --- | --- |
| 400 | Bad request | Check the request body and model ID |
| 401 | Invalid or missing API key | Check the `Authorization` header |
| 402 | Out of credit | Top up your balance |
| 404 | Model not found | Check [models.md](models.md) |
| 429 | Too many requests | Slow down and retry with backoff |
| 500 / 502 / 503 | Server or upstream error | Retry after a few seconds |

## Retrying

The OpenAI SDKs (and our SDKs) retry 429 and 5xx errors automatically. Configure it with `max_retries` (Python) or `maxRetries` (JS).
