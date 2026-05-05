# 代码索引

## 快速查找表
> 新对话时只读这部分。约 60 行。

### 按功能分类
| 功能 | 文件路径 | 一句话说明 | 风险 |
|------|---------|-----------|------|
| 用户登录 | frontend/src/api/auth.ts | 登录注册API | 高 |
| API密钥管理 | frontend/src/api/keys.ts | 密钥CRUD | 高 |
| 渠道监控 | frontend/src/api/channelMonitor.ts | 渠道状态监控 | 中 |
| 订阅管理 | frontend/src/api/subscriptions.ts | 订阅套餐 | 中 |
| 支付功能 | frontend/src/api/payment.ts | 支付相关 | 高 |
| 首页 | frontend/src/views/HomeView.vue | 首页 | 低 |
| 密钥使用统计 | frontend/src/views/KeyUsageView.vue | 密钥使用报表 | 低 |
| 管理后台 | frontend/src/views/admin/ | 管理面板 | 高 |
| 用户设置 | frontend/src/views/user/ | 用户设置页 | 中 |
| 认证 | backend/internal/handler/auth_handler.go | 登录认证逻辑 | 高 |
| 网关代理 | backend/internal/handler/gateway_handler.go | 核心代理逻辑 | 高 |
| 支付处理 | backend/internal/handler/payment_handler.go | 支付回调 | 高 |
| 渠道管理 | backend/internal/handler/channel_handler.go | 渠道配置 | 中 |
| 数据库模型 | backend/ent/ | ent ORM模型定义 | 高 |

---

## 详细索引

### 配置文件
### frontend/vite.config.ts
- 作用：Vite构建配置
- 关键配置项：代理、构建输出路径
- 修改风险：低

### frontend/package.json
- 作用：前端依赖和脚本
- 关键配置项：dev/build/test脚本
- 修改风险：低

### backend/go.mod
- 作用：Go模块定义
- 关键配置项：module名、Go版本、依赖
- 修改风险：中

### backend/ent/schema/*.go
- 作用：数据库ORM模型定义
- 关键配置项：实体字段、关系
- 修改风险：高

---

### API/路由
### frontend/src/api/keys.ts
- 作用：API密钥管理
- 接口：
  - GET /api/keys → 获取密钥列表
  - POST /api/keys → 创建密钥
  - DELETE /api/keys/:id → 删除密钥
- 修改风险：高

### frontend/src/api/channels.ts
- 作用：渠道管理
- 接口：
  - GET /api/channels → 获取渠道列表
  - POST /api/channels → 创建渠道
  - PUT /api/channels/:id → 更新渠道
- 修改风险：中

### frontend/src/router/index.ts
- 作用：前端路由配置
- 路由：
  - / → HomeView
  - /keys → KeyUsageView
  - /admin/* → 管理后台
- 修改风险：中

---

### 数据模型
### backend/ent/schema/user.go
- 模型名：User
- 字段：id, email, password, created_at, updated_at
- 关联：HasMany Keys, HasMany Subscriptions
- 修改风险：高

### backend/ent/schema/api_key.go
- 模型名：ApiKey
- 字段：id, key, user_id, name, quota, used
- 关联：BelongsTo User
- 修改风险：高

---

### 页面/组件
### frontend/src/views/HomeView.vue
- 作用：首页
- 路由：/
- 调用API：auth.ts, keys.ts

### frontend/src/views/KeyUsageView.vue
- 作用：密钥使用统计
- 路由：/keys
- 调用API：keys.ts, usage.ts

### frontend/src/views/admin/Dashboard.vue
- 作用：管理后台仪表盘
- 路由：/admin
- 调用API：channels.ts, payment.ts

---

### 工具/公共
### frontend/src/utils/*.ts
- 作用：工具函数
- 导出函数：formatDate, formatCurrency, validateEmail
- 修改风险：中

### backend/internal/pkg/*.go
- 作用：公共库
- 导出函数：各种工具函数
- 修改风险：中