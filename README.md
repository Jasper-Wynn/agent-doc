# AI Agent 使用导航

> **定位**: 精简导航 + 实战 Demo，详细内容查阅官方文档
>
> **更新**: 2026年3月

## 🎯 快速开始

```mermaid
flowchart TD
    A[我想...] --> B[了解概念<br/>-concepts/]
    A --> C[找 Skills<br/>-skills/]
    A --> D[配置项目<br/>-config/]
    A --> E[看 Demo<br/>-demos/]
    A --> F[找文档<br/>-links/]

    style A fill:#e1f5ff
    style B fill:#fff3cd
    style C fill:#4caf50
    style D fill:#c8e6c9
    style E fill:#ff9800
    style F fill:#2196f3
```

## 📚 目录结构

```
agent-doc/
├── concepts/      基础概念介绍
├── skills/        Skills 导航和推荐
├── config/        配置指南
├── demos/         实战示例
└── links/         官方文档链接
```

---

## 📖 基础概念 (concepts/)

```mermaid
flowchart LR
    A[concepts] --> B[llm.md<br/>LLM]
    A --> C[agent.md<br/>Agent]
    A --> D[subagent.md<br/>Subagent]
    A --> E[agent-team.md<br/>Agent Team]
    A --> F[mcp.md<br/>MCP]
    A --> G[context.md<br/>Context]
    A --> H[token.md<br/>Token]

    style A fill:#e1f5ff
    style B fill:#fff3cd
    style C fill:#c8e6c9
    style D fill:#4caf50
    style E fill:#2196f3
    style F fill:#ff9800
    style G fill:#9c27b0
    style H fill:#66bb6a
```

## 🔧 Skills 导航 (skills/)

```mermaid
flowchart TD
    A[skills/] --> B[README.md<br/>介绍]
    A --> C[recommended.md<br/>推荐列表]
    A --> D[how-to-install.md<br/>安装教程]
    A --> E[awesome-skills.md<br/>社区精选]
    A --> F[create-your-own.md<br/>创建指南]

    style A fill:#e1f5ff
    style B fill:#fff3cd
    style C fill:#4caf50
    style D fill:#2196f3
    style E fill:#ff9800
    style F fill:#9c27b0
```

**推荐资源**:
- [skills.sh](https://skills.sh) - Skills 发现平台

## ⚙️ 配置指南 (config/)

```mermaid
flowchart TD
    A[config/] --> B[settings-json.md<br/>基础配置]
    A --> C[git-workflow.md<br/>Git 工作流]
    A --> D[tmux-setup.md<br/>tmux 分屏]
    A --> E[model-selection.md<br/>模型选择]
    A --> F[two-phase-workflow.md<br/>两阶段工作流]
    A --> G[python-playwright.md<br/>测试配置]

    style A fill:#e1f5ff
    style B fill:#fff3cd
    style C fill:#c8e6c9
    style D fill:#81c784
    style E fill:#4caf50
    style F fill:#2196f3
    style G fill:#ff9800
```

## 🎬 实战示例 (demos/)

```mermaid
flowchart TD
    A[demos/*.md] --> B[hello-world.md<br/>入门]
    A --> C[subagent.md<br/>隔离任务]
    A --> D[agent-team.md<br/>团队协作]
    A --> E[mcp.md<br/>工具集成]
    A --> F[multi-model.md<br/>多模型工作流]
    A --> G[subagent-setup.md<br/>Subagent 配置]
    A --> H[team-setup.md<br/>Agent Team 配置]
    A --> I[faq.md<br/>常见问题]

    style A fill:#e1f5ff
    style B fill:#4caf50
    style C fill:#2196f3
    style D fill:#ff9800
    style E fill:#9c27b0
    style F fill:#f44336
    style G fill:#66bb6a
    style H fill:#795548
    style I fill:#607d8b
```

## 🔗 官方链接 (links/)

- [官方文档](links/official.md)
- [模型平台](links/models.md)
- [工具链接](links/tools.md)

---

## ⚡ 2026 年 3 月快照

```mermaid
flowchart TD
    A[顶级工具] --> B[Claude Opus 4.6<br/>最强编码]
    A --> C[Qwen 3.5-Plus<br/>HF 榜首]
    A --> D[Llama 4<br/>原生多模态]

    E[本地部署] --> F["ollama + Qwen 3.5-27B"]

    F --> G[8GB: 7B<br/>16GB: 27B<br/>24GB: 122B]

    style A fill:#e1f5ff
    style B fill:#f44336
    style C fill:#4caf50
    style D fill:#ff9800
    style E fill:#2196f3
    style F fill:#c8e6c9
    style G fill:#81c784
```

---

## 🤝 贡献

发现好用的 Skill 或 Demo？欢迎 PR！

## 📄 许可证

MIT License

---

<div align="center">

**⭐ Star 收藏，方便下次找到**

Made with ❤️ by the AI Agent community

</div>
