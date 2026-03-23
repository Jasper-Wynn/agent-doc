# LLM - 大语言模型

> 📖 **详细文档**: [Claude 官方文档](https://docs.anthropic.com) | [OpenAI 文档](https://platform.openai.com/docs)

## 什么是 LLM？

**LLM (Large Language Model)** - 在海量文本数据上训练的神经网络，能理解和生成人类语言。

## 核心特点

```mermaid
flowchart TD
    A[LLM 特点] --> B[预训练<br/>海量数据学习]
    A --> C[生成能力<br/>创作连贯文本]
    A --> D[理解能力<br/>解析上下文意图]
    A --> E[推理能力<br/>逻辑思考分析]

    style A fill:#e1f5ff
    style B fill:#fff3cd
    style C fill:#c8e6c9
    style D fill:#81c784
    style E fill:#4caf50
```

## 2026 主流模型

```mermaid
flowchart TD
    A[按类型] --> B[闭源 API<br/>Claude Opus 4.6<br/>GPT-5.3]
    A --> C[开源权重<br/>Llama 4<br/>Qwen 3.5]
    A --> D[代码专用<br/>Qwen3-Coder<br/>Claude Opus]

    style A fill:#e1f5ff
    style B fill:#f44336
    style C fill:#4caf50
    style D fill:#ff9800
```

## 关键参数

| 参数      | 说明        | 示例                  |
|---------|-----------|---------------------|
| **参数量** | 模型规模，影响能力 | 7B, 27B, 122B       |
| **上下文** | 一次处理信息量   | 128K, 1M, 2M tokens |
| **量化**  | 精度压缩      | FP16, INT8, Q4      |

## 相关概念

- [Agent](./agent.md) - LLM 的自主应用
- [Token](./token.md) - LLM 处理单位
- [上下文](./context.md) - 信息处理上限

## 资源链接

- **Hugging Face**: https://huggingface.co/models
- **魔塔社区**: https://modelscope.cn/models
- **Ollama 库**: https://ollama.com/library
