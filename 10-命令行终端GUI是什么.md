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
