# Novel Generator

基于 AI 的网文短篇小说生成器，支持从灵感到完整小说的全流水线自动创作。

## 功能特性

- **AI 灵感生成** — 输入题材即可获取多条故事灵感
- **故事设定生成** — 自动生成人物、世界观、冲突、故事弧线
- **章纲生成** — 按网文节奏模板生成完整章纲，支持单章重新生成
- **正文生成** — 逐章生成正文，自动组装上下文保证长程一致性
- **摘要压缩** — 滚动压缩记忆，追踪伏笔和角色状态
- **字数校验** — 自动扩写/精简，确保每章字数达标
- **导出** — 支持 Markdown / TXT 全文导出

## 技术栈

| 层 | 选型 |
|---|---|
| 后端 | NestJS + TypeScript |
| 前端 | Next.js + Tailwind CSS |
| ORM | Prisma |
| 数据库 | PostgreSQL |
| 队列 | BullMQ (Redis) |
| LLM | OpenAI 兼容接口 |

## 项目结构

```
├── backend/          # NestJS 后端
│   ├── src/
│   │   ├── llm/         # LLM 调用封装（重试 + JSON 校验）
│   │   ├── prompt/      # Prompt 模板管理
│   │   ├── project/     # 项目 CRUD
│   │   ├── setting/     # 阶段一：故事设定 + 灵感生成
│   │   ├── outline/     # 阶段二：章纲生成
│   │   ├── chapter/     # 阶段三：正文生成
│   │   ├── summary/     # 阶段四：摘要压缩
│   │   ├── memory/      # 累积记忆管理
│   │   └── generation/  # 生成队列 + SSE 实时推送
│   └── prisma/          # 数据库 Schema
├── frontend/         # Next.js 前端
│   └── src/
│       ├── app/         # 页面（首页 + 项目详情）
│       ├── components/  # UI 组件
│       └── lib/         # API 客户端
└── prompt.md         # Prompt 设计文档
```

## 快速开始

### 环境要求

- Node.js >= 20
- PostgreSQL
- Redis

### 安装

```bash
# 后端
cd backend
npm install
cp .env.example .env  # 编辑 .env 配置数据库和 LLM

# 前端
cd frontend
npm install
```

### 配置 `.env`

```env
DATABASE_URL="postgresql://user:pass@host:5432/novel_generator"
REDIS_HOST=localhost
REDIS_PORT=6379
LLM_BASE_URL=https://your-api-gateway/v1
LLM_API_KEY=sk-xxx
LLM_MODEL=claude-sonnet-4-6
PORT=3001
```

### 运行

```bash
# 数据库迁移
cd backend
npx prisma migrate dev

# 启动后端
npm run start:dev

# 启动前端
cd frontend
npm run dev
```

访问 http://localhost:3000

## 使用流程

1. **新建项目** — 选择题材、子类型，AI 生成或手写灵感
2. **生成设定** — 一键生成完整故事设定，可手动编辑调整
3. **生成章纲** — 自动生成全本章纲，支持单章重新生成
4. **生成正文** — 逐章或批量生成，自动维护上下文一致性
5. **导出** — Markdown 或 TXT 格式导出完整小说

## 适用题材

- 言情 / 古言 / 总裁
- 悬疑 / 推理 / 惊悚
- 玄幻 / 仙侠 / 奇幻
- 都市 / 现代

## License

MIT
