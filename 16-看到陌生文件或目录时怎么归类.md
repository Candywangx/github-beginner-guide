## 13. AI、RAG、MCP、Agent、Dify 是什么

### 13.1 AI 应用项目

AI 项目不是一段聊天代码。

它包括这些部分：

- 调用大模型。
- 管理提示词。
- 读取文件。
- 做 OCR。
- 做知识库。
- 调用工具。
- 编排多个步骤。
- 提供网页或 API。

### 13.2 RAG

RAG 是 Retrieval-Augmented Generation。

人话：

> 先从资料里找相关内容，再让 AI 基于找到的内容回答。

它不是让模型“背下所有文件”。

常见目录或词：

- `knowledge`
- `retrieval`
- `embedding`
- `vector`
- `documents`
- `rag`

### 13.3 Agent

Agent 是智能体。

人话：

> 不只是聊天，而是能按目标拆步骤、调用工具、执行任务的 AI。

常见词：

- `agent`
- `workflow`
- `planner`
- `tools`
- `memory`
- `langgraph`
- `crew`

### 13.4 MCP

MCP 是 Model Context Protocol。

人话：

> 一套让 AI 调用外部工具和数据的协议。

你可以把它想成：

> AI 和工具之间的通用插座。

为什么需要 MCP？

普通聊天 AI 只能根据对话回答。它不能天然知道你电脑里有哪些文件，也不能天然操作数据库、浏览器、GitHub、业务系统。

如果想让 AI 调用这些外部能力，就需要一套统一约定：

| 角色 | 人话解释 |
|---|---|
| AI 客户端 | 想调用工具的 AI 应用，比如 Codex、Claude Desktop |
| MCP Server | 把某个工具包装成 AI 能调用的服务 |
| Tool | MCP Server 暴露出来的具体能力，比如搜索文件、查数据库 |
| Resource | MCP Server 提供给 AI 阅读的资料 |

例子：

```text
AI 想查数据库
-> 连接数据库 MCP Server
-> 调用 query 工具
-> 拿到查询结果
-> 再用人话回答你
```

MCP 项目常见内容：

- `mcp server`
- `tools`
- `resources`
- `stdio`
- `http`
- `sse`

这些词这样理解：

| 词 | 人话解释 |
|---|---|
| `mcp server` | 给 AI 调用的工具服务 |
| `tools` | AI 可以执行的动作 |
| `resources` | AI 可以读取的资料 |
| `stdio` | 通过标准输入/输出连接，常用于本地工具 |
| `http` | 通过网页网络协议连接 |
| `sse` | 服务器持续推送消息的一种连接方式 |

看到仓库里有 `mcp`、`tools`、`server` 这些词时，先归入“AI 工具调用区”。

### 13.5 Dify

Dify 是可视化 AI 应用平台。

人话：

> 用网页搭知识库问答、聊天应用、工作流。

你先重点理解：

- Knowledge：知识库。
- Chatflow：聊天流程。
- Workflow：工作流。
- RAG：检索资料后回答。

---
