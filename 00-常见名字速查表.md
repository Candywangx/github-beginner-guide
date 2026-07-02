# 零基础看懂任何 GitHub 仓库学习资料

> 目标：你不需要先成为程序员。你先要做到：打开一个仓库时，判断它的用途和类型、看懂常见文件夹/文件的作用、识别 README 里的命令属于哪类操作、遇到报错时判断该查哪一层、让 Codex 帮忙时说清楚目标和范围。

这份资料基于《AI 新手打印学习资料：看懂 linancn GitHub 仓库生态》重新整理，但会比原资料更基础、更通用。你以后看到任何 GitHub 仓库，都可以按这份资料来读。

---

## 使用前先看：常见名字速查表

这张表放在最前面，作用是“看到生词马上查”。你不用一次背完，读到哪里卡住，就回到这里查对应名字。

| 名字 | 它是什么 | 最短解释 |
|---|---|---|
| GitHub | 网站/平台 | 放项目、看代码、协作修改的地方 |
| 仓库 / repo | 项目文件夹 | 一个完整项目在 GitHub 上的保存位置 |
| README.md | 文档文件 | 项目说明书 |
| `.md` | 文件后缀 | Markdown 文档，给人阅读 |
| 源代码 | 文件类别 | 真正实现功能的代码 |
| 配置文件 | 文件类别 | 给工具读取的规则文件 |
| 依赖 | 工具包 | 项目借用的现成能力 |
| 依赖清单 | 文件类别 | 记录要安装哪些工具包 |
| 启动命令 | 命令类别 | 把项目运行起来的命令 |
| `api` | 常见目录名 | 放接口相关代码 |
| API | 程序接口 | 一个程序给另一个程序调用的入口 |
| `app` | 常见目录名 | 放应用代码或页面入口 |
| Artifact | 产物文件 | 自动化流程或构建过程生成的结果文件 |
| `assets` | 常见目录名 | 放资源文件，比如图片、字体、样式 |
| Auth | 权限验证 | 判断用户、程序、请求有没有权限 |
| Boilerplate | 模板骨架 | 已经搭好的项目基础代码 |
| build | 命令名字 | 构建正式版本 |
| Bundler | 打包工具 | 把多个代码文件整理成浏览器或服务器可用的文件 |
| Cache | 缓存 | 为了加速重复操作而保存的临时数据 |
| Changelog | 更新记录 | 记录每个版本改了什么 |
| CI/CD | 自动化流程 | 自动测试、构建、发布项目 |
| CLI | 命令行界面 | 用命令操作软件的方式 |
| Client | 客户端 | 发起请求的一方，比如网页、App、AI 客户端 |
| Compiler | 编译器 | 把一种代码转换成另一种可运行或可发布的形式 |
| `components` | 常见目录名 | 放前端页面组件 |
| `.csv` | 文件后缀 | 表格数据文件，用逗号分隔每一列 |
| dependencies | 配置字段 | 项目运行时需要的依赖包 |
| dev | 命令名字 | development 的缩写，表示开发模式 |
| devDependencies | 配置字段 | 开发、测试、构建时需要的依赖包 |
| `dist` / build output | 构建产物目录 | 放构建后生成的文件 |
| Docker | 工具 | 把项目运行环境打包并启动 |
| Dockerfile | 部署文件 | 说明如何制作 Docker 镜像 |
| `docs` | 常见目录名 | 放文档 |
| Endpoint | 接口地址 | API 里的一个具体访问地址 |
| `.env` | 文件后缀 | 环境变量文件，放端口、密钥、数据库地址 |
| Extension / 扩展 | 扩展能力 | 指编辑器、浏览器、平台里的插件 |
| FastAPI | Python 依赖包 | 用来写 API 服务的工具包 |
| Formatter | 代码格式化工具 | 自动整理代码格式 |
| Framework / 框架 | 项目骨架 | 规定项目怎么组织和运行的一套工具 |
| `.github/workflows` | 常见目录 | 放 GitHub 自动化流程 |
| `.gitignore` | Git 配置文件 | 告诉 Git 哪些文件/文件夹不要提交；被忽略项在 VS Code 里会变灰 |
| `.gitkeep` | 占位文件 | 让 Git 保存一个空文件夹 |
| GUI | 图形界面 | 用按钮、菜单、窗口操作软件的方式 |
| `.hbs` | 文件后缀 | Handlebars 模板文件，用占位符生成 HTML、邮件、文档或代码 |
| `.ipynb` | 文件后缀 | Jupyter 笔记本文件 |
| JavaScript / JS | 编程语言 | 网页和 Node.js 常用语言 |
| `.json` | 文件后缀 | JSON 格式，常用于配置和数据 |
| JSON | 数据/配置格式 | 用 `{}`、`[]`、`"key": "value"` 写结构 |
| Jupyter Notebook | 笔记本文件 | 边写说明、边运行代码、边看结果 |
| key/value | 配置写法 | `名字: 值` 或 `名字 = 值` |
| Library / 库 | 工具包 | 提供现成函数或能力，项目按需调用 |
| License | 授权说明 | 说明别人能怎样使用这个项目 |
| Linter | 代码检查工具 | 检查代码写法问题 |
| MCP | AI 工具协议 | 让 AI 调用外部工具和数据的通用协议 |
| `migrations` | 常见目录名 | 放数据库结构变更记录 |
| `.mjs` | 文件后缀 | JavaScript 模块文件 |
| Module / 模块 | 代码单元 | 可以被别的代码引用的一块功能 |
| Next.js / next | Node.js 依赖包/框架 | 用 React 做网站和应用的框架 |
| Nginx | 服务器软件 | 提供网页、转发请求、配置 HTTPS |
| Node.js | 运行环境 | 让 JavaScript 在电脑/服务器运行 |
| `node_modules` | 文件夹 | npm 下载回来的依赖包 |
| npm | 工具 | Node.js 项目的依赖安装器和命令运行器 |
| `package.json` | 配置文件 | Node.js 项目的菜单、依赖、项目信息 |
| `package-lock.json` | 锁定文件 | 固定 npm 依赖版本 |
| Package manager / 包管理器 | 工具类别 | 安装、更新、锁定依赖包的工具 |
| `package` / `packages` | 常见目录名 | 放一个或多个子项目、子包、可发布包 |
| Permission | 权限 | 允许做什么、不允许做什么 |
| Plugin / 插件 | 扩展能力 | 给已有工具额外加功能 |
| `public` | 常见目录名 | 放公开静态文件，比如图片、图标 |
| `pyproject.toml` | 配置文件 | Python 项目的现代配置文件 |
| Python | 编程语言 | AI、数据处理、后端服务常用语言 |
| React | Node.js 依赖包 | 用来做网页界面的工具包 |
| Release | 发布版本 | 给用户下载或查看的正式版本 |
| `requirements.txt` | 依赖清单 | Python 项目用它列出依赖包 |
| Runtime / 运行时 | 运行环境 | 让某种代码真正跑起来的环境 |
| Schema | 结构规则 | 规定数据应该有哪些字段、字段是什么类型 |
| scripts | 配置字段 | `package.json` 里的“命令菜单” |
| `scripts` 目录 | 常见目录名 | 放自动化脚本；注意它和 `package.json` 里的 `scripts` 字段不是一回事 |
| SDK | 开发工具包 | 一套给程序员调用某个平台/API 的工具包 |
| `server` | 常见目录名 | 放后端服务代码 |
| Server | 服务端 | 接收请求并返回结果的一方 |
| Shell | 命令解释器 | 读取你输入的命令并执行 |
| `src` | 常见目录名 | source 的缩写，放源代码 |
| sync | 动作/命令名字 | synchronize 的缩写，表示把两边内容同步到一致 |
| Template / 模板 | 起始材料 | 给新项目复制使用的基础结构 |
| Terminal / 终端 | 操作窗口 | 输入命令的窗口 |
| test | 命令名字 | 运行测试 |
| `.test.mjs` | 多段后缀 | 测试文件 + JavaScript 模块文件 |
| `tests` / `test` | 常见目录名 | 放测试代码 |
| Token | 访问凭证 | 证明“我有权限访问”的一串字符 |
| `.toml` | 文件后缀 | TOML 格式，常用于 Python/Rust 配置 |
| TOML | 配置格式 | 用 `key = value` 和 `[section]` 写分组 |
| `tools` | 常见目录名 | 放项目自带的小工具 |
| TypeScript / TS | 编程语言 | 更严格的 JavaScript |
| Uvicorn | Python 依赖包 | 用来启动 Python API 服务的工具包 |
| YAML | 配置格式 | 用 `key: value` 和缩进写层级 |
| `.yml` / `.yaml` | 文件后缀 | YAML 格式，常用于 Docker、自动化、部署配置 |
| 版本号 | 编号 | `19.0.0` 这种数字表示某个包的版本 |
---

## 0. 先建立一个最重要的观念

一个 GitHub 仓库不是“一堆代码”。

