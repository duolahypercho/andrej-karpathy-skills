# Codex 外科式编码纪律

这是一个 Codex 原生技能包，用来让编码 Agent 更谨慎、更小步、更可验证。

- `AGENTS.md` 是仓库级 Codex 操作上下文。
- `.codex-plugin/plugin.json` 是插件清单。
- `skills/surgical-coding-discipline/SKILL.md` 是可复用技能。
- `EXAMPLES.md` 是 Codex 风格示例。

[English](./README.md) | 简体中文

## 为什么需要它

编码 Agent 最容易犯的错误不是不会写代码，而是：

- 没有说清楚假设就开始改。
- 把小需求做成大架构。
- 顺手修改了无关代码。
- 没有定义真正能证明结果的检查方式。

这个 skill 的目标是给 Codex 一个简单的工作纪律：先框定问题，再缩小改动，最后证明结果。

## 四个习惯

| 习惯 | 避免的问题 |
|------|------------|
| 先框定请求 | 隐藏假设和隐藏困惑 |
| 偏向最小可用改动 | 过早抽象和复杂 API |
| 只碰任务表面 | 顺手重构和格式漂移 |
| 证明结果 | 只凭感觉判断改好了 |

## 在 Codex 中安装

把本仓库作为本地 Codex 插件源使用。

1. 将本仓库加入 Codex 插件源。
2. Codex 读取 `.codex-plugin/plugin.json`。
3. Codex 加载 `skills/surgical-coding-discipline/SKILL.md`。

插件名：

```text
andrej-karpathy-skills
```

技能名：

```text
surgical-coding-discipline
```

## 仓库结构

```text
.codex-plugin/plugin.json
AGENTS.md
EXAMPLES.md
LICENSE
README.md
README.zh.md
skills/surgical-coding-discipline/SKILL.md
```

## 授权

MIT
