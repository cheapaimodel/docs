# Chat completions

`POST /v1/chat/completions`

## Request body

| Field | Type | Description |
| --- | --- | --- |
| `model` | string | **Required.** Model ID, see [models.md](models.md) |
| `messages` | array | **Required.** Conversation so far: `{ "role": "system" \| "user" \| "assistant" \| "tool", "content": "..." }` |
| `temperature` | number | 0–2. Higher = more creative. |
| `max_tokens` | integer | Maximum tokens to generate. |
| `stream` | boolean | Stream the response, see [streaming.md](streaming.md). |
| `tools` | array | Functions the model may call. |

## Example

```bash
curl https://api.cheapaimodel.ai/v1/chat/completions \
  -H "Authorization: Bearer $CHEAPAIMODEL_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "glm-5.3-flash",
    "temperature": 0.7,
    "messages": [
      {"role": "system", "content": "You are a helpful assistant."},
      {"role": "user", "content": "What is the capital of Vietnam?"}
    ]
  }'
```

## Response

```json
{
  "id": "chatcmpl-123",
  "object": "chat.completion",
  "model": "glm-5.3-flash",
  "choices": [
    {
      "index": 0,
      "message": { "role": "assistant", "content": "The capital of Vietnam is Hanoi." },
      "finish_reason": "stop"
    }
  ],
  "usage": { "prompt_tokens": 24, "completion_tokens": 8, "total_tokens": 32 }
}
```

You are billed for `usage.total_tokens`.
