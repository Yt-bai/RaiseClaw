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

> **注意：**
> 
> ClawHub的质量问题非常严重。社区项目 awesome-openclaw-skills（31.4K Stars）从13,729个技能中只精选了5,494个，剩下的大部分是垃圾、重复或低质量内容。**安装任何第三方Skill前，务必查看源码。**
