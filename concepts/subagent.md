# Subagent - 子代理

> 📖 **详细文档**: [Claude Code - Subagents](https://code.claude.com/docs/en/subagents)

## 什么是 Subagent？

**Subagent** - 在独立上下文中运行的 Agent，用于隔离任务和并行工作。

## 为什么要用 Subagent？

```mermaid
flowchart TD
    A[使用场景] --> B[处理大文件<br/>不污染主上下文]
    A --> C[并行任务<br/>独立执行]
    A --> D[隔离环境<br/>独立分析]

    B --> E[主会话精简<br/>只接收摘要]

    C --> F[同时工作<br/>提高效率]

    D --> G[独立思考<br/>避免干扰]

    style A fill:#e1f5ff
    style B fill:#fff3cd
    style C fill:#c8e6c9
    style D fill:#81c784
    style E fill:#4caf50
    style F fill:#2196f3
    style G fill:#ff9800
```

## Subagent vs 主会话

```mermaid
flowchart LR
    A[主会话] --> B["完整上下文<br/>所有历史"]

    C[Subagent] --> D["独立上下文<br/>干净状态"]

    A --> E[返回摘要<br/>不污染主会话]
    C --> E

    style A fill:#e1f5ff
    style B fill:#fff3cd
    style C fill:#c8e6c9
    style D fill:#81c784
    style E fill:#4caf50
```

## 何时使用 Subagent

```mermaid
flowchart TD
    A{场景判断} --> B[大文件分析<br/>→ Subagent]
    A --> C[并行任务<br/>→ Subagent]
    A --> D[隔离实验<br/>→ Subagent]
    A --> E[简单任务<br/>→ 主会话]

    style A fill:#e1f5ff
    style B fill:#4caf50
    style C fill:#2196f3
    style D fill:#ff9800
    style E fill:#c8e6c9
```

## 使用示例

```markdown
# 使用 Subagent 分析大项目
"用 subagent 分析 src/ 目录结构：
1. 独立分析每个模块
2. 总结架构
3. 报告发现
4. 主会话只接收摘要"
```

## 相关概念

- [Agent](./agent.md) - Agent 基础概念
- [Agent Team](./agent-team.md) - 多 Agent 协作
- [上下文管理](./context.md) - 为什么需要隔离

## 资源链接

- **Claude Code**: https://code.claude.com/docs/en/subagents
- **文档**: [如何使用 Subagents](https://code.claude.com/docs/en/parallel-work)
