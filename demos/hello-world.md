# Hello World Demo

> 📖 **资料来源**: Claude Code 官方文档
>
> 📅 **更新日期**: 2026年3月

## 简介

这是最简单的 Agent 使用示例，帮助你快速上手。

## 工作流程

```mermaid
flowchart TD
    A[开始] --> B[初始化项目]
    B --> C[mkdir hello-agent<br/>cd hello-agent<br/>npm init -y]

    C --> D[启动 Claude Code]
    D --> E["claude"]

    E --> F[输入任务]
    F --> G["创建 Node.js Hello World<br/>输出 'Hello, Agent!'<br/>添加 start 脚本<br/>编写 README"]

    G --> H[Agent 执行]
    H --> I[创建文件<br/>编写代码<br/>配置脚本]

    I --> J[验证结果]
    J --> K["npm start<br/>输出: Hello, Agent!"]

    style A fill:#e1f5ff
    style B fill:#fff3cd
    style C fill:#ffeb3b
    style D fill:#c8e6c9
    style E fill:#81c784
    style F fill:#fff3cd
    style G fill:#4caf50
    style H fill:#2196f3
    style I fill:#64b5f6"
    style J fill:#ff9800"
    style K fill:#ff5722"
```

## 任务描述

创建一个简单的 "Hello World" 程序，展示 Agent 的基本能力。

## 步骤

### 1. 初始化项目

```bash
mkdir hello-agent
cd hello-agent
npm init -y
```

### 2. 使用 Claude Code

```bash
claude

# 在 Claude 中输入:
"创建一个简单的 Node.js Hello World 程序:
- 输出 'Hello, Agent!'
- 添加 package.json 的 start 脚本
- 编写 README.md"
```

### 3. 验证结果

```bash
npm start
# 应该输出: Hello, Agent!
```

## 预期结果

```mermaid
flowchart TD
    A[hello-agent/] --> B[package.json]
    A --> C[index.js]
    A --> D[README.md]

    style A fill:#e1f5ff
    style B fill:#fff3cd
    style C fill:#c8e6c9
    style D fill:#81c784
```

## 学习要点

```mermaid
flowchart TD
    A[学习要点] --> B[Agent 可以创建<br/>完整的项目结构]
    A --> C[Agent 会自动配置<br/>必要的文件]
    A --> D[Agent 遵循项目约定<br/>和最佳实践]

    style A fill:#e1f5ff
    style B fill:#4caf50
    style C fill:#2196f3
    style D fill:#ff9800
```

## 2026 提示

```mermaid
flowchart LR
    A[2026 模型选择] --> B[本地: Qwen 3.5-7B<br/>快速体验]
    A --> C[API: Claude Opus 4.6<br/>最佳效果]

    style A fill:#e1f5ff
    style B fill:#4caf50
    style C fill:#f44336
```

## 下一步

尝试 [调试 Demo](subagent/)
