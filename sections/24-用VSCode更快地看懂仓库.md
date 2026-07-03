## 23. 用 VS Code 更快地看懂仓库

VS Code 不只是写代码的地方，也可以当成“读仓库的地图”。

前面章节已经讲过：打开仓库后先看 README、配置文件、目录结构和入口文件；看到颜色、字母时要理解它们是 Git 或编辑器状态。这里不重复解释那些概念，只讲在 VS Code 里怎么更快做到这些事。

### 23.1 先用预览模式阅读 Markdown

很多仓库的说明都写在 Markdown 文件里，比如：

- `README.md`
- `docs/*.md`
- `CHANGELOG.md`
- `CONTRIBUTING.md`

如果直接打开 Markdown，你会看到 `#`、`-`、反引号、表格线。这些不是乱码，而是 Markdown 的写法。

在 VS Code 里可以使用预览模式，把 Markdown 显示成更像网页文章的样子。

常用方式：

| 想做什么 | Windows / Linux | macOS |
|---|---|---|
| 打开 Markdown 预览 | `Ctrl + Shift + V` | `Cmd + Shift + V` |
| 在旁边打开预览 | `Ctrl + K` 后按 `V` | `Cmd + K` 后按 `V` |
| 用命令面板搜索预览 | 搜索 `Open Preview` | 搜索 `Open Preview` |

新手读仓库时，建议这样用：

1. 左边打开 `README.md` 原文。
2. 右边打开 `Open Preview to the Side`。
3. 先读预览，不懂时再看原文里的 Markdown 写法。

这样你不会被 Markdown 符号干扰，更容易先看懂项目说明。

### 23.2 用分屏把说明和配置放在一起看

读仓库时，经常需要对照两个文件。

比如：

- 一边看 `README.md`，一边看 `package.json`。
- 一边看 `README.md` 的启动命令，一边看 `.env.example`。
- 一边看报错信息，一边看对应的配置文件。

你可以把一个文件拖到右侧，或者用 VS Code 的分屏功能，让两个文件并排显示。

常见对照方式：

| 左边看 | 右边看 | 用来判断什么 |
|---|---|---|
| `README.md` | `package.json` | README 里的命令是不是来自 `scripts` |
| `README.md` | `.env.example` | 启动前需要哪些环境变量 |
| `README.md` | `Dockerfile` | 项目是否主要用 Docker 启动 |
| 报错信息 | 相关配置文件 | 报错是不是环境、依赖或配置问题 |

分屏的重点不是同时看很多文件，而是把“说明”和“证据”放在一起。

### 23.3 用全局搜索找入口、命令和报错

新手读仓库时，不要只靠一层层点文件夹。全局搜索通常更快。

可以搜索这些关键词：

| 想找什么 | 可以搜什么 |
|---|---|
| 启动命令 | `dev`, `start`, `serve`, `run` |
| 构建命令 | `build`, `dist`, `out` |
| 测试命令 | `test`, `pytest`, `vitest`, `jest` |
| 入口文件 | `main`, `index`, `app`, `server` |
| 接口相关 | `api`, `route`, `controller`, `endpoint` |
| 登录相关 | `login`, `auth`, `token`, `session` |
| 配置相关 | `config`, `env`, `setting` |

搜索报错时，不要整段复制。先复制最有特点的一小段，比如：

```text
No package.json found
```

或者：

```text
Module not found
```

如果搜索结果太多，可以先排除这些目录：

- `node_modules`
- `dist`
- `build`
- `.next`
- `.venv`
- `venv`

这些目录通常是依赖、构建产物或本地环境，不是新手第一轮阅读重点。

### 23.4 用大纲快速看长文件结构

长文件不一定要从第一行读到最后一行。

VS Code 的 Outline（大纲）可以帮你看文件结构：

- Markdown 文件里，大纲会显示标题层级。
- 代码文件里，大纲会显示函数、类、变量等结构。
- 配置文件里，有时也能显示主要字段。

读长 Markdown 时，先看大纲里的标题，就像先看一本书的目录。

读长代码文件时，先看函数名和类名，不要急着看每一行实现。

### 23.5 用面包屑确认自己在哪个目录

VS Code 顶部通常会显示当前文件的位置，这叫 Breadcrumbs（面包屑路径）。

比如你看到：

```text
src > components > Button.tsx
```

就可以先这样理解：

> 这个文件在 `src` 源代码区，属于 `components` 组件目录，文件名是 `Button.tsx`。

再比如：

```text
.github > workflows > test.yml
```

可以先理解为：

> 这个文件在 GitHub 自动化区，用来描述某个自动检查或测试流程。

面包屑的作用是提醒你：不要只看文件名，还要看它在哪个目录里。

### 23.6 用 Git 改动视图看这次改了什么

VS Code 左侧的 Source Control 面板可以看到当前仓库有哪些文件被修改。

点开一个被修改的文件时，VS Code 会显示差异：

- 绿色通常表示新增内容。
- 红色通常表示删除内容。
- 左右或上下对比是在看“这次改动前后有什么不同”。

这里先记住一个原则：

> Source Control 面板不是用来理解整个仓库的，而是用来看“这次改了什么”。

文件旁边的 `M`、`U`、`A`、`D` 等状态字母，已经在第 15.4 节讲过。这里不用重复背，遇到不确定时回到那一节查。

### 23.7 少量必会快捷键

不用一开始背很多快捷键。先掌握和“读仓库”直接相关的这些就够了。

| 想做什么 | Windows / Linux | macOS |
|---|---|---|
| 快速打开文件 | `Ctrl + P` | `Cmd + P` |
| 全仓库搜索 | `Ctrl + Shift + F` | `Cmd + Shift + F` |
| 文件内搜索 | `Ctrl + F` | `Cmd + F` |
| 打开命令面板 | `Ctrl + Shift + P` | `Cmd + Shift + P` |
| 打开 Markdown 预览 | `Ctrl + Shift + V` | `Cmd + Shift + V` |
| 在旁边打开 Markdown 预览 | `Ctrl + K` 后按 `V` | `Cmd + K` 后按 `V` |
| 打开或关闭终端 | `` Ctrl + ` `` | `` Ctrl + ` `` |
| 切换侧边栏 | `Ctrl + B` | `Cmd + B` |
| 跳转到定义 | `F12` | `F12` |
| 返回上一个位置 | `Alt + ←` | `Ctrl + -` |
| 保存文件 | `Ctrl + S` | `Cmd + S` |

快捷键不是目标。真正的目标是：

> 用预览读说明，用分屏做对照，用搜索找线索，用大纲看结构，用 Git 视图看改动。

---