它是一个项目工作台。一个仓库里放着项目说明、代码、配置、依赖、启动方式、测试方式、部署方式和协作记录。

先把下面几个词看懂，后面读仓库会轻松很多。

| 名称 | 它是什么 | 例子 |
|---|---|---|
| 项目说明 | 给人看的说明书，解释项目用途和用法 | `README.md` 里写“这个项目做什么、怎么安装、怎么启动” |
| 源代码 | 真正实现功能的文件 | `src/index.ts` 写网页逻辑，`main.py` 写 Python 程序入口 |
| 配置文件 | 给工具和电脑读的规则文件 | `package.json` 告诉 npm 有哪些命令，`pyproject.toml` 告诉 Python 工具项目怎么构建 |
| 依赖清单 | 项目需要安装的工具包列表 | `requirements.txt` 写 Python 包，`package.json` 里的 `dependencies` 写 Node.js 包 |
| 启动命令 | 把项目运行起来的命令 | `npm run dev` 启动前端开发网站，`python main.py` 运行 Python 程序 |
| 测试代码 | 检查功能是否正常的代码 | `tests` 目录、`npm test`、`pytest` |
| 文档 | 给人看的使用说明、接口说明、开发说明 | `docs` 目录、`README.md`、`CONTRIBUTING.md` |
| 部署文件 | 把项目放到服务器、Docker、云平台运行的文件 | `Dockerfile`、`docker-compose.yml`、`nginx.conf` |
| 协作记录 | 多人修改项目时留下的记录 | branch、commit、PR、Issue |

### 0.1 配置文件是什么

配置文件就是“给工具看的设置说明”。

人读 README，工具读配置文件。

举例：

| 你要告诉谁 | 用什么文件告诉它 | 文件里写什么 |
|---|---|---|
| 告诉 npm 怎么启动项目 | `package.json` | `dev` 命令对应 `next dev` |
| 告诉 Python 工具项目叫什么、依赖什么 | `pyproject.toml` | 项目名、版本、依赖、测试配置 |
| 告诉 Docker 启动哪些服务 | `docker-compose.yml` | 前端、后端、数据库、端口 |
| 告诉程序端口和密钥 | `.env` | `PORT=3000`、`API_KEY=...` |

一个很小的配置文件例子：

```json
{
  "scripts": {
    "dev": "next dev"
  }
}
```

先不要急着理解代码，只看它的结构：

| 看到的名字 | 它是什么 | 意思 |
|---|---|---|
| `package.json` | Node.js 项目的配置文件 | 这个文件里保存项目菜单和依赖 |
| `scripts` | `package.json` 里的命令菜单 | 下面列出这个项目能运行哪些命令 |
| `dev` | 命令菜单里的一个名字 | development 的缩写，表示开发模式 |
| `next dev` | `dev` 真正对应的命令 | 用 Next.js 启动开发服务 |

这段配置的完整意思是：

> 当你运行 `npm run dev` 时，npm 会打开 `package.json`，找到 `scripts` 里的 `dev`，然后执行 `next dev`。

所以 `scripts` 不是一个文件。它是 `package.json` 里面的一个栏目。

`dev` 也不是固定魔法词。它是项目作者给“开发模式启动命令”起的名字。大多数 Node.js 项目都把开发模式叫 `dev`，所以你经常看到 `npm run dev`。

所以配置文件不是文章，也不是主功能代码。它的作用是告诉工具“按这些规则运行”。

### 0.2 依赖清单是什么

依赖清单就是“项目需要哪些现成工具包”的清单。

例子：

```txt
fastapi
uvicorn
```

在这个例子里，这两行写在 Python 项目的 `requirements.txt` 文件里。

它们不是普通文件名，而是 Python 依赖包的名字：

| 名字 | 它是什么 | 用来做什么 |
|---|---|---|
| `fastapi` | Python 依赖包 | 用 Python 写 API 服务 |
| `uvicorn` | Python 依赖包 | 启动 FastAPI 这类 Python Web 服务 |

这段依赖清单的意思是：

> 这个 Python 项目运行前，需要先安装 `fastapi` 和 `uvicorn` 这两个工具包。

Node.js 项目的依赖写在 `package.json` 里：

```json
{
  "dependencies": {
    "react": "19.0.0",
    "next": "15.0.0"
  }
}
```

这表示项目运行时需要 `react` 和 `next`。

逐项拆开：

| 看到的内容 | 它是什么 | 意思 |
|---|---|---|
| `dependencies` | 依赖清单栏目 | 项目运行时需要的包写在这里 |
| `react` | Node.js 依赖包 | 做网页界面的工具包 |
| `next` | Node.js 依赖包 | Next.js 框架的包名 |
| `19.0.0` | 版本号 | 安装 React 的 19.0.0 版本 |
| `15.0.0` | 版本号 | 安装 Next.js 的 15.0.0 版本 |

版本号可以理解成软件版本：

```text
19.0.0 = 第 19 个大版本.第 0 个小版本.第 0 个修补版本
```

版本号不同，功能和兼容性就会不同。依赖清单写版本号，是为了让项目在不同电脑上安装到一致的工具包。

### 0.3 启动命令是什么

启动命令就是“把项目跑起来”的命令。

例子：

| 命令 | 意思 |
|---|---|
| `npm install` | 先安装 Node.js 项目依赖 |
| `npm run dev` | 启动前端开发服务 |
| `python main.py` | 运行 Python 程序 |
| `docker compose up` | 用 Docker 一次启动多个服务 |

先记住这一句：

> 配置文件写规则，依赖清单列工具包，启动命令让项目运行。

### 0.4 sync 是什么

`sync` 是 synchronize 的缩写，意思是“同步”。

同步不是一种文件格式。同步是一种动作：

> 把两个地方的内容更新到一致。

看到 `sync` 时，先问三个问题：

1. 哪两个地方要保持一致？
2. 是从哪里更新到哪里？
3. 同步的是代码、依赖、配置、数据，还是文件？

常见例子：

| 看到的内容 | 同步哪两边 | 人话解释 |
|---|---|---|
| `uv sync` | 依赖清单和本机 Python 环境 | 按项目清单安装/调整 Python 依赖，让本机环境和项目要求一致 |
| `git pull` | GitHub 远程仓库和本地仓库 | 把远程最新修改同步到本地 |
| `sync data` | 远程数据和本地数据 | 把一边的数据复制或更新到另一边 |
| `sync config` | 配置来源和当前配置文件 | 把配置更新到一致 |

所以 `sync` 的核心不是“它是什么文件”，而是：

> 它要让哪两个地方变成一致。

所以你看仓库时，不要把它当成一堆陌生文件。把它拆成稳定的几个部分：

1. 给人看的说明区：README、docs、Wiki。
2. 给电脑运行的代码区：src、app、server、api。
3. 给工具读取的配置区：package.json、pyproject.toml、docker-compose.yml。
4. 给项目安装依赖的清单区：dependencies、requirements.txt、lock 文件。
5. 给项目验证质量的测试区：tests、test、spec。
6. 给项目上线运行的部署区：Dockerfile、Nginx、GitHub Actions。
7. 给团队协作的记录区：branch、commit、PR、Issue。

仓库作者可以换目录名、换框架、换工具，但这些部分的职责稳定不变。你要学的是“每个部分负责什么”，而不是只记某一个仓库的摆放方式。

---

## 1. 仓库是什么

### 1.1 GitHub 是什么

GitHub 可以理解成“项目协作平台”。

它不是普通网盘，因为它不仅保存文件，还保存每一次修改记录、每个人做了什么、为什么改、能不能合并。

你在 GitHub 上常见这些东西：

| 名称 | 人话解释 |
|---|---|
| Repository / repo | 仓库，一个完整项目文件夹 |
| README | 项目说明书 |
| Code | 文件和代码 |
| Issues | 问题、需求、任务卡 |
| Pull requests / PR | 请求把某个修改合并进项目 |
| Actions | 自动检查、自动构建、自动部署 |
| Releases | 正式发布版本 |
| Branches | 分支，不同修改线 |
| Commits | 每一次保存的修改记录 |

### 1.2 仓库不只放软件代码

仓库按用途可以分成这些类型：

| 仓库类型 | 你会看到什么 | 它负责什么 |
|---|---|---|
| 前端网站 | `package.json`, `src`, `app`, `components` | 做网页界面 |
| 后端服务 | `api`, `server`, `app.py`, `main.py`, `routes` | 提供接口和业务逻辑 |
| Python 工具 | `pyproject.toml`, `requirements.txt`, `.venv` | 数据处理、AI、脚本工具 |
| 文档站 | `docs`, `docusaurus.config`, `mkdocs.yml` | 做说明文档网站 |
| AI 应用 | `prompts`, `agents`, `rag`, `knowledge`, `models` | 调用模型、做知识库或智能体 |
| MCP 工具 | `mcp`, `server`, `tools`, `stdio`, `sse` | 让 AI 调用外部工具 |
| 数据库项目 | `sql`, `migrations`, `schema`, `prisma` | 管理数据结构 |
| Docker 部署项目 | `Dockerfile`, `docker-compose.yml` | 打包和启动服务 |
| SDK / 开发工具包 | `sdk`, `client`, `examples`, `package.json`, `pyproject.toml` | 给别的程序调用的平台工具包 |
| 模板项目 | `template`, `boilerplate`, `starter` | 给别人复制使用的项目骨架 |

