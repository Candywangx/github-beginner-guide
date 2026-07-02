## 11. 前端、后端、数据库、API 是什么

### 11.1 前端

前端就是用户看得见、点得到的界面。

常见技术：

- HTML
- CSS
- JavaScript
- TypeScript
- React
- Vue
- Next.js
- Vite

常见目录：

- `components`
- `pages`
- `app`
- `styles`
- `public`

### 11.2 后端

后端是用户看不见，但负责处理数据和规则的服务。

它常做：

- 登录验证
- 数据保存
- 计算逻辑
- 调 AI 模型
- 提供 API
- 连接数据库

常见技术：

- Python FastAPI / Flask / Django
- Node.js Express / NestJS
- Java Spring
- Go

常见目录：

- `api`
- `server`
- `routes`
- `controllers`
- `services`
- `models`

### 11.3 数据库

数据库是专门存数据的地方。

常见数据库：

- PostgreSQL
- MySQL
- SQLite
- MongoDB
- Redis
- Elasticsearch

常见目录/文件：

- `schema`
- `migrations`
- `sql`
- `prisma`

### 11.4 API

API 是程序之间说话的接口。

人话：

> 前端问后端要数据，后端按约定返回结果，这个约定就是 API。

常见形式：

```http
GET /api/users
POST /api/login
```

返回内容常见是 JSON：

```json
{
  "name": "Alice",
  "role": "admin"
}
```

### 11.5 SDK、库、框架、插件是什么

这几个词都属于“别人已经写好的能力”。区别在于：你是直接调用一个入口、安装一个工具包、按一套项目规则写代码，还是给已有工具加功能。

| 名字 | 它是什么 | 你在仓库里怎么理解 |
|---|---|---|
| API | 调用入口和调用规则 | 一个程序向另一个程序要数据或提交数据 |
| SDK | 开发工具包 | 把 API 包装成更好用的代码工具，项目安装后直接调用 |
| Library / 库 | 工具包 | 提供一组现成功能，项目需要时调用它 |
| Framework / 框架 | 项目规则和骨架 | 规定项目目录、启动方式、写法和运行流程 |
| Module / 模块 | 代码单元 | 一块可以被其他代码引用的功能 |
| Plugin / 插件 | 扩展能力 | 给已有工具、平台、框架增加功能 |
| Extension / 扩展 | 扩展能力 | 在编辑器、浏览器、平台里增加功能 |
| Template / 模板 | 起始项目 | 新项目复制它作为起点 |
| Boilerplate | 模板骨架 | 已经搭好的基础代码，减少从零搭建 |
| Client | 客户端 | 发起请求的一方，比如网页、App、AI 客户端 |
| Server | 服务端 | 接收请求并返回结果的一方 |
| Schema | 结构规则 | 规定数据有哪些字段、字段是什么类型 |

SDK 和 API 的关系：

> API 是“对方开放的入口”。SDK 是“为了更方便使用这个入口而提供的工具包”。

举例：

```txt
你要调用一个 AI 平台
方式 1：自己按 API 文档拼请求
方式 2：安装这个平台提供的 SDK，用 SDK 里的函数调用
```

所以看到 `openai`、`stripe`、`aws-sdk`、`github-sdk` 这类名字时，先按“某个平台的开发工具包”理解。它们会出现在依赖清单里，例如 `package.json`、`requirements.txt`、`pyproject.toml`。

一个名字可以同时有多个身份。判断时看它出现的位置：

| 出现位置 | 判断方式 |
|---|---|
| 出现在 `dependencies`、`requirements.txt` 里 | 它是要安装的依赖包 |
| 出现在 README 的项目介绍里 | 它是项目使用的技术、框架或平台能力 |
| 出现在文件夹名里，比如 `sdk`、`client`、`plugins` | 它是仓库里的功能区域 |
| 出现在代码里，比如 `import openai` | 它是代码正在引用的模块或依赖包 |

比如 FastAPI：

| 看到的位置 | 解释 |
|---|---|
| `requirements.txt` 里的 `fastapi` | 一个 Python 依赖包，需要安装 |
| README 里写“使用 FastAPI” | 一个 Python 后端框架 |
| 代码里写 `from fastapi import FastAPI` | 正在引用 FastAPI 这个模块 |

这不是矛盾。编程资料里的很多名字同时可以表示“包名、工具名、框架名、模块名、目录名”。你先看位置，再定身份。

### 11.6 JSON 是什么

JSON 是一种数据格式。

你先记住：

- `{}` 表示对象。
- `[]` 表示列表。
- `"key": "value"` 表示一项数据。

---
