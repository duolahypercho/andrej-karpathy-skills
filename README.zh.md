# Codex Andrej Karpathy Skill

这是一个 Codex 原生 skill，用来打包 Andrej Karpathy 启发的 coding-agent 指南。

- `AGENTS.md` 是仓库级 Codex 操作上下文。
- `.codex-plugin/plugin.json` 是插件清单。
- `skills/andrej-karpathy-skill/SKILL.md` 是可复用 skill。
- `instruction.md` 是可以复制到 Codex Custom Instructions 的版本。
- `EXAMPLES.md` 是 Codex 风格示例。

[English](./README.md) | 简体中文

## 为什么需要它

Coding agent 常见失败方式很固定：

- 做太多隐藏假设。
- 把简单请求做复杂。
- 修改无关代码。
- 没有明确成功标准就说完成。

这个仓库把 Karpathy 风格的四条原则整理成 Codex 可用的 skill、`AGENTS.md` 和 Custom Instructions。

## 四条原则

| 原则 | Codex 行为 |
|------|------------|
| Think before coding | 先暴露假设、困惑、替代方案和权衡。 |
| Keep it simple | 只解决当前请求，不添加推测性功能或抽象。 |
| Make surgical changes | 只修改任务需要的代码，保留周围代码形状。 |
| Define and verify the goal | 把请求变成可检查的结果，再说完成。 |

## 在 Codex 中安装

把本仓库作为本地 Codex 插件源使用。

1. 将本仓库加入 Codex 插件源。
2. Codex 读取 `.codex-plugin/plugin.json`。
3. Codex 加载 `skills/andrej-karpathy-skill/SKILL.md`。

插件名：

```text
andrej-karpathy-skills
```

Skill 名：

```text
andrej-karpathy-skill
```

## 不安装也可以使用

如果不想安装插件，也不想依赖 `AGENTS.md`：

1. 打开 `instruction.md`。
2. 复制其中的 Custom Instructions 区块。
3. 粘贴到 Codex Settings -> Custom Instructions。

这个版本是自包含的，Codex 不需要额外读取仓库文件就能使用同样的行为。

## 仓库结构

```text
.codex-plugin/plugin.json
AGENTS.md
EXAMPLES.md
instruction.md
LICENSE
README.md
README.zh.md
skills/andrej-karpathy-skill/SKILL.md
```

## 授权

MIT
