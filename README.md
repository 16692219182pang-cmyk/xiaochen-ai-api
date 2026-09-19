# 小辰 AI · GPT API

> OpenAI 兼容接口 · GPT Luna / GPT Terra / GPT-5.5 · 按量计费

小辰 AI 是一个面向开发者的 OpenAI 兼容 GPT API 入口。已有使用 OpenAI SDK、curl 或其他兼容客户端的项目，只需要替换 Base URL，并在控制台创建自己的 API Key，即可开始调用。

## 当前服务

- OpenAI 兼容接口，支持 `chat/completions` 与流式调用
- 当前提供 GPT Luna、GPT Terra 和 GPT-5.5
- 输入、输出、缓存读取、缓存写入分开计费
- 控制台创建和管理 API Key
- 注册后可进入控制台查看模型、分组和使用记录
- 提供在线接入文档与卡密充值

## 快速开始

1. 注册账号：<https://api.208314.xyz/register>
2. 完成邮箱验证并登录控制台
3. 在「API 密钥」页面创建 API Key
4. 在客户端中将 Base URL 设置为：

```text
https://api.208314.xyz/v1
```

完整接入说明：<https://api.208314.xyz/api-quickstart.html>

## 当前模型与分组

| 分组 | 倍率 | 模型 |
|---|---:|---|
| GPT Luna | `0.25×` | `gpt-5.6-luna` |
| GPT Terra | `0.049×` | `gpt-5.6-terra`、`gpt-5.5` |

完整可用模型以登录后控制台及 `/v1/models` 返回为准。

## 客户实际价格

以下为已经包含分组倍率的客户实际价格，单位为 USD / 1M tokens：

| 分组 / 模型 | 输入 | 缓存读取 | 缓存写入 | 输出 |
|---|---:|---:|---:|---:|
| GPT Luna / `gpt-5.6-luna` | `$0.05` | `$0.005` | `$0.0625` | `$0.30` |
| GPT Terra / `gpt-5.6-terra` | `$0.098` | `$0.0098` | `$0.1225` | `$0.588` |
| GPT Terra / `gpt-5.5` | `$0.245` | — | — | `$1.47` |

账单按输入、缓存读取、缓存写入和输出四类 token 分开计算，最终以控制台使用记录为准。

## 调用示例

### curl

```bash
curl https://api.208314.xyz/v1/chat/completions \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "gpt-5.6-luna",
    "messages": [
      {"role": "user", "content": "你好，请用一句话介绍自己。"}
    ],
    "stream": false
  }'
```

### Python · OpenAI SDK

```python
from openai import OpenAI

client = OpenAI(
    api_key="YOUR_API_KEY",
    base_url="https://api.208314.xyz/v1",
)

response = client.chat.completions.create(
    model="gpt-5.6-luna",
    messages=[{"role": "user", "content": "你好"}],
)

print(response.choices[0].message.content)
```

## 充值

卡密购买入口：<https://pay.ldxp.cn/shop/7SK173VS>

当前可见面值：`1 / 3 / 5 / 10 / 20 / 50 / 100 元`。

购买后回到控制台，在「钱包 → 兑换」输入卡密。购买和兑换是两个步骤。

## 常见问题

### API Key 放在哪里？

只放在自己的环境变量、服务端配置或本地客户端中，不要提交到公开仓库、日志或聊天记录。

### 模型列表在哪里看？

登录控制台查看，或使用有效 API Key 请求：

```text
GET https://api.208314.xyz/v1/models
```

### 为什么首字速度会变化？

请求延迟会受到模型、上游调度、并发和临时排队影响。遇到偶发 429/5xx 时，可以降低并发并稍后重试，避免无间隔重复请求。

### 遇到 401 或余额不足怎么办？

确认请求使用了正确的 `Authorization: Bearer YOUR_API_KEY`，并检查控制台余额、API Key 状态和对应分组权限。

## 相关链接

- 首页：<https://api.208314.xyz/home>
- 登录：<https://api.208314.xyz/login>
- 注册：<https://api.208314.xyz/register>
- API 快速开始：<https://api.208314.xyz/api-quickstart.html>
- 充值入口：<https://pay.ldxp.cn/shop/7SK173VS>

---

*小辰 AI · GPT API 聚合服务*
