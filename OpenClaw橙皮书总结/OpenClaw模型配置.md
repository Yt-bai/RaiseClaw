## OpenClaw模型提供商
OpenClaw支持十余家模型提供商，从国际顶尖到国产平价再到完全免费的本地模型，覆盖所有预算和场景。

OpenClaw最大的优势之一是模型自由：你不被绑定在某一家厂商上。通过 ~/.openclaw/openclaw.json 配置文件，可以灵活切换主力模型、设置Fallback备选链、甚至让不同任务走不同模型。

| 提供商 | 代表模型 | 输入价格 / 1M tokens | 输出价格 / 1M tokens | 接入方式 | 推荐场景 |
|---|---|---:|---:|---|---|
| Anthropic | Claude Sonnet 4.6 | $3.00 | $15.00 | 内置 Provider | Agent 任务效果最佳 |
| OpenAI | GPT-5.4 | $2.50 | $15.00 | 内置 Provider | 通用能力强 |
| Google | Gemini 3 Pro | $2.00 | $12.00 | 内置 Provider | 多模态、超长上下文 |
| DeepSeek | DeepSeek-V3.2.2 / V4 | $0.14 | $0.28 | 自定义 Provider | 极致低价、代码任务 |
| 智谱 GLM | GLM-5 | $0.80 | $2.56 | 内置（zai） | 国产最强代码能力 |
| 智谱 GLM | GLM-5-Turbo | $0.96 | $3.20 | 内置（zai） | 国内首个专为 OpenClaw 训练优化的模型 |
| 通义千问 | Qwen 3.5 Max | $1.20 | $6.00 | 插件（OAuth） | 中文 NLP、代码生成 |
| 豆包 | Seed 2.0 Pro | $0.47 | $2.37 | 自定义 Provider | 批量处理、低成本 |
| 百度文心 | 文心 5.0 | ~$0.58 | ~$1.16 | 自定义（需适配） | 百度云生态用户 |
| Kimi | Kimi K2.5 | $0.60 | $3.00 | 自定义 Provider | 中文 Agent、长上下文 |
| MiniMax | MiniMax M2.5 | $0.50 | $2.00 | 自定义 Provider | SWE-bench 高分、性价比 |
| Ollama | Qwen3.5-Coder:32B | 免费 | 免费 | 自动发现 | 隐私敏感、零成本 |
| LM Studio | Devstral-24B | 免费 | 免费 | 自定义 Provider | 本地 GUI、模型测试 |

**模型配置的三个核心概念**

一、内置Provider：Anthropic、OpenAI、Google、智谱（zai）等无需额外配置，设置API Key即可使用；

二、自定义Provider：DeepSeek、豆包、Kimi等需要在 models.providers 中手动添加；

三、Fallback机制：主模型不可用时自动切换到备选，这是最核心的省钱策略。





