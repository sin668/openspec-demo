# 项目上下文 
## 目的 
音乐人演出排班管理系统（Gig Staffing Dashboard），帮助管理员安排音乐人的演出任务，让音乐人查看、接受或拒绝演出分配，并支持替换请求流程。 
## 技术栈
### 前端 
- React 18+ (TypeScript) 
- TailwindCSS (响应式/移动端友好) 
- React Router (路由) 
- React Query 或 SWR (数据获取) 
### 后端 
- Python 3.11+ 
- FastAPI (REST API) 
- SQLAlchemy (ORM) 
- Pydantic (数据验证) 
- Alembic (数据库迁移)
### 数据库 
- PostgreSQL 15+
### 基础设施 
- Docker + docker-compose (本地开发和部署) 
- Nginx (反向代理)
### 认证 
- JWT Token 认证 
- bcrypt 密码哈希 
- 邮件密码重置功能
## 项目约定 
### 编码规范
- 遵循 Clean Architecture 
- 使用 Domain-Driven Design 
- 所有核心逻辑需要单元测试 
- API 需要集成测试
### 代码风格
- 前端：ESLint + Prettier, 使用函数式组件和 Hooks 
- 后端：Black + isort + mypy, PEP 8 规范 
- 命名： 
  - 组件：PascalCase (如 `GigDashboard.tsx`) 
  - 函数/变量：camelCase (前端) / snake_case (后端) 
  - 常量：UPPER_SNAKE_CASE - API 端点：kebab-case (如 `/api/gig-assignments`)
### 架构模式 
- 前端：组件分层 (pages → components → hooks → utils) 
- 后端：分层架构 (routers → services → repositories → models) 
- RBAC 权限控制必须在后端强制执行，不仅仅是前端隐藏
### 测试策略 
- 前端：Jest + React Testing Library (组件单元测试) 
- 后端：pytest (API 集成测试)
- 覆盖率目标：核心业务逻辑 > 80%
### Git 工作流 
- 主分支：`main` (生产环境) 
- 功能分支：`feature/<描述>` 
- 修复分支：`fix/<描述>` 
- 提交信息格式：`type(scope): description` 
  - 类型：feat, fix, docs, refactor, test, chore
## 领域上下文 
### 核心概念 
- **Gig (演出)**: 一场演出活动，包含日期、地点、所需人员配置 
- **Assignment (分配)**: 将音乐人分配到演出的某个角色/位置 
- **Sub-out Request (替换请求)**: 音乐人请求找人替换自己的分配
### 用户角色 
- **Admin (管理员)**: 创建演出、分配音乐人、处理替换请求 
- **Musician (音乐人)**: 查看分配、接受/拒绝、请求替换
### 分配状态流转
pending → accepted  
→ declined  
→ sub_out_requested → (admin 处理) → reassigned / cancelled
## 重要约束 
### 技术约束 
- 移动端优先设计（音乐人主要使用手机） 
- 必须支持打印功能（演出当天工作表） 
- 数据库定期备份 - 错误日志记录
### 业务约束 
- 音乐人拒绝或请求替换时，管理员必须立即收到邮件通知 
- 所有状态变更需记录审计日志（谁、何时、改了什么） 
- V1 阶段通知方式：仅邮件（SMS/Push 留待后续版本）
## 外部依赖 
### 必需服务 
- SMTP 邮件服务 (发送通知和密码重置邮件) 
- PostgreSQL 数据库服务
### 可选服务 (V2+) 
- SMS 网关 (Twilio 等) 
- Push 通知服务
## 核心功能清单 
### V1 必须实现 
- [ ] 演出排班仪表板（按日期、地区、状态筛选） 
- [ ] 分配状态管理（接受/拒绝/待定/替换请求） 
- [ ] 可打印的演出工作表页面 
- [ ] 审计日志（基本的活动历史记录） 
- [ ] CSV 导出（演出和分配数据） 
- [ ] 邮件通知（拒绝/替换请求时通知管理员） 
- [ ] 安全认证 + 密码重置 
- [ ] RBAC 后端权限控制 
## 交付物 
- 可运行的生产环境 Web 应用 
- 源代码（交付至 GitHub 仓库） 
- 部署文档
