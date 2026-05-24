# Karpathy 启发的 Codex Skill

这是一个 Codex 原生技能包，来自 Andrej Karpathy 对 LLM 编码常见问题的观察。

本仓库使用：

- `.codex-plugin/plugin.json`：Codex 插件清单。
- `AGENTS.md`：仓库级 Codex 操作上下文。
- `skills/karpathy-guidelines/SKILL.md`：可复用技能说明。
- `EXAMPLES.md`：四个原则的实践示例。

[English](./README.md) | 简体中文

## 解决的问题

LLM 编码 Agent 经常出现三类问题：

- 做太多隐藏假设。
- 把简单任务做复杂。
- 在解决问题时改动无关代码。

## 技能原则

`karpathy-guidelines` 技能包含四个原则：

| 原则 | 作用 |
|------|------|
| Think Before Coding | 暴露假设、困惑、替代方案和权衡。 |
| Simplicity First | 用最少必要代码解决当前请求。 |
| Surgical Changes | 只修改任务需要的文件和代码行。 |
| Goal-Driven Execution | 把模糊请求转成可验证的成功标准。 |

## 在 Codex 中安装

把本仓库作为本地 Codex 插件源使用。

1. 将本仓库加入 Codex 插件源。
2. Codex 读取 `.codex-plugin/plugin.json`。
3. Codex 从 `skills/karpathy-guidelines/SKILL.md` 加载技能。

插件名：

```text
andrej-karpathy-skills
```

技能名：

```text
karpathy-guidelines
```

## 仓库结构

```text
.codex-plugin/plugin.json
AGENTS.md
EXAMPLES.md
README.md
README.zh.md
skills/karpathy-guidelines/SKILL.md
```

## 授权

MIT
