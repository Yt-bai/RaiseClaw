<img width="1026" height="405" alt="image" src="https://github.com/user-attachments/assets/e7b2a0a7-a803-4442-89be-baa68d8aa3c6" />## OpenClaw模型提供商
**模型配置的三个核心概念**

- 1. 内置Provider：Anthropic、OpenAI、Google、智谱（zai）等无需额外配置，设置API Key即可使用；

- 2. 自定义Provider：DeepSeek、豆包、Kimi等需要在 models.providers 中手动添加；

- 3. Fallback机制：主模型不可用时自动切换到备选，这是最核心的省钱策略。
  
*注：*

- **Provider = “模型供应商/接入通道”**
- **Fallback = “主模型失败时的备用顺序”**

而 内置 Provider 和 自定义 Provider 都只是 Provider 的两种来源；Fallback 不是第三类 Provider，而是“从这些 Provider 里的模型里，指定一个候补链”。

---

OpenClaw支持十余家模型提供商，从国际顶尖到国产平价再到完全免费的本地模型，覆盖所有预算和场景。

OpenClaw最大的优势之一是模型自由：你不被绑定在某一家厂商上。通过 ~/.openclaw/openclaw.json 配置文件，可以灵活切换主力模型、设置Fallback备选链、甚至让不同任务走不同模型。

---

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


```text
{
 env: { "API_KEY_NAME": "sk-xxx" },
 agents: {
 defaults: {
 model: {
 primary: "provider/model-name", // 主⼒模型
 fallbacks: ["provider/model-b"] // 备选（主模型限速时⾃动切换）
 }
 }
 },
 models: {
 mode: "merge", // 保留内置provider，叠加⾃定义
 providers: { /* ⾃定义provider配置 // }
 }
}
```

## 国际模型对比
Anthropic Claude VS OpenAI GPT VS Google Gemini，全部是OpenClaw**内置模型**。

**Anthropic Claude**

> OpenClaw默认模型提供商
>
> Agent任务效果最好
>
> 工具调用准确稳定

| 模型 | 输入 / 1M | 输出 / 1M | 上下文 | 定位 |
|---|---:|---:|---:|---|
| Claude Opus 4.6 | $5.00 | $25.00 | 200K | 最强推理，复杂任务 |
| Claude Sonnet 4.6 | $3.00 | $15.00 | 200K | 主力模型，性价比之选 |
| Claude Haiku 4.5 | $1.00 | $5.00 | 200K | 轻量任务，高速低成本 |

**OpenAI GPT**

| 模型 | 输入 / 1M | 输出 / 1M | 上下文 | 定位 |
|---|---:|---:|---|---|
| GPT-5.4 | $2.50 | $15.00 | 272K（标准） | 最新旗舰 |
| GPT-5.4（>272K） | $5.00 | $15.00 | 1.05M | 超长上下文 |
| GPT-5.2 | $1.75 | $14.00 | — | 上一代旗舰 |
| GPT-5 | $1.25 | $10.00 | — | 性价比之选 |

**Google Gemini**

> 2M上下文窗口
>
> 慷慨的免费额度
>
> 多模态能力最强

| 模型 | 输入 / 1M | 输出 / 1M | 上下文 | 定位 |
|---|---:|---:|---|---|
| Gemini 3 Pro（<=200K） | $2.00 | $12.00 | 200K | 旗舰多模态 |
| Gemini 3 Pro（>200K） | $4.00 | $18.00 | 2M | 超长上下文 |
| Gemini 3 Flash | $0.50 | $3.00 | — | 高速低成本 |

## 国产模型对比
主打一个省钱

**Deepseek：自定义Provider**

> 性价比之王

| 模型 | 输入 / 1M | 输出 / 1M | 定位 |
|---|---:|---:|---|
| DeepSeek-V3.2.2（deepseek-chat） | $0.14 | $0.28 | 当前稳定版，极致低价 |
| DeepSeek-R1（deepseek-reasoner） | $0.55~0.70 | $2.19~2.50 | 深度推理 |

**智谱AI：内置Provider**

> 国产模型中代码能力最强

| 模型 | 输入 / 1M | 输出 / 1M | 定位 |
|---|---:|---:|---|
| GLM-5-Turbo | $0.96 | $3.20 | 首个专为 OpenClaw 优化的基座模型 |
| GLM-5 | $0.80 | $2.56 | 旗舰，代码能力强 |
| GLM-4.5 | $0.60 | $2.20 | 上一代主力 |
| GLM-4.7-Flash | 免费 | 免费 | 轻量免费 |
| GLM-4.5-Flash | 免费 | 免费 | 轻量免费 |

