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
