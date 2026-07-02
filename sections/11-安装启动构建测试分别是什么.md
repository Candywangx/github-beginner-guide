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