---

## 2. 仓库里的每个部分是什么

一个仓库由两层组成：

| 层 | 你看到什么 | 它负责什么 |
|---|---|---|
| GitHub 页面层 | Code、Issues、Pull requests、Actions、Releases | 展示项目、协作、自动化、发布记录 |
| 文件内容层 | README、src、package.json、Dockerfile、tests | 保存项目说明、代码、配置、测试、部署文件 |

这两层都属于仓库。GitHub 页面层负责协作和管理，文件内容层负责项目本身。

### 2.1 GitHub 页面上的部分

打开 GitHub 仓库页面后，你会看到这些区域：

| 页面部分 | 它是什么 | 你看到它时怎么理解 |
|---|---|---|
| 仓库名 | 项目的名字 | 用来识别项目 |
| About | 项目简介和标签 | 用来说明项目用途 |
| Code | 文件列表 | 仓库真正保存的文件 |
| README 显示区 | 首页自动展示的说明书 | 给人看的入门说明 |
| Issues | 问题和任务 | 记录 bug、需求、待办 |
| Pull requests | 修改合并请求 | 记录别人准备合并的修改 |
| Actions | 自动化流程 | 自动测试、构建、部署 |
| Projects | 项目看板 | 管理任务进度 |
| Wiki | 项目知识库 | 放更长的说明资料 |
| Security | 安全提醒 | 依赖漏洞、安全策略 |
| Insights | 项目统计 | 提交、贡献者、活跃度 |
| Releases | 正式发布版本 | 给用户下载或查看版本说明 |
| Branches | 分支列表 | 查看不同修改线 |
| Commits | 修改历史 | 查看每一次保存记录 |

这些页面部分不受项目语言影响。Python 项目、前端项目、AI 项目都有这些协作区域。

### 2.2 文件列表里的部分

点进 Code 后，你看到的是文件内容层。下面这张表不是让你一次背完，而是给你一个“归类框架”。

如果表里的 `src`、`package.json`、`Dockerfile` 现在还像乱码，先记住这一点：

> 每个文件/目录都不是孤立字符，它一定属于某个职责区。你暂时看不懂名字时，先问“它属于说明、代码、配置、依赖、测试、部署、协作里的哪一类？”

文件内容层可以拆成这些稳定部分：

| 部分 | 常见文件/目录 | 它负责什么 |
|---|---|---|
| 说明区 | `README.md`, `docs`, `Wiki` | 给人解释项目用途和用法 |
| 源代码区 | `src`, `app`, `server`, `api`, `components` | 实现项目功能 |
| 配置区 | `package.json`, `pyproject.toml`, `.npmrc`, `tsconfig.json` | 告诉工具怎么运行、检查、构建项目 |
| 依赖区 | `dependencies`, `requirements.txt`, `uv.lock`, `package-lock.json` | 记录项目需要哪些工具包 |
| 环境变量区 | `.env.example`, `.env` | 记录端口、密钥、数据库地址等运行参数 |
| 测试区 | `tests`, `test`, `spec`, `pytest`, `vitest` | 检查项目功能是否正常 |
| 脚本区 | `scripts`, `bin`, `tools` | 放自动化小工具和命令 |
| 数据区 | `data`, `fixtures`, `examples` | 放样例数据、测试数据、演示数据 |
| 部署区 | `Dockerfile`, `docker-compose.yml`, `nginx.conf` | 把项目放进容器或服务器运行 |
| 自动化区 | `.github/workflows` | GitHub 自动测试、构建、发布 |
| 忽略规则区 | `.gitignore`, `.dockerignore` | 告诉工具哪些文件不要处理 |

仓库设计者可以把目录命名成 `src`、`app`、`server` 或 `packages`，但这些目录仍然会落到上面某个职责里。

### 2.3 README.md 是说明区

`README.md` 是项目说明书。

它回答这些问题：

- 这个项目是什么？
- 适合谁用？
- 怎么安装？
- 怎么启动？
- 需要什么环境？
- 有哪些配置？
- 怎么测试？
- 怎么部署？

README 的职责是说明，不负责运行项目。代码的职责是实现功能，配置文件的职责是告诉工具怎么处理项目。

### 2.4 配置文件属于配置区

配置文件是给工具读取的规则。它不负责实现业务功能，而是告诉工具如何安装、运行、检查、构建、部署项目。

| 文件 | 说明 |
|---|---|
| `package.json` | Node.js / JavaScript / TypeScript 项目的菜单和依赖清单 |
| `pyproject.toml` | 现代 Python 项目的配置文件 |
| `requirements.txt` | Python 依赖清单 |
| `Dockerfile` | 如何把项目打包成 Docker 镜像 |
| `docker-compose.yml` | 一次启动多个服务 |
| `.env.example` | 环境变量模板 |
| `.nvmrc` | 推荐 Node.js 版本 |
| `.npmrc` | npm 配置，比如源、代理、安装路径 |
| `tsconfig.json` | TypeScript 配置 |
| `vite.config.ts` | Vite 前端项目配置 |
| `next.config.js` | Next.js 项目配置 |
| `pnpm-lock.yaml` / `package-lock.json` | 依赖锁定文件 |
| `.github/workflows` | GitHub 自动化流程 |

### 2.5 目录属于功能分区

目录名告诉你项目怎么分层。

| 目录 | 人话解释 |
|---|---|
| `src` | 源代码主目录 |
| `app` | 应用代码；Next.js 和 Python 项目都会使用这个目录名 |
| `pages` | 页面路由，常见于老式 Next.js 项目 |
| `components` | 页面组件，比如按钮、表格、弹窗 |
| `api` | 接口相关代码 |
| `server` | 后端服务代码 |
| `client` | 前端代码 |
| `web` | 网页端代码 |
| `backend` | 后端代码 |
| `frontend` | 前端代码 |
| `docs` | 文档 |
| `scripts` | 自动化脚本 |
| `tests` | 测试代码 |
| `public` | 静态资源，比如图片、图标 |
| `assets` | 图片、字体、样式资源 |
| `config` | 配置 |
| `data` | 数据文件 |
| `migrations` | 数据库结构变更记录 |
| `examples` | 示例 |
| `tools` | 工具函数或命令工具 |
| `prompts` | AI 提示词 |
| `agents` | 智能体相关 |
| `skills` | 可复用的 AI 技能 |

同一个职责可以有不同目录名。例如网页界面代码可以放在 `src`、`app`、`pages`、`web`；后端代码可以放在 `api`、`server`、`backend`。目录名不同，职责仍然可以归入“源代码区”。

### 2.6 文件名、后缀、颜色状态的通用规则

你遇到陌生文件时，不要只盯着一个词。按这四个问题判断：

1. 它是文件还是文件夹？
2. 它在 VS Code 里有没有特殊颜色或标记？
3. 它的名字能拆成几段？
4. 它在什么位置？

#### 2.6.1 先分清文件和文件夹

同一个词可以同时出现在文件名、文件夹名、命令名里。先看“类型”，再看“名字”。

| 看到的形式 | 类型 | 例子 | 人话解释 |
|---|---|---|---|
| 左侧是文件图标 | 文件 | `package.json` | 打开后看到具体内容 |
| 左侧是文件夹图标 | 文件夹 | `package/` | 里面还能继续放文件 |
| 名字后面写 `/` | 文件夹 | `packages/` | 斜杠表示目录 |
| 出现在命令里 | 命令或参数 | `npm run build` | 这是让工具执行的动作 |

例子：

| 名字 | 它是什么 |
|---|---|
| `package.json` | 文件 |
| `package/` | 文件夹 |
| `build/` | 文件夹 |
| `build` 命令 | `package.json` 的 `scripts` 里的命令名 |
| `scripts/` | 文件夹 |
| `scripts` 字段 | `package.json` 里的命令菜单 |

所以不要只问“package 是什么”。要问：

> 这里的 `package` 是文件、文件夹、字段，还是命令里的一个词？

同一个词在不同位置会变成不同含义：

| 词 | 出现形式 | 含义 |
|---|---|---|
| `test` | `test/` 或 `tests/` | 测试目录 |
| `test` | `user.test.mjs` | 文件名中间段，表示这是测试文件 |
| `test` | `npm test` | 命令名，表示运行测试 |
| `env` | `.env` | 环境变量文件 |
| `env` | `.env.example` | 环境变量模板文件 |
| `config` | `config/` | 配置目录 |
| `config` | `config.json` | JSON 配置文件 |
| `config` | `config.local.json` | 本地 JSON 配置文件 |
| `lock` | `uv.lock` | 依赖锁定文件 |
| `lock` | `package-lock.json` | npm 依赖锁定文件 |

