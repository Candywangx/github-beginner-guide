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
