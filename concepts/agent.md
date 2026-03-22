# Agent - AI 代理

> 📖 **详细文档**: [Claude Code - How it works](https://code.claude.com/docs/en/how-claude-code-works)

## 什么是 Agent？

**Agent** - 能自主执行任务以达到目标的 AI 系统，核心是 **循环执行**：观察 -思考 -行动 -验证

## Chatbot vs Agent

```mermaid
flowchart LR
    A[Chatbot] --> B["用户 -模型 -回答 -结束"]

    C[Agent] --> D["用户 -目标 -循环执行 -结果"]

    style A fill:#e1f5ff
    style B fill:#ffcc80
    style C fill:#c8e6c9
    style D fill:#4caf50
```

## Agent 循环

```mermaid
flowchart TD
    A[Agent 循环] --> B[观察 Observe<br/>获取状态]
    B --> C[思考 Think<br/>分析推理]
    C --> D[行动 Act<br/>执行操作]
    D --> E[验证 Verify<br/>确认结果]
    E --> F{完成?}
    F -->|否| B
    F -->|是| G[✓ 完成]

    style A fill:#e1f5ff
    style B fill:#fff3cd
    style C fill:#c8e6c9
    style D fill:#81c784
    style E fill:#4caf50
    style F fill:#ffc107
    style G fill:#66bb6a
```

## 相关概念

- [Subagent](./subagent.md) - 独立上下文的 Agent
- [Agent Team](./agent-team.md) - 多 Agent 协作
- [LLM](./llm.md) - Agent 的基础模型

## 工具对比

| 工具 | 类型 | 特点 |
|------|------|------|
| **Claude Code** | CLI | 最强 Agent 能力 |
| **Cursor** | IDE | 多 Agent 并行 |
| **OpenDevin** | 开源 | 自主软件工程师 |

## 资源链接

- **Claude Code**: https://code.claude.com
- **Agentic Patterns**: https://www.anthropic.com/news/agentic-patterns