#### 2.6.2 VS Code 里灰色代表状态，不代表文件类型

VS Code 里的颜色是状态提示，不是文件内容的一部分。

文件或文件夹显示灰色时，先按这个规则理解：

> 它被某个规则忽略、排除、隐藏，或者属于生成出来的内容。

最常见来源是 `.gitignore`。`.gitignore` 告诉 Git 哪些文件或文件夹不要提交。

```gitignore
.env
node_modules/
dist/
```

通用判断：

1. 看到灰色文件或文件夹，先找 `.gitignore`。
2. 在 `.gitignore` 里搜索这个名字。
3. 搜到了，说明它被 Git 忽略。
4. 没搜到，再看 VS Code 的 `files.exclude` 或 `search.exclude` 设置。

更完整的 VS Code 状态表见第 15.4 节。

#### 2.6.3 文件名可以拆成多段

文件名不是只能有一个后缀。很多文件名由“主题 + 用途 + 格式”组成。

从右往左拆：

```text
user.test.mjs
```

| 部分 | 意思 |
|---|---|
| `user` | 文件主题 |
| `.test` | 用途：测试文件 |
| `.mjs` | 格式：JavaScript 模块文件 |

常见多段名字：

| 文件名 | 从右往左理解 |
|---|---|
| `button.test.ts` | TypeScript 格式的测试文件 |
| `user.spec.js` | JavaScript 格式的测试规格文件 |
| `App.module.css` | 组件专用 CSS 样式文件 |
| `config.local.json` | 本地用的 JSON 配置文件 |
| `.env.example` | 环境变量模板文件 |
| `.env.local` | 本地环境变量文件 |

#### 2.6.4 后缀主要说明格式，不单独决定用途

后缀告诉你“文件里面按什么格式写”。用途要结合文件名和位置判断。

| 判断线索 | 例子 | 说明 |
|---|---|---|
| 后缀 | `.yml` | 按 YAML 格式写 |
| 文件名 | `docker-compose.yml` | 和 Docker Compose 有关 |
| 所在位置 | `.github/workflows/test.yml` | GitHub 自动化流程 |

同样是 `.yml`：

| 文件 | 用途 |
|---|---|
| `docker-compose.yml` | Docker 多服务启动配置 |
| `.github/workflows/test.yml` | GitHub 自动测试流程 |
| `mkdocs.yml` | 文档站配置 |
| `environment.yml` | Conda 环境配置 |

#### 2.6.5 常见格式对照

| 格式 | 长相 | 常见后缀 | 先归入哪一类 |
|---|---|---|---|
| JSON | `"key": "value"`，有 `{}` | `.json` | 配置/数据区 |
| TOML | `key = "value"`，有 `[section]` | `.toml` | 配置区 |
| YAML | `key: value`，有层级时用缩进 | `.yml`, `.yaml` | 配置/部署区 |
| ENV | `KEY=VALUE` | `.env` | 环境变量区 |
| JavaScript 模块 | `import` / `export` | `.mjs` | 代码区 |
| TypeScript | 类型、接口、`.ts` 代码 | `.ts`, `.tsx` | 代码区 |
| Markdown | 标题、列表、段落 | `.md` | 说明区 |
| Handlebars 模板 | 普通文本里夹着 `{{name}}` | `.hbs` | 模板区 |
| CSV 表格数据 | 第一行是列名，后面一行一条记录 | `.csv` | 数据区 |

YAML 有一个容易误解的点：不是所有 YAML 都必须缩进。没有上下级关系时，它可以一行一个配置项：

```yaml
schema_version: 1
classification_system: CPC
status: scaffold
mappings: []
```

这里每一行都在同一层，所以没有缩进。

#### 2.6.6 特殊文件名不是普通后缀

| 名字 | 它是什么 | 人话解释 |
|---|---|---|
| `.gitignore` | Git 忽略规则 | 告诉 Git 哪些文件/文件夹不要提交 |
| `.gitkeep` | 占位文件 | 让 Git 保存空文件夹 |
| `.env.example` | 模板文件 | 告诉你 `.env` 需要填哪些项 |
| `package-lock.json` | 锁定文件 | 固定 npm 依赖版本 |
| `pyproject.toml` | Python 配置文件 | 配置 Python 项目和工具 |
| `docker-compose.yml` | Docker 配置文件 | 一次启动多个服务 |

遇到陌生名字时，用一句话归类：

> 这是【文件/文件夹/命令/字段】，它按【格式】写，位于【位置】，负责【职责】。

---

## 3. 用 5 个问题判断一个仓库

每次打开仓库，都问自己这 5 个问题：

1. 这个仓库是做什么的？
2. 它属于前端、后端、AI、数据库、文档、部署、工具，还是混合项目？
3. 它主要用什么语言？
4. 它怎么安装、启动、测试？
5. 我现在需要看懂哪一层，不需要看哪一层？

### 3.1 一句话判断模板

你可以这样写：

> 这个仓库是一个【项目类型】，主要用【语言/工具】实现，用来【用途】。运行它需要【环境/依赖】，入口文件/核心目录是【文件或目录】。

例子：

> 这个仓库是一个前端网站，主要用 TypeScript 和 Next.js 实现，用来展示平台页面。运行它需要 Node.js 和 npm，核心目录是 `app`、`components` 和 `package.json`。

---

## 4. 常见文件：看到它就知道什么意思

### 4.1 多数仓库都会出现的文件

| 文件 | 人话解释 | 新手怎么处理 |
|---|---|---|
| `README.md` | 项目说明书 | 归入说明区，用来理解项目用途和用法 |
| `LICENSE` | 开源许可证 | 知道能不能用、怎么用 |
| `.gitignore` | 告诉 Git 哪些文件不要提交 | 被忽略的文件在 VS Code 里会显示灰色 |
| `CHANGELOG.md` | 版本更新记录 | 看项目变化 |
| `CONTRIBUTING.md` | 贡献指南 | 开 PR 前看 |
| `CODE_OF_CONDUCT.md` | 社区行为规则 | 开源项目常见 |

### 4.2 Node.js 项目常见文件

| 文件/目录 | 人话解释 |
|---|---|
| `package.json` | 项目菜单、依赖、脚本 |
| `node_modules` | npm 下载的依赖包，体积很大，不提交 |
| `package-lock.json` | npm 锁定依赖版本 |
| `pnpm-lock.yaml` | pnpm 锁定依赖版本 |
| `yarn.lock` | yarn 锁定依赖版本 |
| `.nvmrc` | 推荐 Node 版本 |
| `.npmrc` | npm 配置 |
| `tsconfig.json` | TypeScript 配置 |
| `src` | 源代码 |

### 4.3 Python 项目常见文件

| 文件/目录 | 人话解释 |
|---|---|
| `pyproject.toml` | Python 项目配置、依赖、构建方式 |
| `requirements.txt` | Python 依赖清单 |
| `.venv` | 本地虚拟环境 |
| `venv` | 另一个常见虚拟环境目录名 |
| `main.py` | 程序入口文件名 |
| `app.py` | 应用入口文件名 |
| `notebooks` | Jupyter 笔记本 |
| `tests` | 测试 |

### 4.4 Docker 和部署常见文件

| 文件 | 人话解释 |
|---|---|
| `Dockerfile` | 说明如何打包一个运行环境 |
| `docker-compose.yml` | 一次启动多个服务，比如前端、后端、数据库 |
| `.dockerignore` | 打包 Docker 时忽略哪些文件 |
| `nginx.conf` | Nginx 服务器配置 |
| `.github/workflows/*.yml` | GitHub 自动检查、构建、部署 |

### 4.5 AI / Agent / MCP 项目常见文件

| 文件/目录 | 人话解释 |
|---|---|
| `prompts` | 提示词 |
| `agents` | 智能体流程 |
| `skills` | 可复用技能 |
| `tools` | AI 可以调用的工具 |
| `mcp` | MCP 相关代码 |
| `server` | MCP 或 API 服务 |
| `knowledge` | 知识库资料 |
| `rag` | 检索增强生成相关 |
| `models` | 模型配置或模型代码 |

---

## 5. JavaScript、TypeScript、Node.js、npm 是什么

如果你完全没接触过编程，先不要急着记命令。你只需要先搞懂它们之间的关系。

一句话版：

> JavaScript 是一种语言；TypeScript 是更严格的 JavaScript；Node.js 让 JavaScript 能在你电脑和服务器上运行；npm 帮 Node.js 项目下载工具包和运行命令。

### 5.1 JavaScript 是什么

JavaScript，常缩写成 JS，是一种编程语言。

最早它主要用来让网页“动起来”。

比如：

- 点击按钮后弹出窗口。
- 输入内容后马上检查格式。
- 页面不用刷新也能加载新数据。
- 表格、图表、聊天框、菜单可以交互。

