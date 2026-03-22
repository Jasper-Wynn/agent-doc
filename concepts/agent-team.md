# Agent Team - 代理团队

> 📖 **详细文档**: [Claude Code - Agent Teams](https://code.claude.com/docs/en/agent-teams)

## 什么是 Agent Team？

**Agent Team** - 多个独立 Agent 会话协作完成复杂任务，队友间可以直接通信。

## Subagent vs Agent Team

```mermaid
flowchart TD
    subgraph Subagent_工作流
        A1[主会话] --> A2[Subagent 1<br/>独立上下文]
        A1 --> A3[Subagent 2<br/>独立上下文]
        A2 --> A4[返回摘要<br/>到主会话]
        A3 --> A5[返回摘要<br/>到主会话]
    end

    subgraph Agent_Team_工作流
        B1[队友 1] --> B2[共享任务列表]
        B2 --> B3[队友 2]
        B2 --> B4[队友 3]
        B3 -.->|直接通信| B4
        B4 -.->|直接通信| B3
        B3 -.->|直接通信| B1
        B4 -.->|直接通信| B1
    end

    style A1 fill:#f44336
    style A2 fill:#c8e6c9
    style A3 fill:#c8e6c9
    style B1 fill:#4caf50
    B2 fill:#ff9800
    B3 fill:#2196f3
    B4 fill:#9c27b0
```

## Agent Team 特点

```mermaid
flowchart TD
    A[Agent Team] --> B[共享任务列表<br/>团队协调]
    A --> C[直接通信<br/>队友讨论]
    A --> D[自我协调<br/>完成复杂任务]

    B --> E[明确分工<br/>避免重复]
    C --> F[实时交流<br/>解决问题]
    D --> G[动态调整<br/>适应变化]

    style A fill:#e1f5ff
    style B fill:#fff3cd
    style C fill:#c8e6c9
    style D fill:#81c784
    style E fill:#4caf50
    style F fill:#2196f3
    style G fill:#ff9800
```

## 何时使用 Agent Team

```mermaid
flowchart TD
    A{任务类型?} --> B[复杂协作<br/>-Agent Team]
    A --> C[简单任务<br/>-Subagent]
    A --> D[单一功能<br/>-主会话]

    B --> E[需要讨论<br/>分工协作]
    C --> F[快速专注<br/>独立执行]
    D --> G[直接完成<br/>无需协调]

    style A fill:#e1f5ff
    style B fill:#4caf50
    style C fill:#2196f3
    style D fill:#c8e6c9
    style E fill:#81c784
    style F fill:#66bb6a"
    style G fill:#ffcc80"
```

## 典型场景

```mermaid
flowchart TD
    A[Agent Team 场景] --> B[大型重构<br/>多人分工]
    A --> C[代码审查<br/>并行审查]
    A --> D[问题调研<br/>多角度分析]
    A --> E[功能开发<br/>模块并行]

    style A fill:#e1f5ff
    style B fill:#f44336
    style C fill:#ff9800
    style D fill:#2196f3
    style E fill:#4caf50
```

## 使用示例

```markdown
# 启动 Agent Team 进行重构
"启动 Agent Team 重构项目：
- 队友 1: 分析现有架构
- 队友 2: 设计新架构
- 队友 3: 逐步迁移
共享任务列表，实时讨论协调"
```

## 相关概念

- [Agent](./agent.md) - 单个 Agent 基础
- [Subagent](./subagent.md) - 隔离任务执行
- [协作模式](./agent.md) - 协作工作方式

## 资源链接

- **Claude Code**: https://code.claude.com/docs/en/agent-teams
- **最佳实践**: [并行工作](https://code.claude.com/docs/en/parallel-work)
