# Token - 基本单位

## 什么是 Token？

**Token** - LLM 处理文本的基本单位，类似单词的片段或字符组合。

## Token 换算

```mermaid
flowchart TD
    A[Token 换算] --> B[英文文本]
    A --> C[中文文本]
    A --> D[代码]

    B --> E["1 token ≈ 4 个字符<br/>1 token ≈ 0.75 单词<br/>1000 tokens ≈ 750 单词"]

    C --> F["1 token ≈ 1-2 个汉字<br/>1000 tokens ≈ 500-1000 汉字"]

    D --> G["1 token ≈ 3-5 个字符<br/>100 行代码 ≈ 1000-2000 tokens"]

    style A fill:#e1f5ff
    style B fill:#fff3cd
    style C fill:#c8e6c9
    style D fill:#81c784
    style E fill:#ffeb3b
    style F fill:#a5d6a7
    style G fill:#66bb6a
```

## 为什么理解 Token 很重要？

```mermaid
flowchart TD
    A[理解 Token] --> B[估算成本<br/>API 按 token 计费]
    A --> C[管理上下文<br/>上下文有 token 限制]
    A --> D[优化提示词<br/>简洁节省 token]

    style A fill:#e1f5ff
    style B fill:#4caf50
    style C fill:#2196f3
    style D fill:#ff9800
```

## 节省 Token 技巧

```mermaid
flowchart LR
    A[❌ 浪费] --> B["看看这个文件 /path/to/file.js<br/>告诉我有什么问题"]

    C[✅ 高效] --> D["@/path/to/file.js<br/>找出潜在问题"]

    style A fill:#e1f5ff
    style B fill:#f44336
    style C fill:#4caf50
    style D fill:#c8e6c9
```

## 相关概念

- [上下文窗口](./context.md) - Token 限制
- [LLM](./llm.md) - 使用 Token 的模型

## 估算工具

- **Tokenizr**: https://tokenzer.net
- **Claude Token Counter**: 内置显示

## 资料链接

- **OpenAI Tokenizer**: https://platform.openai.com/tokenizer
- **Anthropic Pricing**: https://www.anthropic.com/pricing
