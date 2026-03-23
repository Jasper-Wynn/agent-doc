# MCP Integration Demo - 工具集成

> 📖 **相关文档**: [MCP 官方文档](https://modelcontextprotocol.io)
>
> 📅 **更新日期**: 2026年3月

## 场景

使用 MCP 协议集成外部工具，让 Agent 访问 GitHub、数据库、文件系统等资源。

## 工作流程

```mermaid
flowchart LR
    A[Claude Code] --> B[MCP Client]
    B --> C[MCP Server]
    C --> D[GitHub]
    C --> E[Database]
    C --> F[Filesystem]

    style A fill:#e1f5ff
    style B fill:#fff3cd
    style C fill:#c8e6c9
    style D fill:#f44336
    style E fill:#ff9800
    style F fill:#2196f3
```

## 步骤

### 1. 安装 MCP Server

```bash
# 安装 GitHub MCP Server
npm install -g @modelcontextprotocol/server-github
```

### 2. 配置 Claude Code

编辑 `~/.claude/settings.json`:

```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"]
    }
  }
}
```

### 3. 验证安装

```bash
claude mcp list
```

### 4. 使用 MCP 工具

```bash
claude

# 在 Claude 中使用 GitHub 工具:
"查看 anthropics/claude-code 仓库的最新 PR"
```

## 常用 MCP 服务器

| 服务器            | 功能         | 安装                                                    |
|----------------|------------|-------------------------------------------------------|
| **GitHub**     | PR 管理、代码操作 | `npm install @modelcontextprotocol/server-github`     |
| **Postgres**   | 数据库查询      | `npm install @modelcontextprotocol/server-postgres`   |
| **Filesystem** | 文件访问       | `npm install @modelcontextprotocol/server-filesystem` |
| **Puppeteer**  | 浏览器控制      | `npm install @modelcontextprotocol/server-puppeteer`  |

## 示例配置

```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"]
    },
    "postgres": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-postgres", "postgresql://user:pass@localhost/db"]
    },
    "filesystem": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "/allowed/path"]
    }
  }
}
```

## 学习要点

- MCP 是开放标准，统一工具集成
- 配置简单，即插即用
- 安全可控，权限管理

## 下一步

探索更多 [MCP 服务器](https://github.com/modelcontextprotocol/servers)
