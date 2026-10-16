# Models

Get the live list of available models:

```bash
curl https://api.cheapaimodel.ai/v1/models \
  -H "Authorization: Bearer $CHEAPAIMODEL_API_KEY"
```

| Model ID | Input / 1M tokens | Output / 1M tokens | Official price (in / out) |
| --- | --- | --- | --- |
| `kimi-k3` | $2.85 | $14.25 | $3.00 / $15.00 |
| `glm-5.3` | $1.33 | $4.18 | $1.40 / $4.40 |
| `glm-5.3-flash` | $0.1425 | $0.475 | $0.15 / $0.50 |
| `deepseek-v4-1-flash` | $0.285 | $1.14 | $0.30 / $1.20 |

Every model is 5% below the official list price. You pay per token: no subscription, top up from $5.

Prices may change; the [model catalog](https://cheapaimodel.ai/models?utm_source=github&utm_medium=docs) always has the current list.

## Choosing a model

- **Chatbots, summaries, simple tasks:** `glm-5.3-flash` or `deepseek-v4-1-flash`.
- **Coding, reasoning, harder tasks:** `glm-5.3` or `kimi-k3`.
- Not sure? Start with a flash model and move up only if the quality isn't good enough.
