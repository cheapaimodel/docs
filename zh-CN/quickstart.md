# 快速开始

[English](../quickstart.md) | 简体中文

CheapAIModel 兼容 OpenAI 接口：只需修改 base URL 和 API Key，现有的 OpenAI SDK 和工具即可直接使用。

## 1. 获取 API Key

在 [cheapaimodel.ai](https://cheapaimodel.ai/?utm_source=github&utm_medium=docs-zh) 注册，并在 [API Keys 页面](https://console.cheapaimodel.ai/keys?utm_source=github&utm_medium=docs-zh) 创建密钥。

```bash
export CHEAPAIMODEL_API_KEY="your-key"
```

## 2. 发送第一个请求

**Python**

```python
from openai import OpenAI

client = OpenAI(base_url="https://api.cheapaimodel.ai/v1", api_key="your-key")
res = client.chat.completions.create(
    model="glm-5.3-flash",
    messages=[{"role": "user", "content": "你好！"}],
)
print(res.choices[0].message.content)
```

**JavaScript**

```js
import OpenAI from "openai";

const client = new OpenAI({ baseURL: "https://api.cheapaimodel.ai/v1", apiKey: "your-key" });
const res = await client.chat.completions.create({
  model: "glm-5.3-flash",
  messages: [{ role: "user", content: "你好！" }],
});
console.log(res.choices[0].message.content);
```

**cURL**

```bash
curl https://api.cheapaimodel.ai/v1/chat/completions \
  -H "Authorization: Bearer $CHEAPAIMODEL_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"model":"glm-5.3-flash","messages":[{"role":"user","content":"你好！"}]}'
```

## 3. 模型与价格

| 模型 ID | 输入 / 百万 tokens | 输出 / 百万 tokens |
| --- | --- | --- |
| `kimi-k3` | $2.85 | $14.25 |
| `glm-5.3` | $1.33 | $4.18 |
| `glm-5.3-flash` | $0.1425 | $0.475 |
| `deepseek-v4-1-flash` | $0.285 | $1.14 |

所有模型均比官方价格低 5%。按 token 计费，无订阅，最低充值 $5。最新列表见 [模型目录](https://cheapaimodel.ai/models?utm_source=github&utm_medium=docs-zh)。

## 4. 在常用工具中使用

在 Cline、Cherry Studio、LobeChat、SillyTavern、OpenClaw 等工具中，选择 **OpenAI Compatible**（或"自定义服务商"），然后填写：

| 设置 | 值 |
| --- | --- |
| Base URL | `https://api.cheapaimodel.ai/v1` |
| API Key | 你的 CheapAIModel 密钥 |
| 模型 ID | 例如 `glm-5.3-flash` |

各工具的详细步骤（英文）：[examples/integrations](https://github.com/cheapaimodel/examples/tree/main/integrations)

## 5. 从 OpenRouter 迁移

把 base URL 改为 `https://api.cheapaimodel.ai/v1`，换成 CheapAIModel 的 Key，并把模型 ID 改为不带前缀的形式（例如 `deepseek-v4-1-flash`）。完整说明（英文）：[migrate-from-openrouter.md](../migrate-from-openrouter.md)