*此外，还有阿里Qwen，豆包，百度文心，月之暗面Kimi、MaxMini等。*

## Coding Plan 包月套餐（无需自己管理API和担心Token余额）

相比按量付费的API，包月套餐的优势是成本可预期、无需管理API Key余额，尤其适合个人开发者和轻度到中度使用者。

> 厂商自营Coding Plan

| 厂商 | 套餐档位 | 月费 | 模型 | 特色 / 限制 |
|---|---|---:|---|---|
| 智谱 GLM | Lite | ~49元 | GLM-4.7 | MCP 联网 100 次 / 月 |
| 智谱 GLM | Pro | ~80元 | GLM-4.7 | 速度快 40-60%，MCP 1000 次 / 月 |
| 智谱 GLM | Max | ~160元 | GLM-4.7 + GLM-5 | 唯一含 GLM-5，MCP 4000 次 / 月 |
| 智谱 GLM | 龙虾体验卡 | 39元 | GLM-5-Turbo | 3500 万 tokens / 月，OpenClaw 专项优化 |
| 智谱 GLM | 龙虾进阶卡 | 99元 | GLM-5-Turbo | 1 亿 tokens / 月，OpenClaw 专项优化 |
| Kimi | Andante | 49元 | Kimi K2.5 | 基础档，Token 计量 |
| Kimi | Moderato | 99元 | Kimi K2.5 | 中档 |
| Kimi | Allegretto | 199元 | Kimi K2.5 | 每 5 小时 100-500 次请求 |
| MiniMax | Starter | 29元 | M2.5 | 无每周限额，性价比高 |
| MiniMax | Standard | 49元 | M2.5 | 年付省 17% |
| MiniMax | Premium | 119元 | M2.5 | 重度用户 |

> 云聚合Coding Plan

| 平台 | 档位 | 原价 / 月 | 首月优惠 | 包含模型 | 用量 |
|---|---|---:|---:|---|---|
| 阿里云百炼 | Lite | 40元 | 7.9元 | Qwen + GLM + Kimi + MiniMax | ~18,000次 / 月 |
| 阿里云百炼 | Pro | 200元 | 39.9元 | 同上 | ~90,000次 / 月 |
| 腾讯云 | Lite | 40元 | 7.9元 | 混元2.0 + GLM-5 + Kimi K2.5 + M2.5 | 每5h ~1,200次 |
| 腾讯云 | Pro | 200元 | 39.9元 | 同上 | 每5h ~6,000次 |
| 火山引擎 | Lite | 40元 | 8.91元 | 豆包Code + GLM-4.7 + DeepSeek-V3.2.2 + Kimi | 每5h ~1,200次 |
| 火山引擎 | Pro | 200元 | 44.91元 | 同上 | 每5h ~6,000次 |

选型建议：

首月体验（7.9元起）：阿里云百炼或腾讯云 Lite 档，首月仅7.9元，包含4家模型自由切换，是零风险的入门方式。

长期性价比：MiniMax Starter（29元/月）无每周限额，M2.5代码能力强；如果需要多模型切换，云平台续费5折（约20元/月）也很划算。

追求最强单模型：智谱Max（160元/月）是目前唯一包含GLM-5的自营套餐；腾讯云也新增了GLM-5支持。

重度用户：Coding Plan普遍有频率限制（每5小时N次），如果你需要高频调用，建议直接使用API按量付费，搭配Fallback链控制成本。

## 本地模型

| 模型 | 参数量 | 推荐场景 | 最低内存 |
|---|---:|---|---|
| Qwen3.5-Coder:32B | 32B | 代码生成、Agent任务 | 32GB RAM |
| Devstral-24B | 24B | Agent / 工具调用 | 32GB RAM |
| Qwen 2.5:32B | 32B | 通用任务 | 32GB RAM |
| DeepSeek-R1:14B | 14B | 推理任务 | 16GB RAM |
| Llama 3.3 | 8B-70B | 通用任务 | 16-64GB RAM |

*注：硬件要求*

*运行3-7B参数模型最低需要16GB RAM。运行32B参数模型推荐32GB RAM。如果有 NVIDIA/Apple Silicon GPU 会显著加速推理。*

