# MCP - Model Context Protocol

> 📖 **详细文档**: [MCP 官方文档](https://modelcontextprotocol.io/)

## 什么是 MCP？

**MCP (Model Context Protocol)** - 连接 AI 应用到外部数据的开放标准协议。

## MCP 解决什么问题？

```mermaid
flowchart TD
    A[问题] --> B[AI 应用<br/>无法访问外部数据]
    A --> C[每个工具<br/>需要单独集成]
    A --> D[无统一标准<br/>开发成本高]

    E[MCP 解决] --> F[开放协议<br/>统一标准]
    E --> G[即插即用<br/>快速集成]
    E --> H[安全可控<br/>权限管理]

    style A fill:#e1f5ff
    style B fill:#f44336
    style C fill:#ff9800
    style D fill:#ff5722
    style E fill:#4caf50
    style F fill:#c8e6c9
    style G fill:#81c784
    style H fill:#66bb6a
```

## MCP 架构

```mermaid
flowchart LR
    A[AI 应用] --> B[MCP Client]
    B --> C[MCP Server]

    C --> D[GitHub<br/>数据库<br/>文件系统<br/>Slack<br/>浏览器]

    style A fill:#e1f5ff
    style B fill:#fff3cd
    style C fill:#c8e6c9
    style D fill:#4caf50
```

## 常用 MCP 服务器

| 服务器            | 功能         | 获取                                                    |
|----------------|------------|-------------------------------------------------------|
| **GitHub**     | PR 管理、代码操作 | `npm install @modelcontextprotocol/server-github`     |
| **Postgres**   | 数据库查询      | `npm install @modelcontextprotocol/server-postgres`   |
| **Filesystem** | 文件访问       | `npm install @modelcontextprotocol/server-filesystem` |
| **Slack**      | 消息发送       | 社区贡献                                                  |
| **Browser**    | 浏览器控制      | `@modelcontextprotocol/server-puppeteer`              |

## 快速开始

```bash
# 1. 安装服务器
npm install -g @modelcontextprotocol/server-github

# 2. 配置 ~/.claude/settings.json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"]
    }
  }
}

# 3. 验证
claude mcp list
```

## 相关概念

- [Skills](../skills/) - 可复用知识
- [CLAUDE.md](../skills/) - 项目配置

## 资源链接

- **MCP 官网**: https://modelcontextprotocol.io
- **服务器列表**: https://github.com/modelcontextprotocol/servers
- **规范文档**: https://spec.modelcontextprotocol.io/
