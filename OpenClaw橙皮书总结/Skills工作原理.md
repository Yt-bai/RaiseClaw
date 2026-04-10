## Skills工作原理

**OpenClaw的Skills有三个储存位置：**

| 优先级 | 位置 | 说明 |
|---|---|---|
| 最高 | `<workspace>/skills/` | 项目级 Skills，只对当前工作区生效。适合针对特定项目定制的能力。 |
| 中 | `~/.openclaw/skills/` | 用户级 Skills，全局生效。通过 ClawHub 安装或手动放置的 Skills 都在这里。 |
| 最低 | bundled skills | 内置的 55 个 Skills，随 OpenClaw 版本发布。不需要安装，开箱即用。 |

> *如果同名Skill存在于多个层级，高优先级会覆盖低优先级。这意味着你可以在workspace级别「重写」一个内
置Skill的行为，而不影响其他项目。*

<img width="1440" height="360" alt="image" src="https://github.com/user-attachments/assets/7d3a6fa3-16e5-4c08-a325-04cf9d2f2ea2" />

## ClawHub

ClawHub是OpenClaw的官方技能注册表。

ClawHub支持向量搜索，也就是说你可以用自然语言描述需求来搜索Skill，不必精确匹配名称。

> **注意**
> 
> ClawHub的质量问题非常严重。社区项目 awesome-openclaw-skills（31.4K Stars）从13,729个技能中只精选了5,494个，剩下的大部分是垃圾、重复或低质量内容。**安装任何第三方Skill前，务必查看源码。**

### 从ClawHub中安装搜索Skills的方式

```text
# 安装Skill
openclaw skills install <skill-name>

# 搜索Skill
openclaw skills search "browser automation"

# 列出已安装的Skills
openclaw skills list

# 卸载Skill
openclaw skills uninstall <skill-name>
```

### ClawHub中的Skills分类Top10

| 排名 | 分类 | 数量 | 说明 |
|---|---|---:|---|
| 1 | 编码Agent与IDE | 1,222 | 代码生成、调试、重构等开发辅助 |
| 2 | Web与前端开发 | 938 | HTML/CSS/JS生成、组件开发 |
| 3 | DevOps与云 | 408 | Docker、K8s、CI/CD管理 |
| 4 | 搜索与研究 | 350 | 联网搜索、信息汇总 |
| 5 | 浏览器与自动化 | 335 | 网页操作、表单填写、截图 |
| 6 | 生产力与任务 | 206 | 日程、待办、项目管理 |
| 7 | AI与LLM | 197 | 提示工程、模型切换、多Agent协作 |
| 8 | CLI工具 | 186 | 终端命令增强、系统管理 |
| 9 | Git与GitHub | 170 | 仓库管理、PR审查、Issue处理 |
| 10 | 图片与视频生成 | 169 | AI绘图、视频处理 |

*编码相关的技能占了绝大多数（前两名合计2,160个），反映出OpenClaw用户中开发者占比极高。但也意味着这两个分类里重复和低质量Skill最多。*

### 其他第三方Skills平台

| 平台 | 技能数量 | 出品方 | 定位 | 支持的Agent |
|---|---:|---|---|---|
| ClawHub | 13,729 | OpenClaw 官方 | 策展市场（App Store式），有向量搜索和版本回滚 | 仅 OpenClaw |
| Skills.sh | 87,918 | Vercel | 开放市场（npm式），体量最大，跨Agent兼容 | Claude Code、Cursor、Copilot、Codex、OpenClaw等20+ |
| SkillsMP | 400,000+ | 社区 | 社区爬取 GitHub 的 `SKILL.md` 文件，数量最多但质量参差 | 通用 |
| SkillHub | 7,000+ | 社区 | 每个 Skill 有 AI 自动评分，质量控制更好 | 通用 |
| 扣子 Skills | 早期阶段 | 字节跳动 | 技能商店 + 付费变现，支持“一句话生成”技能 | 扣子 Agent |

