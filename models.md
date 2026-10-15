# Models

Get the live list of available models:

```bash
curl https://api.cheapaimodel.com/v1/models \
  -H "Authorization: Bearer $CHEAPAIMODEL_API_KEY"
```

<!-- TODO: replace the table below with your real models and prices -->

| Model ID | Good for | Context | Input / 1M tokens | Output / 1M tokens |
| --- | --- | --- | --- | --- |
| `gpt-4o-mini` | Fast, cheap everyday tasks | 128K | $— | $— |
| `model-id-2` | — | — | $— | $— |
| `model-id-3` | — | — | $— | $— |

Prices may change; see [cheapaimodel.com](https://cheapaimodel.com) for the current list.

## Choosing a model

- **Chatbots, summaries, simple tasks:** pick the cheapest fast model.
- **Coding, reasoning, long documents:** pick a larger model with a longer context window.
- Not sure? Start cheap and move up only if the quality isn't good enough.
