# Codex Change Budget

这是一个 Codex 原生 skill，用来让编码 Agent 在改代码前先明确边界、风险和证据。

- `AGENTS.md` 是仓库级 Codex 操作上下文。
- `.codex-plugin/plugin.json` 是插件清单。
- `skills/change-budget/SKILL.md` 是可复用 skill。
- `instruction.md` 是可以复制到 Codex Custom Instructions 的版本。
- `EXAMPLES.md` 是 Codex 风格示例。

[English](./README.md) | 简体中文

## 核心工作流

每个非平凡任务都先形成一个轻量 ledger：

```text
Outcome:
Boundary:
Non-goals:
Risk:
Evidence:
```

然后按任务类型切换模式：

| 模式 | 用途 |
|------|------|
| Implementation | 添加行为，但不顺手发明框架。 |
| Debugging | 围绕失败形状修复最近的契约。 |
| Refactor | 改结构，同时保持行为不变。 |
| Review | 用具体证据报告风险。 |

## 在 Codex 中安装

把本仓库作为本地 Codex 插件源使用。

1. 将本仓库加入 Codex 插件源。
2. Codex 读取 `.codex-plugin/plugin.json`。
3. Codex 加载 `skills/change-budget/SKILL.md`。

插件名：

```text
andrej-karpathy-skills
```

Skill 名：

```text
change-budget
```

## 不安装也可以使用

如果不想安装插件，也不想依赖 `AGENTS.md`：

1. 打开 `instruction.md`。
2. 复制其中的 Custom Instructions 区块。
3. 粘贴到 Codex Settings -> Custom Instructions。

这个版本是自包含的，Codex 不需要额外读取仓库文件就能使用 Change Budget 工作流。

## 仓库结构

```text
.codex-plugin/plugin.json
AGENTS.md
EXAMPLES.md
instruction.md
LICENSE
README.md
README.zh.md
skills/change-budget/SKILL.md
```

## 授权

MIT