你在仓库里看到这些文件，就按 JavaScript 文件阅读：

| 文件 | 说明 |
|---|---|
| `.js` | JavaScript 文件 |
| `.jsx` | 写 React 页面组件的 JavaScript 文件 |

人话理解：

> JavaScript 就像网页世界里最常见的“操作语言”。

### 5.2 TypeScript 是什么

TypeScript，常缩写成 TS，是 JavaScript 的升级版。

它不是完全新的世界，而是在 JavaScript 上加了“类型检查”。

类型检查是什么意思？

比如一个函数需要数字，你却传了一段文字。JavaScript 在运行时暴露错误；TypeScript 在写代码或构建时提前提醒。

你在仓库里看到这些文件，就按 TypeScript 文件阅读：

| 文件 | 说明 |
|---|---|
| `.ts` | TypeScript 文件 |
| `.tsx` | 写 React 页面组件的 TypeScript 文件 |
| `tsconfig.json` | TypeScript 配置文件 |

人话理解：

> TypeScript 是“更严格、更适合大项目协作的 JavaScript”。

新手不用一开始会写 TypeScript。你只要知道：

- `.js` / `.jsx` 按 JavaScript 阅读。
- `.ts` / `.tsx` 按 TypeScript 阅读。
- TypeScript 项目构建后变成 JavaScript 再运行。

### 5.3 Node.js 是什么

Node.js 不是一门语言。

Node.js 是 JavaScript 的运行环境。

什么叫运行环境？

你可以这样理解：

> 语言本身像“菜谱”，运行环境像“厨房”。没有厨房，菜谱不能自己变成菜。

JavaScript 最早主要在浏览器里运行，比如 Chrome、Edge、Firefox。

但后来大家希望 JavaScript 也能做这些事：

- 在电脑终端里运行工具。
- 写后端服务。
- 读写文件。
- 启动本地开发网站。
- 做命令行工具。
- 做 MCP 工具。

于是就有了 Node.js。

所以：

| 场景 | 谁在运行 JavaScript |
|---|---|
| 网页里点击按钮 | 浏览器运行 JavaScript |
| 终端里执行 `npm run dev` | Node.js 相关工具在运行 JavaScript |
| 后端服务用 JS/TS 写 | Node.js 在服务器运行 JavaScript |

你看到 README 里写：

```bash
node -v
```

意思是检查你电脑上的 Node.js 版本。

### 5.4 npm 是什么

npm 是 Node.js 世界里的包管理器和命令工具。

先解释“包”是什么。

包就是别人写好的工具代码，你的项目可以拿来用。

比如：

- 做网页界面的包。
- 处理日期的包。
- 连接数据库的包。
- 启动开发服务器的包。
- 检查代码格式的包。

如果每个项目都从零写，会非常慢。所以项目会依赖很多包。

npm 主要做两件事：

| npm 做什么 | 常见命令 | 人话解释 |
|---|---|---|
| 下载依赖包 | `npm install` | 把项目需要的工具包装到本地 |
| 运行项目命令 | `npm run dev` | 按 `package.json` 里的菜单启动某个任务 |

你可以把 npm 理解成：

> Node.js 项目的“应用商店 + 命令遥控器”。

### 5.5 `package.json` 是什么

`package.json` 是 Node.js 项目的说明和菜单文件。

它记录：

- 项目名字。
- 项目版本。
- 项目需要哪些依赖包。
- 可以运行哪些命令。
- 这个项目是网站、工具、库，还是服务。

你不用一开始读懂全部内容。重点识别这三块：

| 区域 | 人话解释 |
|---|---|
| `scripts` | 命令菜单 |
| `dependencies` | 项目运行需要的包 |
| `devDependencies` | 开发、测试、构建时需要的包 |

### 5.6 它们之间的关系

把它们放在一起看：

```text
JavaScript
  一门语言，常用于网页和工具开发

TypeScript
  更严格的 JavaScript，大项目常用

Node.js
  让 JavaScript/TypeScript 相关工具能在电脑或服务器上运行

npm
  帮 Node.js 项目下载依赖、运行命令

package.json
  记录这个 Node.js 项目需要什么包、有哪些命令
```

再用开餐馆比喻：

| 技术词 | 比喻 |
|---|---|
| JavaScript | 做菜的语言/菜谱写法 |
| TypeScript | 写得更严格、更不容易出错的菜谱 |
| Node.js | 厨房，让菜谱真的能执行 |
| npm | 采购员 + 菜单遥控器 |
| package.json | 采购清单 + 后厨操作菜单 |
| node_modules | 采购回来的食材和工具 |

### 5.7 看到这些命令时不要混

| 命令 | 它在做什么 |
|---|---|
| `node -v` | 看 Node.js 版本 |
| `npm -v` | 看 npm 版本 |
| `npm install` | 下载依赖 |
| `npm run dev` | 启动开发模式 |
| `npm run build` | 构建正式版本 |
| `npm test` | 运行测试 |

最重要的一句：

> `npm install` 是准备材料，`npm run dev` 才是把项目跑起来。

---

## 6. `package.json` 怎么读

如果仓库里有 `package.json`，先按 Node.js 项目阅读。

重点识别三个地方：

```json
{
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "test": "vitest"
  },
  "dependencies": {},
  "devDependencies": {}
}
```

### 6.1 `scripts` 是命令菜单

| 脚本 | 常见命令 | 人话解释 |
|---|---|---|
| `dev` | `npm run dev` | 启动开发模式 |
| `build` | `npm run build` | 生成正式版本 |
| `start` | `npm start` | 启动正式服务 |
| `test` | `npm test` | 跑测试 |
| `lint` | `npm run lint` | 检查代码风格和常见错误 |
| `format` | `npm run format` | 格式化代码 |

### 6.2 `dependencies` 是正式依赖

项目运行时需要它们。

比如：

- `react`：做前端界面。
- `next`：做 Next.js 网站。
- `express`：做 Node 后端服务。
- `@modelcontextprotocol/sdk`：做 MCP 工具。

### 6.3 `devDependencies` 是开发依赖

开发、测试、构建时需要它们；正式运行阶段不依赖这类工具。

比如：

- `typescript`
- `eslint`
- `vite`
- `vitest`

### 6.4 为什么有 `package.json`，还有 `package/` 或 `packages/`

`package.json` 是文件，`package/` 和 `packages/` 是文件夹。它们名字相近，但类型不同。

| 名字 | 类型 | 人话解释 |
|---|---|---|
| `package.json` | 文件 | Node.js 项目的配置文件，记录命令、依赖、项目名称 |
| `package/` | 文件夹 | 放一个子项目、一个可发布包，或打包后的内容 |
| `packages/` | 文件夹 | 放多个子项目或多个包 |

#### 为什么根目录有 `package.json`，`package/` 里面还有 `package.json`

这是多包项目或子项目结构。

例子：

```text
my-repo/
  package.json
  packages/
    web/
      package.json
    cli/
      package.json
```

逐层解释：

| 位置 | 负责什么 |
|---|---|
| 根目录 `package.json` | 管理整个仓库，比如统一安装、统一测试、统一构建 |
| `packages/web/package.json` | 管理 web 这个子项目自己的依赖和命令 |
| `packages/cli/package.json` | 管理 cli 这个子项目自己的依赖和命令 |

这种仓库叫 monorepo，中文常说“单仓多包”。

人话：

> 一个大仓库里面放了多个小项目，每个小项目都有自己的 `package.json`。

最重要的是不要被名字骗到：

> `package.json` 是配置文件；`package` / `packages` 是目录。目录里面可以继续放自己的 `package.json`。

同类规则见第 2.6 节：同一个词可以出现在文件名、文件夹名、字段名、命令名里，先判断类型，再判断职责。

---

## 7. Python 项目怎么读

如果仓库里有 `pyproject.toml` 或 `requirements.txt`，先按 Python 项目阅读。

### 7.1 依赖管理文件

| 看到什么 | 说明 |
|---|---|
| `requirements.txt` | 常见老式依赖清单 |
| `pyproject.toml` | 现代 Python 项目配置 |
| `uv.lock` | 使用 uv 管理依赖 |
| `poetry.lock` | 使用 Poetry 管理依赖 |
| `environment.yml` | 使用 Conda 管理环境 |

### 7.2 常见命令

| 命令 | 人话解释 |
|---|---|
| `python --version` | 看 Python 版本 |
| `python -m venv .venv` | 创建虚拟环境 |
| `pip install -r requirements.txt` | 安装依赖 |
| `uv sync` | 用 uv 同步环境 |
| `python main.py` | 运行入口文件 |
| `pytest` | 跑测试 |

### 7.3 什么是虚拟环境

虚拟环境就是给每个 Python 项目单独准备一个“小房间”。

它的作用是：

- A 项目需要旧版本工具包。
- B 项目需要新版本工具包。
- 两个项目互不影响。

看到 `.venv` 时，你只要知道：这是 Python 项目的本地环境，一般不提交到 GitHub。

