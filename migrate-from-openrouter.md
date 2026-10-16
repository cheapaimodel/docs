# Migrate from OpenRouter

Both APIs follow the OpenAI format, so most apps switch by changing two values and the model ID.

## 1. Change the base URL and key

| | OpenRouter | CheapAIModel |
| --- | --- | --- |
| Base URL | `https://openrouter.ai/api/v1` | `https://api.cheapaimodel.ai/v1` |
| API key | `OPENROUTER_API_KEY` | `CHEAPAIMODEL_API_KEY` ([create one](https://console.cheapaimodel.ai/keys?utm_source=github&utm_medium=docs)) |

**Python**

```diff
 from openai import OpenAI

 client = OpenAI(
-    base_url="https://openrouter.ai/api/v1",
-    api_key=os.environ["OPENROUTER_API_KEY"],
+    base_url="https://api.cheapaimodel.ai/v1",
+    api_key=os.environ["CHEAPAIMODEL_API_KEY"],
 )
```

**JavaScript**

```diff
 const client = new OpenAI({
-  baseURL: "https://openrouter.ai/api/v1",
-  apiKey: process.env.OPENROUTER_API_KEY,
+  baseURL: "https://api.cheapaimodel.ai/v1",
+  apiKey: process.env.CHEAPAIMODEL_API_KEY,
 });
```

## 2. Change the model ID

OpenRouter model IDs start with a provider prefix (`moonshotai/...`, `z-ai/...`, `deepseek/...`). CheapAIModel IDs have no prefix:

| Model | CheapAIModel ID |
| --- | --- |
| Kimi K3 | `kimi-k3` |
| GLM 5.3 | `glm-5.3` |
| GLM 5.3 Flash | `glm-5.3-flash` |
| DeepSeek V4.1 Flash | `deepseek-v4-1-flash` |

Prices and the full list: [models.md](models.md). Live list: `GET /v1/models`.

Variant suffixes such as `:free` or `:nitro` are OpenRouter features; drop them.

## 3. Remove OpenRouter-only options

These are not part of the CheapAIModel API. Remove them so requests behave predictably:

| OpenRouter option | What to do |
| --- | --- |
| `HTTP-Referer` and `X-Title` headers | Remove |
| `provider` object (routing, `sort`, `order`, `allow_fallbacks`) | Remove |
| `models` array (fallback models) | Use a single `model`; handle fallback in your code |
| `transforms`, `route` | Remove |
| `reasoning: { "effort": "low" }` in Chat Completions | Use `reasoning_effort: "low"` instead ([details](https://cheapaimodel.ai/blog/deepseek-v4-1-flash-reasoning-effort?utm_source=github&utm_medium=docs)) |

## 4. Switching inside apps

In apps where you picked **OpenRouter** as the provider (Cline, Cherry Studio, SillyTavern, LobeHub...), choose the **OpenAI Compatible** or **Custom** provider instead and enter the base URL, key and model ID above. Step-by-step guides for each app: [examples/integrations](https://github.com/cheapaimodel/examples/tree/main/integrations).

## Billing

You pay per token from a prepaid balance. Top up from $5 in your [wallet](https://console.cheapaimodel.ai/wallet?utm_source=github&utm_medium=docs); there is no subscription.
