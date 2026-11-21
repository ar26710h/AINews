# AINews · 新闻事件智能解析系统

软件课程设计项目（电信 2401 班）。B/S 架构：上传新闻 PDF → MinerU 解析 → Prompt 驱动大模型按范式抽取事件 → 时间线摘要 + 事件分析报告 → 可视化与导出。

## 技术栈

| 层 | 选型 |
|---|---|
| 前端 | Vue 3 + Vite + Element Plus + ECharts |
| 后端 | Python 3.11 + FastAPI + SQLAlchemy |
| 数据库 | MySQL 8.0（utf8mb4） |
| 缓存/队列 | Redis + RQ |
| 文档解析 | MinerU 2.7.6（pipeline 后端，CUDA 加速） |
| 大模型 | 阿里云百炼 · 通义千问（OpenAI 兼容接口） |
| 部署 | Nginx + Uvicorn |

## 目录结构（规划）

```
app/           后端应用
  api/         路由
  service/     业务逻辑
  model/       ORM 模型
  pipeline/    解析与抽取流水线
  worker/      异步任务
web/           前端工程
docs/          文档
```

## 本地开发

运行环境（Python/Node/MySQL/Redis/Nginx/MinerU）安装在仓库外的 `D:\DSHworkspace\env`，不入库。

```powershell
# 启动 MySQL / Redis / Nginx
powershell -NoProfile -ExecutionPolicy Bypass -File D:\DSHworkspace\env\start-all.ps1
# 激活环境变量
. D:\DSHworkspace\env\env.ps1
```

配置：复制 `.env.example` 为 `.env` 并填写 `DASHSCOPE_API_KEY`。

## 说明

- `.env`、`env/`、`data/` 均已在 `.gitignore` 中排除，请勿提交密钥与运行数据。
- 课程设计进度：第 11 周完成环境搭建与方案论证，第 13 周起进入编码。