### 7.4 Jupyter 笔记本是什么

Jupyter Notebook，中文常叫 Jupyter 笔记本，是一种“边写说明、边运行代码、边看结果”的文件形式。

它常见于：

- 数据分析。
- AI 实验。
- 机器学习训练。
- 图表展示。
- 教学演示。
- 科研计算过程记录。

你在仓库里看到这些内容，就按 Jupyter 相关内容阅读：

| 文件/目录 | 人话解释 |
|---|---|
| `.ipynb` | Jupyter 笔记本文件 |
| `notebooks` | 专门放笔记本的目录 |
| `*.ipynb_checkpoints` | Jupyter 自动生成的临时检查点，一般不用看 |

Jupyter 笔记本不是普通代码文件。它更像一份“可运行的实验记录”。

里面按单元格排列：

| 单元格类型 | 用途 |
|---|---|
| Markdown 单元格 | 写解释、标题、公式、备注 |
| Code 单元格 | 写代码，并能直接运行 |
| Output 输出 | 显示代码运行结果，比如表格、图片、图表 |

你可以这样理解：

> 普通 `.py` 文件像一篇连续的程序；Jupyter 笔记本像一本实验手册，每一步旁边都能放解释和运行结果。

新手看到 `.ipynb` 时，不要急着逐行读代码。先识别：

1. 标题和文字说明，它在做什么实验。
2. 前几格导入了哪些工具包。
3. 中间读取了什么数据。
4. 最后输出了什么图表或结果。

在 AI、LCA、数据分析类仓库里，Jupyter 常常不是正式产品入口，而是用来探索、验证、演示思路。

---

## 8. Git 和 GitHub 操作是什么

### 8.1 Git 是什么

Git 是版本控制工具。

人话：

> Git 负责记录项目每一次修改，让你知道谁改了什么，也能回到以前的版本。

### 8.2 GitHub 是什么

GitHub 是基于 Git 的云端协作平台。

人话：

> GitHub 让很多人可以围绕同一个项目协作、审核、讨论、合并。

### 8.3 最常见操作

| 操作 | 命令 | 人话解释 |
|---|---|---|
| 看状态 | `git status` | 看哪些文件被改了 |
| 看具体修改 | `git diff` | 看文件里改了什么 |
| 创建分支 | `git checkout -b fix-name` | 开一条安全修改线 |
| 暂存修改 | `git add .` | 把修改加入本次提交 |
| 提交修改 | `git commit -m "说明"` | 保存一次修改记录 |
| 上传 | `git push` | 把本地修改传到 GitHub |
| 拉取 | `git pull` | 把 GitHub 最新修改同步到本地 |
| 看远程地址 | `git remote -v` | 看这个项目连着哪个 GitHub 仓库 |

### 8.4 什么是分支

分支就是一条修改线。

你可以理解为：

- `main`：正式线。
- `dev`：开发线。
- `fix-login-error`：修某个问题的临时线。

新手原则：

> 不要直接在 `main` 上乱改。先新建分支，再修改。

### 8.5 什么是 PR

PR 是 Pull Request。

人话：

> 我在一个分支上改好了，请你帮我看看，没问题就合并到正式分支。

PR 页面有四个重点：

| 标签 | 看什么 |
|---|---|
| Conversation | 为什么改、别人怎么讨论 |
| Commits | 每一次提交 |
| Checks | 自动测试有没有通过 |
| Files changed | 具体改了哪些文件 |

---

## 9. 命令行、终端、GUI 是什么

### 9.1 终端是什么

终端就是输入命令的窗口。

你会见到这些终端：

- Windows PowerShell
- Windows Terminal
- macOS Terminal
- VS Code Terminal
- WSL Terminal

### 9.2 CLI 是什么

CLI 是 Command Line Interface，命令行界面。

人话：

> 用输入命令的方式操作软件。

比如：

```bash
npm install
npm run dev
git status
python main.py
docker ps
```

### 9.3 GUI 是什么

GUI 是 Graphical User Interface，图形界面。

人话：

> 有按钮、有菜单、有窗口的操作界面。

比如：

- VS Code 左侧 Source Control 面板。
- GitHub 网页。
- Docker Desktop。

### 9.4 新手怎么选

能用 GUI 看清楚时，先用 GUI。

README 里的安装和启动以命令行为主。

你不用害怕命令。新手先做到：

- 会复制命令。
- 会看自己在哪个目录。
- 会判断报错属于哪一层。

---

## 10. 安装、启动、构建、测试分别是什么

这是新手最容易混的四件事。

| 操作 | 常见命令 | 人话解释 |
|---|---|---|
| 安装依赖 | `npm install`, `uv sync`, `pip install -r requirements.txt` | 下载项目需要的工具包 |
| 启动开发服务 | `npm run dev`, `python app.py` | 在本地跑起来给开发调试 |
| 构建 | `npm run build` | 生成正式发布用的文件 |
| 测试 | `npm test`, `pytest` | 检查功能有没有坏 |
| 格式检查 | `npm run lint` | 检查代码风格或潜在错误 |
| 部署 | `docker run`, `docker compose up` | 放到容器或服务器里运行 |

### 10.1 安装依赖不是启动项目

`npm install` 只是下载依赖。

它不等于项目已经运行。

安装后继续运行：

```bash
npm run dev
```

### 10.2 `npm run dev` 和 `npm run build` 不一样

`npm run dev` 是开发模式，方便边改边看。

`npm run build` 是正式构建，检查项目能不能生成正式版本。

### 10.3 `.env` 是配置，不是代码

`.env` 放：

- API Key
- 数据库地址
- 端口
- 密码
- 模型地址
- 代理配置

重要原则：

> 真实 `.env` 不能提交到 GitHub。仓库里放 `.env.example`。

---

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

## 12. Docker、WSL、端口、localhost、Nginx 是什么

### 12.1 Docker

Docker 是把运行环境打包的工具。

人话：

> 把“代码 + 依赖 + 系统环境”装进一个盒子，换电脑也能尽量一样运行。

为什么需要 Docker？

因为现实里经常出现这种情况：

- A 电脑能运行，B 电脑不能运行。
- 你装的是 Python 3.12，项目需要 Python 3.10。
- 你本机没有数据库，但项目需要 PostgreSQL。
- 后端、前端、数据库、缓存要一起启动，新手很容易漏步骤。

Docker 想解决的是：

> 不要让每个人都手动搭一遍复杂环境，而是把环境写成配置，让电脑按配置启动。

看到这些文件就想到 Docker：

- `Dockerfile`
- `docker-compose.yml`
- `.dockerignore`

几个核心词先这样理解：

| 词 | 人话解释 |
|---|---|
| Image / 镜像 | 打包好的运行环境模板，像“做好的盒子模板” |
| Container / 容器 | 按镜像启动出来的一个正在运行的实例 |
| Dockerfile | 告诉 Docker 怎么制作镜像 |
| docker-compose.yml | 告诉 Docker 一次启动哪些服务、端口、环境变量 |
| Volume / 数据卷 | 让容器里的数据能保存到外面 |
| Port mapping / 端口映射 | 把容器里的端口接到你电脑上的端口 |

`Dockerfile` 和 `docker-compose.yml` 的区别：

| 文件 | 重点 |
|---|---|
| `Dockerfile` | 怎么做一个运行环境 |
| `docker-compose.yml` | 怎么把一个或多个服务一起跑起来 |

例子：

一个完整项目包含这些服务：

- 前端网站。
- 后端 API。
- PostgreSQL 数据库。
- Redis 缓存。

用 `docker-compose.yml` 就可以把这些服务写在一个文件里，一条命令一起启动。

常见命令：

| 命令 | 人话解释 |
|---|---|
| `docker ps` | 看正在运行的容器 |
| `docker run ...` | 启动一个容器 |
| `docker compose up` | 按 compose 配置启动一组服务 |
| `docker stop <id>` | 停止容器 |

新手看到 Docker 时，先掌握到这个程度就够：

1. 它是为了解决环境一致性。
2. `Dockerfile` 是做镜像。
3. `docker-compose.yml` 是启动一组服务。
4. 端口映射决定你用哪个 `localhost:端口` 访问服务。
5. 不要一开始就改 Docker 配置，先读 README 里的启动步骤。

### 12.2 WSL

WSL 是 Windows Subsystem for Linux。

人话：

> 在 Windows 里跑一个 Linux 环境。

很多开发工具在 Linux 环境里更自然，所以 Windows 用户常会遇到 WSL。

### 12.3 端口

端口是服务入口编号。

比如：

```text
http://localhost:3000
http://localhost:8000
```

这里 `3000` 和 `8000` 就是端口。

如果报错 `port already in use`，表示这个端口已经被别的程序占用了。

### 12.4 localhost

`localhost` 指你当前这台电脑。

如果 README 说：

```text
Open http://localhost:3000
```

意思是：

> 项目在你本机启动后，用浏览器打开这个地址。

### 12.5 Nginx 是什么

