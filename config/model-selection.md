# 模型选择策略

> 为不同任务选择合适的模型，平衡质量和成本

## 2026 主流模型

```mermaid
flowchart TD
    A[模型梯队] --> B[闭源 API<br/>Claude Opus 4.6, GPT-5.3]
    A --> C[开源权重<br/>Llama 4, Qwen 3.5]
    A --> D[代码专用<br/>Qwen-Coder, Claude Opus]

    B --> E[最强能力<br/>按 token 计费]
    C --> F[可本地部署<br/>自由度高]
    D --> G[优化代码<br/>开发效率]

    style A fill:#e1f5ff
    style B fill:#f44336
    style C fill:#4caf50
    style D fill:#2196f3
```

## Claude 模型对比

| 模型 | 位置 | 能力 | 成本 | 适用场景 |
|------|------|------|------|----------|
| **Opus 4.6** | 最强 | 复杂推理、深度分析 | 最高 | 架构设计、复杂问题 |
| **Sonnet 4.6** | 平衡 | 日常开发 | 中等 | 代码实现、文档编写 |
| **Haiku 4.5** | 快速 | 简单任务 | 最低 | 测试运行、格式检查 |

## 选择策略

### 按任务类型

```mermaid
flowchart TD
    A{任务类型} --> B["复杂推理<br/>-Opus"]
    A --> C["常规开发<br/>-Sonnet"]
    A --> D["简单重复<br/>-Haiku"]

    B --> E[架构设计<br/>安全审查<br/>算法优化]
    C --> F[代码实现<br/>文档编写<br/>Bug 修复]
    D --> G[运行测试<br/>格式检查<br/>日志分析]

    style A fill:#e1f5ff
    style B fill:#f44336
    style C fill:#2196f3
    style D fill:#4caf50
```

### 按角色分配

| 角色 | 模型 | 原因 |
|------|------|------|
| **架构师** | Opus | 需要全局视野和复杂决策 |
| **前端/后端** | Sonnet | 实现任务，平衡质量和成本 |
| **测试/运维** | Haiku | 重复性高，速度优先 |

## 配置方式

### 全局默认模型

```jsonc
// settings.json
{
  "subagentModel": "claude-sonnet-4-6"
}
```

### Agent 级别指定

```markdown
---
name: architect
model: claude-opus-4-6
---
```

```markdown
---
name: tester
model: claude-haiku-4-5
---
```

## 成本优化策略

### 主会话 + Subagent 组合

```mermaid
flowchart TD
    A[主会话 Opus] --> B[复杂分析]
    A --> C[关键决策]

    D[Subagent Sonnet] --> E[代码实现]
    D --> F[文档编写]

    G[Subagent Haiku] --> H[测试运行]
    G --> I[格式检查]

    style A fill:#f44336
    style D fill:#2196f3
    style G fill:#4caf50
```

**成本对比**:
| 配置 | 相对成本 |
|------|----------|
| 全程 Opus | 100% |
| 主 Opus + Subagent Sonnet | ~40% |
| 主 Opus + Subagent Haiku | ~15% |

### Agent Team 成本控制

```mermaid
flowchart TD
    A[Agent Team] --> B[Lead: Opus<br/>1 个]
    A --> C[Implementer: Sonnet<br/>2-3 个]
    A --> D[Tester: Haiku<br/>1-2 个]

    B --> E[20% 工作量]
    C --> F[60% 工作量]
    D --> G[20% 工作量]

    style A fill:#e1f5ff
    style B fill:#f44336
    style C fill:#2196f3
    style D fill:#4caf50
```

**注意**: Agent Team 消耗约 15 倍 token，需合理使用

## 实际配置示例

### 配置 1: 质量优先

```jsonc
{
  "subagentModel": "claude-opus-4-6"
}
```

适用：关键项目、复杂系统

### 配置 2: 成本平衡（推荐）

```jsonc
{
  "subagentModel": "claude-sonnet-4-6"
}
```

Agent 覆盖：
```markdown
---
# agents/architect.md
model: claude-opus-4-6
---
```

适用：日常开发

### 配置 3: 成本优先

```jsonc
{
  "subagentModel": "claude-haiku-4-5"
}
```

适用：简单任务、批量处理

### 配置 4: 两阶段工作流

```jsonc
{
  "subagentModel": "claude-sonnet-4-6"
}
```

```markdown
---
# agents/architect.md - 设计阶段
model: claude-opus-4-6
---
```

```markdown
---
# agents/backend.md - 实现阶段
model: claude-sonnet-4-6
---
```

```markdown
---
# agents/tester.md - 测试阶段
model: claude-haiku-4-5
---
```

## 选择决策树

```mermaid
flowchart TD
    A{选择模型} --> B{任务复杂度?}
    B -->|高| C[Opus]
    B -->|中| D{是否需要<br/>代码实现?}
    B -->|低| E[Haiku]

    D -->|是| F[Sonnet]
    D -->|否| E

    C --> G[架构/安全/算法]
    F --> H[开发/文档/测试]
    E --> I[运行/检查/分析]

    style A fill:#e1f5ff
    style C fill:#f44336
    style F fill:#2196f3
    style E fill:#4caf50
```

## 常见场景

| 场景 | 主会话 | Subagent | Agent Team |
|------|--------|----------|------------|
| **新功能开发** | Opus | Sonnet | Lead: Opus, 其他: Sonnet |
| **Bug 修复** | Sonnet | Haiku | 不推荐 |
| **代码审查** | Opus | - | 不推荐 |
| **文档编写** | Sonnet | Haiku | 不推荐 |
| **测试运行** | - | Haiku | 不推荐 |
| **架构设计** | Opus | - | 不推荐 |
| **大型重构** | Opus | Sonnet | Lead: Opus, 其他: Sonnet |

## 开源模型替代

### Qwen 3.5 (MoE)

```mermaid
flowchart TD
    A[Qwen 3.5-Plus] --> B[397B 总参数]
    A --> C[17B 激活参数]
    A --> D[HF #1 排名]

    B --> E[与 Opus 相当]
    C --> F[成本更低]
    D --> G[开源可本地]

    style A fill:#e1f5ff
    style B fill:#f44336
    style C fill:#4caf50
    style D fill:#2196f3
```

### 本地部署方案

| 内存 | 推荐 |
|------|------|
| 8GB | Qwen 3.5-7B |
| 16GB | Qwen 3.5-27B |
| 24GB+ | Qwen 3.5-122B |

## 相关指南

- [settings.json 配置](./settings-json.md)
- [两阶段工作流](./two-phase-workflow.md)
- [Subagent 配置](../demos/06-subagent-config/)
