## 国产Claw

> OpenClaw爆火后，国内大厂纷纷推出自己的「龙虾」产品。有的基于OpenClaw封装降门槛，有的完全自研。截至2026年3月11日，市面上至少有10款以上的产品可选。

| 阵营 | 原理 | 优势 | 劣势 | 代表产品 |
|---|---|---|---|---|
| OpenClaw 封装版 | 基于 OpenClaw 开源代码，加上自家模型和一键部署 | 与 OpenClaw 生态兼容，Skills 通用，社区资源可复用 | 更新可能滞后于官方版本，安全漏洞需等上游修复 | QClaw、MaxClaw、KimiClaw、AutoClaw、ArkClaw |
| 独立自研版 | 自研 Agent 框架，不依赖 OpenClaw 代码 | 可深度优化，与自家生态整合更紧密 | 不兼容 ClawHub Skills 生态，需要独立建设 | miclaw（小米）、LobsterAI（网易有道）、CoPaw（阿里） |

**具体对比：**

| 产品 | 公司 | 形态 | 基于 OpenClaw | 默认模型 | 价格 | 核心卖点 |
|---|---|---|---|---|---|---|
| MaxClaw | MiniMax | 云端 | 是 | MiniMax M2.5 | ¥39/月起 | 18 秒部署，价格最低，飞书 5 分钟接入 |
| AutoClaw | 智谱 AI | 客户端 | 是 | GLM-5 / Pony-Alpha-2 | 免费 + 积分 | 96 个预置 Skills，AutoGLM 浏览器自动化，一键安装 |
| QClaw | 腾讯（电脑管家团队） | 客户端 | 是 | DeepSeek / Kimi / GLM 等多模型 | 全量公测，免费 | 微信 / QQ 直连，一键安装，灵感广场，仅 macOS |
| ArkClaw | 字节 / 火山引擎 | 云端 SaaS | 是 | Seed 2.0 等多模型 | Coding Plan Pro 附赠 | 开箱即用，飞书深度适配 |
| KimiClaw | 月之暗面 | 云端 | 是 | Kimi K2.5 | ¥199/月（含会员） | Kimi 生态整合 |
| WorkBuddy | 腾讯（自研，非 OpenClaw fork） | 客户端 | 兼容 Skills | 混元 / DeepSeek / GLM 等 | 免费（5000 Credits） | 自研智能体，微信直连，企业微信适配，T 半自动，安全哲学 |
| LobsterAI | 网易有道 | 开源客户端 | 否，自研 | 多模型可选 | 免费开源 | GUI 界面，沙箱隔离，Office 能力强 |
| CoPaw | 阿里通义 | 开源 | 否，自研 | Qwen 系列 / Ollama 等 | 免费开源 | 端云双部署，钉钉 / 飞书 / QQ 多频道 |
| miclaw | 小米 | 移动端 | 否，自研 | MiMo | 3 月 19 日开放免费体验 | 手机原生运行，米家 IoT 生态，101 亿 + 设备 |

<img width="651" height="389" alt="image" src="https://github.com/user-attachments/assets/57df771f-db90-4374-963f-33f54f551c82" />

> QClaw 是在你电脑上装一只龙虾（产品），ClawBot 是让你从微信里和已有的龙虾说话（渠道）。两者可以配合使用——用 QClaw 装好龙虾，再用 ClawBot 从手机微信远程操控它。

> WorkBuddy 的负责人在接受采访时明确表示「WorkBuddy 不是 OpenClaw」，技术路线完全自研。但它兼容ClawHub 的 Skills 生态，用户可以直接安装社区技能。这是一个有趣的策略：自研框架 + 借用生态。
>
> 但是 QClaw 就是OpenClaw包装出的产品。

**各种具体的国产Claw选购指南可以翻阅橙皮书地35章节**
