# Quickstart

## 1. Get an API key

Sign up at [cheapaimodel.ai](https://cheapaimodel.ai?utm_source=github&utm_medium=docs) and create a key on the [API keys page](https://console.cheapaimodel.ai/keys?utm_source=github&utm_medium=docs).

```bash
export CHEAPAIMODEL_API_KEY="your-key"
```

## 2. Make your first request

**Python**

```python
from openai import OpenAI

client = OpenAI(base_url="https://api.cheapaimodel.ai/v1", api_key="your-key")
res = client.chat.completions.create(
    model="glm-5.3-flash",
    messages=[{"role": "user", "content": "Hello!"}],
)
print(res.choices[0].message.content)
```

**JavaScript**

```js
import OpenAI from "openai";

const client = new OpenAI({ baseURL: "https://api.cheapaimodel.ai/v1", apiKey: "your-key" });
const res = await client.chat.completions.create({
  model: "glm-5.3-flash",
  messages: [{ role: "user", content: "Hello!" }],
});
console.log(res.choices[0].message.content);
```

## 3. Next steps

- Stream responses → [streaming.md](streaming.md)
- Pick a model → [models.md](models.md)
- More examples → [cheapaimodel/examples](https://github.com/cheapaimodel/examples)
- Coming from OpenRouter? → [migrate-from-openrouter.md](migrate-from-openrouter.md)