Nginx 读作 engine-x。它是一种常见的服务器软件。

新手可以先把它理解成：

> Nginx 是站在用户和真正服务之间的“门口接待员”和“转发员”。

它经常做这些事：

| Nginx 做什么 | 人话解释 |
|---|---|
| 静态网站服务 | 把打包好的网页文件发给浏览器 |
| 反向代理 | 用户访问一个地址，Nginx 转发给后端服务 |
| 端口转发 | 外面访问 80/443，里面转到 3000/8000 |
| HTTPS 配置 | 配证书，让网站支持安全访问 |
| 负载均衡 | 多个后端服务之间分流请求 |

你在仓库里看到这些文件，就按 Nginx 配置阅读：

| 文件/目录 | 人话解释 |
|---|---|
| `nginx.conf` | Nginx 主配置文件 |
| `conf.d/*.conf` | Nginx 的站点或服务配置 |
| `default.conf` | 默认站点配置，Docker 里常见 |

为什么前端项目会出现 Nginx？

因为很多前端项目正式发布时，会先执行：

```bash
npm run build
```

生成一堆静态文件。然后 Nginx 负责把这些文件提供给浏览器访问。

为什么后端项目会出现 Nginx？

因为后端服务运行在 `localhost:8000`，用户访问的是：

```text
https://example.com
```

Nginx 会把用户请求转发给后端服务。

你看到 Nginx 配置时，先看这几个词：

| 配置词 | 人话解释 |
|---|---|
| `listen` | Nginx 监听哪个端口 |
| `server_name` | 这个配置对应哪个域名 |
| `location` | 哪些路径走这段规则 |
| `proxy_pass` | 把请求转发到哪里 |
| `root` | 静态文件放在哪里 |
| `index` | 默认打开哪个文件 |

新手不需要一开始会写 Nginx 配置。先做到：

1. 看到 `nginx.conf`，知道它属于部署/服务器配置。
2. 看到 `proxy_pass`，知道它在转发请求。
3. 看到 `listen 80` 或 `listen 443`，知道它在监听网页访问端口。
4. 不要把 Nginx 问题和前端代码问题混在一起。

---

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

## 14. 看到命令时怎么判断它属于哪类

| 命令 | 属于哪类 | 人话解释 |
|---|---|---|
| `git status` | Git | 看修改状态 |
| `git diff` | Git | 看改了什么 |
| `git pull` | Git | 拉取远程最新 |
| `git push` | Git | 上传本地提交 |
| `node -v` | Node | 看 Node 版本 |
| `npm -v` | npm | 看 npm 版本 |
| `nvm use` | Node 版本管理 | 切换 Node 版本 |
| `npm install` | Node 依赖 | 安装依赖 |
| `npm run dev` | Node 启动 | 启动开发服务 |
| `npm run build` | Node 构建 | 生成正式版本 |
| `python --version` | Python | 看 Python 版本 |
| `pip install ...` | Python 依赖 | 安装 Python 包 |
| `uv sync` | Python 依赖 | 按项目依赖清单同步本机 Python 环境 |
| `pytest` | Python 测试 | 跑测试 |
| `docker ps` | Docker | 看容器 |
| `docker compose up` | Docker | 启动多个服务 |
| `curl ...` | 网络/API | 请求接口 |

---

## 15. 看到陌生文件或目录时怎么归类

你不是要背所有文件名，而是要把它归入一个稳定职责。

### 15.1 先按名字归类

| 名字里出现 | 归入哪个部分 | 理解方式 |
|---|---|---|
| `readme`, `docs`, `guide`, `wiki` | 说明区 | 给人看的说明 |
| `src`, `app`, `lib`, `core` | 源代码区 | 实现功能 |
| `api`, `server`, `backend`, `routes` | 后端/API 区 | 处理请求、提供接口 |
| `components`, `pages`, `views`, `web`, `frontend` | 前端界面区 | 展示页面和交互 |
| `config`, `.rc`, `.json`, `.toml`, `.yml` | 配置区 | 给工具读的规则 |
| `test`, `tests`, `spec`, `fixtures` | 测试区 | 验证功能和准备测试数据 |
| `scripts`, `bin`, `tools` | 脚本区 | 自动化命令和小工具 |
| `data`, `dataset`, `examples`, `samples` | 数据/示例区 | 样例、演示、测试材料 |
| `docker`, `nginx`, `deploy`, `k8s` | 部署区 | 容器、服务器、上线运行 |
| `.github`, `workflow`, `actions` | 自动化区 | GitHub 自动测试、构建、发布 |
| `prompt`, `agent`, `mcp`, `rag`, `knowledge` | AI/Agent 区 | 提示词、工具调用、知识库 |
| `sdk`, `client`, `lib`, `module`, `package` | 开发包/可复用代码区 | 给别的程序或项目调用的代码 |
| `plugin`, `extension`, `addons` | 扩展区 | 给已有工具或平台增加功能 |
| `schema`, `types`, `models` | 结构定义区 | 规定数据结构、字段、类型 |
| `template`, `boilerplate`, `starter` | 模板区 | 给新项目复制使用的基础结构 |
| `cli`, `command`, `bin` | 命令行工具区 | 提供可以在终端里执行的命令 |
| `dist`, `build`, `output`, `artifacts` | 构建产物区 | 放工具生成出来的结果文件 |
| `cache`, `tmp`, `temp` | 缓存/临时区 | 放加速用或临时生成的数据 |
| `auth`, `token`, `key`, `secret`, `credentials` | 权限/密钥区 | 登录、权限、访问凭证相关内容 |
| `license`, `changelog`, `release` | 发布/规则说明区 | 授权、版本、更新记录 |
| `sync`, `import`, `export`, `fetch`, `pull`, `push` | 数据流/同步动作 | 表示内容在两个地方之间移动或保持一致 |

### 15.2 再按后缀归类

| 后缀 | 归入哪个部分 | 理解方式 |
|---|---|---|
| `.md` | 说明区 | Markdown 文档 |
| `.js`, `.jsx`, `.mjs`, `.cjs`, `.ts`, `.tsx` | JavaScript/TypeScript 代码区 | 前端、Node.js、工具代码 |
| `.py` | Python 代码区 | Python 程序、脚本、服务 |
| `.ipynb` | Jupyter 笔记本区 | 数据分析、AI 实验、教学演示 |
| `.json` | 配置/数据区 | 严格结构化配置或数据 |
| `.toml` | 配置区 | Python、Rust 等项目配置 |
| `.yml`, `.yaml` | 配置/部署区 | Docker、GitHub Actions、环境配置 |
| `.env` | 环境变量区 | 端口、密钥、数据库地址 |
| `.lock` | 依赖锁定区 | 固定依赖版本 |
| `.sql` | 数据库区 | 数据表、查询、迁移脚本 |
| `.csv` | 数据/表格区 | 用逗号分隔列的表格数据 |
| `.hbs` | 模板区 | Handlebars 模板，用占位符生成文本、HTML、邮件或代码 |
| `.sh`, `.ps1`, `.bat` | 脚本区 | Linux、PowerShell、Windows 命令脚本 |
| `.gitkeep` | 占位/结构维护 | 让 Git 保存空目录 |
| `.test.mjs`, `.spec.ts`, `.env.example` | 多段后缀 | 最右边看格式，中间段看用途 |

### 15.3 最后按内容归类

文件名看不懂时，看内容长什么样。

| 内容特征 | 归入哪个部分 |
|---|---|
| 一行一个 `KEY=VALUE` | 环境变量区 |
| 很多 `{}`、`[]`、`"key": "value"` | JSON 配置/数据区 |
| 很多 `[section]` 和 `key = value` | TOML 配置区 |
| 一行一个 `key: value`，或者靠缩进表示层级 | YAML 配置/部署区 |
| 很多 `import`、`function`、`class` | 代码区 |
| 很多 `CREATE TABLE`、`SELECT`、`INSERT` | 数据库区 |
| 很多 `docker`, `image`, `services`, `ports` | Docker 部署区 |
| 很多 `name`, `on`, `jobs`, `steps` | GitHub Actions 自动化区 |
| 很多标题、段落、列表 | 文档说明区 |

归类后的目标不是立刻看懂每一行，而是先知道：

> 这个东西属于哪一部分，它负责什么，我需要用哪套知识去理解它。

### 15.4 再看 VS Code 给你的状态提示

VS Code 不只显示名字，还会用颜色、图标、字母提示状态。

在 VS Code 的 Explorer 里，颜色和右侧字母主要是 Git 状态提示。颜色由 VS Code 主题决定，字母比颜色更可靠。最可靠的判断方式是运行 `git status`。

