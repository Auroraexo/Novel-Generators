# Novel Generator

基于 AI 的网文短篇小说生成器。项目已拆分为独立前后端仓库：

| 仓库 | 说明 |
|------|------|
| [novel-generator-backend](https://github.com/Auroraexo/novel-generator-backend) | NestJS API、Prisma、BullMQ、LLM |
| [novel-generator-frontend](https://github.com/Auroraexo/novel-generator-frontend) | Next.js Web 界面 |

本仓库（`Novel-Generators`）为早期 monorepo，后续开发请在上述两个仓库中进行。

## 本地开发

```bash
# 后端 — 默认 http://localhost:3001
git clone https://github.com/Auroraexo/novel-generator-backend.git
cd novel-generator-backend
npm install && cp .env.example .env
npx prisma migrate dev && npm run start:dev

# 前端 — 默认 http://localhost:3000
git clone https://github.com/Auroraexo/novel-generator-frontend.git
cd novel-generator-frontend
npm install && cp .env.example .env.local
npm run dev
```

## License

MIT
