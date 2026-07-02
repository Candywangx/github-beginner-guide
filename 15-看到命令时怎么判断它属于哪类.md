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