---

## 五套推荐方案

```text
方案一：极致省钱（月均<$5）
主力：DeepSeek-V3.2（$0.14/$0.28）
备选：Qwen 3.5 Plus（$0.40/$1.20）
心跳/Cron：GLM-4.5-Flash（免费）
推理任务：DeepSeek-R1（$0.55/$2.19）
适合：个人开发者、学习探索。风险：DeepSeek高峰期延迟，需Fallback兜底。
```

```text
方案二：国产性价比（月均$5-15）
主力：GLM-5（$0.80/$2.56）
备选：DeepSeek-V3.2（$0.14/$0.28）
推理增强：Kimi K2.5（$0.60/$3.00）
简单任务：GLM-4.5-Flash（免费）
适合：国内用户，追求中文体验和稳定性。GLM-5代码能力强，延迟低。
```

```text
方案三：国际平衡（月均$10-30）
主力：Claude Sonnet 4.6（$3.00/$15.00）
轻量：Claude Haiku 4.5 或 Gemini Flash
复杂任务：Claude Opus 4.6（按需升级）
心跳/Cron：Gemini Flash（免费额度）
适合：追求Agent效果最优、预算充足。Claude在Agent/工具调用场景效果最好。
```

```text
方案四：混合最优（月均$5-20，推荐）
复杂任务：Claude Sonnet 4.6
日常对话：DeepSeek-V3.2
心跳/定时：Gemini Flash 或本地 Ollama
Fallback链：Sonnet → Haiku → DeepSeek-V3.2
大多数用户的最佳选择。兼顾效果和成本，Fallback机制自动处理限速。
```

```text
方案五：完全免费
选项A：本地 Ollama + Qwen3.5-Coder:32B 或 Devstral-24B（需32GB RAM）
选项B：免费API组合 — GLM-4.5-Flash + ERNIE Speed + Gemini Flash
适合：隐私敏感、纯实验用途。本地方案需要较好的硬件。
```

---

## 价格速查（从低到高排序）

| # | 模型 | 输入 | 输出 | 一句话评价 |
|---|---|---:|---:|---|
| — | Ollama / LM Studio | 免费 | 免费 | 仅消耗本地算力 |
| — | GLM Flash / ERNIE Speed | 免费 | 免费 | 云端免费 tier |
| 1 | Doubao 1.5 Lite-32k | $0.042 | — | 最便宜云端对话 |
| 2 | Qwen3 8B | $0.05 | $0.40 | 轻量低成本 |
| 3 | DeepSeek-V3.2 | $0.14 | $0.28 | 性价比之王 |
| 4 | Qwen3 Coder 480B | $0.22 | $1.00 | 代码专用性价比 |
| 5 | Qwen 3.5 Plus | $0.40 | $1.20 | 平衡之选 |
| 6 | Doubao Seed 2.0 Pro | $0.47 | $2.37 | 国产旗舰 |
| 7 | Gemini 3 Flash | $0.50 | $3.00 | 国际低价 |
| 8 | Kimi K2.5 | $0.60 | $3.00 | 中文旗舰 |
| — | GLM-5-Turbo | $0.96 | $3.20 | 首个 OpenClaw 专项优化模型 |
| 9 | GLM-5 | $0.80 | $2.56 | 国产代码最强 |
| 10 | Claude Haiku 4.5 | $1.00 | $5.00 | 国际轻量 |
| 11 | Gemini 3 Pro | $2.00 | $12.00 | Google 旗舰 |
| 12 | GPT-5.4 | $2.50 | $15.00 | OpenAI 旗舰 |
| 13 | Claude Sonnet 4.6 | $3.00 | $15.00 | Agent 效果最佳 |
| 14 | Claude Opus 4.6 | $5.00 | $25.00 | 最强也最贵 |

---

## 模型配置要点速查

| 操作 | 命令 / 配置 |
|---|---|
| 引导式配置 | `openclaw onboard` |
| 查看已配置模型 | `openclaw models list` |
| 测试连通性 | `openclaw models status --probe` |
| 设置主力模型 | `openclaw config set agents.defaults.model.primary provider/model` |
| 添加 Fallback | 编辑 `openclaw.json` 的 `fallbacks` 数组 |
| 重启网关 | `openclaw gateway restart`（改配置后必须执行） |
| 环境变量引用 | 配置中用 `"${VAR_NAME}"` 引用 `env` 中的变量 |

---


