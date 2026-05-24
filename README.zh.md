# Andrej Karpathy 指导原则（Codex 版）

这是一个最小化行为规范仓库，来自 Andrej Karpathy 关于 LLM 编码误区的观察。  
当前仓库已转换为 **Codex 插件包**。

- 主入口：`.codex-plugin/plugin.json`
- 技能入口：`skills/karpathy-guidelines/SKILL.md`
- 兼容文件：`CLAUDE.md`、`CURSOR.md`

## 安装（Codex）

1. 将仓库加入本地 Codex 插件源。
2. Codex 会从 `.codex-plugin/plugin.json` 读取插件元数据。
3. 插件名：`andrej-karpathy-skills`，技能条目：`karpathy-guidelines`。

## 示例与规则

- 规则文档：[`skills/karpathy-guidelines/SKILL.md`](skills/karpathy-guidelines/SKILL.md)
- 实例说明：[`EXAMPLES.md`](EXAMPLES.md)
- Cursor 规则：`.cursor/rules/karpathy-guidelines.mdc`

## 兼容说明（非必需）

原有 `README`、`CLAUDE.md`、`CURSOR.md` 中的部分旧流程会保留为兼容内容。  
如果你只在 Codex 使用，本文件已足够说明当前插件行为入口。

## 授权

MIT
