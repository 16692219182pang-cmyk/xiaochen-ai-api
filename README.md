# 小辰 AI · 国产大模型 API

> OpenAI 兼容接口 · DeepSeek / GLM / Kimi / MiniMax · **价格约为官方目录价 1 折起**

一个可直接接入的国产大模型 API 网关。注册即送 0.05 余额试用，OpenAI SDK / Claude Code / Cherry Studio / 各类客户端改一行 Base URL 就能用。

## ✨ 亮点

- **便宜**：按官方目录价约 1 折计费（模型组倍率 0.1x / 0.2x），缓存命中价格更低
- **模型全**：DeepSeek V4（Flash / Pro / Vision）、GLM、Kimi、MiniMax、Mimo 等主流国产模型
- **1M 上下文**：支持超长上下文与视觉输入
- **标准协议**：OpenAI 兼容，`/v1/chat/completions`、流式、函数调用都支持
- **国内直连**：国内线路入口，响应快
- **充值方便**：卡密购买、在线兑换、订单查询一条龙

## 🚀 快速开始

1. **注册**：<https://new.208314.xyz/sign-up>（邮箱验证后自动送 0.05 余额）
2. **创建 Key**：控制台 → API 密钥
3. **接入**：Base URL 换成下面的地址

```
Base URL: https://new.208314.xyz/v1
```

### curl

```bash
curl https://new.208314.xyz/v1/chat/completions \
  -H "Authorization: Bearer YOUR_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "deepseek-v4-flash-0731",
    "messages": [{"role": "user", "content": "你好！"}]
  }'
```

### Python (OpenAI SDK)

```python
from openai import OpenAI

client = OpenAI(
    api_key="YOUR_API_KEY",
    base_url="https://new.208314.xyz/v1",
)
resp = client.chat.completions.create(
    model="deepseek-v4-flash-0731",
    messages=[{"role": "user", "content": "你好！"}],
)
print(resp.choices[0].message.content)
```

## 🧠 模型与分组

| 分组 | 说明 | 模型示例 |
|---|---|---|
| `0.1x` | 国模中缓存（主力池） | deepseek-v4-flash-0731、deepseek-v4-pro、glm-5.3、kimi-k2.6、mimo-v2.5 等 18 个 |
| `0.2x` | flash稳定分组 | deepseek-v4-flash、deepseek-v4-flash-vision-exp、glm-5.3-flash |

完整模型列表见控制台「模型与价格」，或调用 `/v1/models`。

## 💰 价格说明

- 单价以 **官方目录价为基准 × 分组倍率**（0.1x / 0.2x）计算
- 例：deepseek-v4-flash 官方输入约 1.5 元/M tokens，本站约 **0.15 元/M**（0.1x 档）
- 缓存命中（相同前缀复用）按 CacheRatio 再打折，长对话/Agent 场景更省
- 模型价格以控制台实时显示为准

## 🔗 链接

- 控制台 / 注册：<https://new.208314.xyz>
- API 快速开始文档：<https://208314.xyz/api-quickstart.html>
- 卡密购买：<https://wzyp.cn/shop/7SK173VS/cvxdiu>

## ❓ 常见问题

- **余额不够**：到钱包购买卡密（面值 1–100 元），回「钱包 → 兑换」输入卡密到账
- **订单查询**：钱包页「链动订单查询」直达官方查单页（联系方式 / 订单号 + 图形验证码）
- **报错**：见文档「常见报错」一节（401 / 403 / 429 等含义与处理）

## ⚠️ 使用约定

- 请勿将 API Key 提交到公开仓库或分享给他人
- 上游偶发排队会导致首字变慢，属正常现象
- 遇到问题请联系：**QQ 3043826886**

---
*小辰 AI · 国产大模型 API 服务*
