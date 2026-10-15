# Streaming

Set `"stream": true` to receive the answer token by token, using Server-Sent Events. This makes chat apps feel much faster.

```python
stream = client.chat.completions.create(
    model="glm-5.3-flash",
    messages=[{"role": "user", "content": "Tell me a story"}],
    stream=True,
)
for chunk in stream:
    if chunk.choices and chunk.choices[0].delta.content:
        print(chunk.choices[0].delta.content, end="")
```

Each event looks like:

```
data: {"choices":[{"delta":{"content":"Once"}}]}
```

The stream ends with:

```
data: [DONE]
```
