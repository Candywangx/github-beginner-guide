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
