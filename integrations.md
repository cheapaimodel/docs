# Using CheapAIModel with other tools

Any tool that lets you set a custom **OpenAI base URL** works with CheapAIModel.

Use these values:

- **Base URL:** `https://api.cheapaimodel.com/v1`
- **API key:** your CheapAIModel key
- **Model:** any ID from [models.md](models.md)

## LangChain (Python)

```python
from langchain_openai import ChatOpenAI

llm = ChatOpenAI(
    model="gpt-4o-mini",
    base_url="https://api.cheapaimodel.com/v1",
    api_key="your-key",
)
```

## Vercel AI SDK

```ts
import { createOpenAI } from "@ai-sdk/openai";
import { generateText } from "ai";

const cheapaimodel = createOpenAI({
  baseURL: "https://api.cheapaimodel.com/v1",
  apiKey: process.env.CHEAPAIMODEL_API_KEY,
});

const { text } = await generateText({
  model: cheapaimodel("gpt-4o-mini"),
  prompt: "Hello!",
});
```

## Apps with an "OpenAI-compatible" setting

Many chat apps, IDE extensions and automation tools have an "OpenAI-compatible" or "custom provider" option. Paste the base URL and key above.
