# 项目档案

## 基本信息
- 项目名称：Sub2API
- 项目类型：API代理服务 / Web应用
- 记录日期：2026-05-04
- 源码路径：E:\GitHub\sub2api

## 来源关系
- 原作者：Wei-Shaw（https://github.com/Wei-Shaw/sub2api）
- 亮爷 fork：https://github.com/nstl250619-ctrl/sub2api
- 亮爷包装项目：greenpool（https://github.com/nstl250619-ctrl/greenpool）

## 技术栈
- 前端：Vue 3 + TypeScript + Vite + TailwindCSS + Pinia
- 后端：Go (Gin框架) + ent ORM
- 数据库：PostgreSQL + Redis
- 其他：Docker, Nginx

## 启动与测试
- 前端开发：cd frontend && pnpm dev
- 前端构建：cd frontend && pnpm build
- 后端编译：cd backend && go build ./cmd/server
- 测试命令：cd frontend && pnpm test（或后端 go test）

## 目录结构
```
E:\GitHub\sub2api\
├── .github/          # GitHub配置
├── assets/           # 静态资源
├── backend/          # Go后端
│   ├── cmd/          # 入口命令（server, jwtgen）
│   ├── ent/          # ent ORM模型
│   ├── internal/      # 内部业务逻辑
│   ├── migrations/   # 数据库迁移
│   └── resources/    # 资源文件
├── deploy/           # 部署配置
├── docs/             # 文档
├── frontend/         # Vue前端
│   ├── public/       # 公共资源
│   └── src/          # 源代码
├── tools/            # 工具脚本
├── Dockerfile
├── Makefile
└── go.mod / package.json
```

## 环境变量（需用户提供）
- 后端：DATABASE_URL, REDIS_ADDR, JWT_SECRET 等
- 前端：VITE_API_BASE_URL 等

## 部署方式
- 手动SSH到服务器，自己执行命令
- Docker容器
- 原项目使用 Makefile 构建

## API接口（待索引阶段补充）
（暂未索引）

## 版本信息
- 当前版本：0.1.121（从git log获取）
- 最新commit：48912014 chore: sync VERSION to 0.1.121 [skip ci]