| 显示 | 常见含义 | 说明 |
|---|---|---|
| 绿色 | 新增文件 | Git 还没正式记录，或者刚加入暂存区 |
| `U` | Untracked | 新文件，Git 还没有跟踪 |
| `A` | Added | 新文件，已经 `git add`，等待提交 |
| 橙色 / 黄色 | 已修改 | 原来就存在的文件被改过 |
| `M` | Modified | 文件内容被修改，尚未提交 |
| 红色 | 删除或冲突 | 文件被删除，或者有 Git 冲突 |
| `D` | Deleted | 文件被删除，尚未提交 |
| `R` | Renamed | 文件被重命名 |
| `C` | Conflict | 合并、拉取或切换分支时产生冲突 |
| 灰色 / 变淡 | 被忽略、排除、生成，或状态特殊 | 查 `.gitignore` 或 VS Code exclude 设置 |
| 左侧是文件夹图标 | 这是目录 | 打开后继续看里面的部件 |
| 左侧是文件图标 | 这是文件 | 根据后缀和内容判断用途 |
| 名字最后是 `/` | 这是文件夹 | `package/` 和 `package.json` 不是同一个东西 |

你现在最常见会遇到的是这几个：

| 标记 | 最短解释 | 人话 |
|---|---|---|
| `U` | 新文件，Git 还不知道它 | 这是新冒出来的文件，还没加入版本管理 |
| `M` | 旧文件被修改了 | 这是原来的文件，被你或工具改过 |
| `D` | 文件被删除了 | 原来的文件被删了 |
| `A` | 新文件已经加入 Git 暂存区 | 这个新文件准备进入下一次提交 |
| `C` | 有冲突，需要手动解决 | Git 不知道该保留哪一版，需要你处理冲突 |

每次不确定时，直接在终端运行：

```bash
git status
```

它会用文字告诉你每个文件到底是什么状态，比单看颜色更可靠。

通用判断顺序：

1. 先看它是文件还是文件夹。
2. 再看颜色和 Git 状态。
3. 再看名字和后缀。
4. 最后看里面的内容。

这样遇到 `package/`、`package.json`、`.env`、`node_modules/`、`user.test.mjs` 时，你都能用同一套规则判断。

---

## 16. 如何找入口文件

入口文件就是项目开始运行的地方。

### 16.1 Node.js 项目

入口信息写在 `package.json`：

- `scripts.dev`
- `scripts.start`
- `main`
- `bin`

常见入口：

- `src/index.ts`
- `src/main.ts`
- `server.ts`
- `app.ts`
- `pages`
- `app`

### 16.2 Python 项目

常见入口：

- `main.py`
- `app.py`
- `server.py`
- `manage.py`
- `src/...`

README 里也会写：

```bash
python main.py
uvicorn app:app --reload
```

### 16.3 Docker 项目

看：

- `Dockerfile`
- `docker-compose.yml`

里面会写启动命令。

---

## 17. 遇到报错时先判断层级

不要一看到红字就慌。

先问：

> 这个报错属于哪一层？

| 现象 | 所属层级 |
|---|---|
| `command not found: node` | Node 没装或环境没加载 |
| `npm install` 失败 | npm、网络、依赖、权限 |
| `No package.json found` | 你不在项目根目录 |
| `Module not found` | 依赖没装或路径错 |
| `port already in use` | 端口被占用 |
| `API 401` | API Key 或登录权限 |
| `API 404` | 地址或资源 ID 错 |
| `API 500` | 后端服务内部错误 |
| `Cannot connect to localhost` | 服务没启动、端口错、环境隔离 |
| `Docker daemon is not running` | Docker 没启动 |
| `merge conflict` | Git 合并冲突 |
| `push rejected` | 远程有新提交或没有权限 |

### 17.1 报错处理四步

1. 看报错第一行和最后一行。
2. 判断属于哪一层。
3. 回到 README 确认前置步骤有没有漏。
4. 再让 Codex 帮你解释。

### 17.2 问 Codex 的报错模板

```text
请解释下面报错。请先判断它属于哪一层：
Git / Node/npm/nvm / Python / Docker / 网络代理 / API Key / 数据库 / 代码逻辑。

请按这个格式回答：
1. 报错核心意思；
2. 主要原因；
3. 第一条检查命令；
4. 不建议我乱做什么；
5. 如果第一步无效，再做什么。

报错内容如下：
……
```

---

## 18. 让 Codex 帮你读仓库

### 18.1 先解释，不改代码

```text
请先不要修改任何文件。

请阅读这个仓库的 README、主要配置文件和目录结构，用零基础能听懂的方式说明：
1. 这个仓库是做什么的；
2. 它属于前端、后端、AI、MCP、文档、数据库、部署还是工具；
3. 它主要用什么语言和运行环境；
4. 它怎么安装、启动、测试；
5. 每类文件分别负责什么；
6. 哪些内容现在可以先不用看。
```

### 18.2 小范围修改

```text
请只修改与下面目标直接相关的文件，不要顺手重构无关代码。

目标：
……

已知问题：
……

期望行为：
……

不要修改：
……

修改完成后，请告诉我：
1. 修改了哪些文件；
2. 每个文件为什么要改；
3. 我应该怎么验证；
4. 风险点是什么。
```

### 18.3 检查修改

```text
请检查当前修改。

重点看：
1. 有没有无关文件被改；
2. 有没有临时文件、密钥、配置被误提交；
3. 是否会破坏原有功能；
4. 是否需要测试；
5. README 或注释是否需要同步更新。
```

---

## 19. 你该如何记录一个仓库

每看一个仓库，复制下面模板填一遍。

```text
仓库名：
仓库地址：

一句话说明：

项目类型：
[ ] 前端
[ ] 后端
[ ] Python/AI
[ ] MCP
[ ] 文档
[ ] 数据库
[ ] Docker/部署
[ ] CLI 工具
[ ] SDK
[ ] 其他：

主要语言：

关键文件：
- README：
- package.json / pyproject.toml：
- Dockerfile / docker-compose：
- .env.example：
- docs：

怎么安装：

怎么启动：

怎么测试：

我现在最该看懂的 3 个文件：
1.
2.
3.

暂时不用看的内容：

卡住的问题：

需要请 Codex 帮忙的问题：
```

---

## 20. 一周入门学习路线

### 第 1 天：只学 GitHub 页面

目标：

- 知道 README、Issues、PR、Actions、Releases 在哪里。
- 能说出仓库是做什么的。

练习：

- 找 3 个仓库，只读首页和 README。
- 每个仓库写一句话说明。

### 第 2 天：学常见文件

目标：

- 认识 `package.json`、`pyproject.toml`、`Dockerfile`、`.env.example`。

练习：

- 打开 3 个仓库根目录。
- 判断它们分别是什么类型。

### 第 3 天：学 Git 基础

目标：

- 知道分支、提交、PR 是什么。
- 会看 `git status` 和 `git diff` 的意思。

练习：

- 让 Codex 解释当前仓库的修改状态。

### 第 4 天：学 Node/npm

目标：

- 知道 `npm install`、`npm run dev`、`npm run build` 的区别。
- 会读 `package.json` 的 `scripts`。

练习：

- 找一个 Node 项目，只看 `scripts`，解释每条命令。

### 第 5 天：学 Python 项目

目标：

- 知道 `requirements.txt`、`pyproject.toml`、`.venv`、`uv sync`。

练习：

- 找一个 Python 项目，判断怎么安装依赖、怎么启动。

### 第 6 天：学 API、数据库、Docker

目标：

- 知道前端、后端、数据库怎么配合。
- 知道 Docker 是打包运行环境。

练习：

- 找一个有 `docker-compose.yml` 的项目，看看它启动了哪些服务。

### 第 7 天：学 AI / MCP / RAG

目标：

- 知道 AI 项目常见目录。
- 知道 MCP 是 AI 调工具的协议。
- 知道 RAG 是先检索资料再回答。

练习：

- 找一个 AI 或 MCP 仓库，判断它给人用、给 AI 用，还是给程序调用。

---

## 21. 最重要的安全原则

1. 不要随便提交 `.env`、密钥、密码、token。
2. 不要直接在 `main` 分支乱改。
3. 不要看到报错就乱删文件夹。
4. 不要手动改 `node_modules`。
5. 不要手动乱改锁文件，除非你知道为什么。
6. 不要把 README 里的命令跨项目乱用。
7. 不要把全局配置当成项目配置乱改，比如全局 `.npmrc`。
8. 让 Codex 改代码前，先确认目标和范围。
9. Codex 改完后，一定看改了哪些文件。
10. 不懂时先让 Codex 解释，不要马上让它大改。

---

## 22. 你最终要练出的能力

你现在不需要追求“会写很多代码”。

你先练这 5 种能力：

1. 看见仓库，知道它是什么类型。
2. 看见文件，知道它负责什么。
3. 看见命令，知道它属于安装、启动、测试、构建还是部署。
4. 看见报错，知道先判断哪一层。
5. 让 Codex 帮忙时，能说清楚目标、范围、验证方式。

真正的入门不是背术语，而是建立技术地图感：

> 这个东西属于哪一层？它和谁有关？它应该归入说明区、配置区、代码区、命令区、日志区，还是部署区？

当你能这样问问题时，你已经开始看懂仓库了。
