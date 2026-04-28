
> 基于 OpenAI 官方文档及 2026 年社区经验总结

---

## 目录

1. [GPT-5.3-Codex 概述](https://zhuanlan.zhihu.com/p/2011904144760410797/edit#1-gpt-53-codex-%E6%A6%82%E8%BF%B0)
2. [环境搭建与基本配置](https://zhuanlan.zhihu.com/p/2011904144760410797/edit#2-%E7%8E%AF%E5%A2%83%E6%90%AD%E5%BB%BA%E4%B8%8E%E5%9F%BA%E6%9C%AC%E9%85%8D%E7%BD%AE)
3. [AGENTS.md 配置指南](https://zhuanlan.zhihu.com/p/2011904144760410797/edit#3-agentsmd-%E9%85%8D%E7%BD%AE%E6%8C%87%E5%8D%97)
4. [审批模式选择](https://zhuanlan.zhihu.com/p/2011904144760410797/edit#4-%E5%AE%A1%E6%89%B9%E6%A8%A1%E5%BC%8F%E9%80%89%E6%8B%A9)
5. [提示词工程](https://zhuanlan.zhihu.com/p/2011904144760410797/edit#5-%E6%8F%90%E7%A4%BA%E8%AF%8D%E5%B7%A5%E7%A8%8B)
6. [上下文窗口管理](https://zhuanlan.zhihu.com/p/2011904144760410797/edit#6-%E4%B8%8A%E4%B8%8B%E6%96%87%E7%AA%97%E5%8F%A3%E7%AE%A1%E7%90%86)
7. [Agent Skills（技能系统）](https://zhuanlan.zhihu.com/p/2011904144760410797/edit#7-agent-skills%E6%8A%80%E8%83%BD%E7%B3%BB%E7%BB%9F)
8. [多代理工作流](https://zhuanlan.zhihu.com/p/2011904144760410797/edit#8-%E5%A4%9A%E4%BB%A3%E7%90%86%E5%B7%A5%E4%BD%9C%E6%B5%81)
9. [CLI 与 Cloud 混合使用](https://zhuanlan.zhihu.com/p/2011904144760410797/edit#9-cli-%E4%B8%8E-cloud-%E6%B7%B7%E5%90%88%E4%BD%BF%E7%94%A8)
10. [安全与沙盒配置](https://zhuanlan.zhihu.com/p/2011904144760410797/edit#10-%E5%AE%89%E5%85%A8%E4%B8%8E%E6%B2%99%E7%9B%92%E9%85%8D%E7%BD%AE)
11. [代码审查与质量保障](https://zhuanlan.zhihu.com/p/2011904144760410797/edit#11-%E4%BB%A3%E7%A0%81%E5%AE%A1%E6%9F%A5%E4%B8%8E%E8%B4%A8%E9%87%8F%E4%BF%9D%E9%9A%9C)
12. [Git 工作流集成](https://zhuanlan.zhihu.com/p/2011904144760410797/edit#12-git-%E5%B7%A5%E4%BD%9C%E6%B5%81%E9%9B%86%E6%88%90)
13. [需求开发完整流程模板](https://zhuanlan.zhihu.com/p/2011904144760410797/edit#13-%E9%9C%80%E6%B1%82%E5%BC%80%E5%8F%91%E5%AE%8C%E6%95%B4%E6%B5%81%E7%A8%8B%E6%A8%A1%E6%9D%BF)
14. [常见反模式与避坑指南](https://zhuanlan.zhihu.com/p/2011904144760410797/edit#14-%E5%B8%B8%E8%A7%81%E5%8F%8D%E6%A8%A1%E5%BC%8F%E4%B8%8E%E9%81%BF%E5%9D%91%E6%8C%87%E5%8D%97)
15. [与其他工具对比参考](https://zhuanlan.zhihu.com/p/2011904144760410797/edit#15-%E4%B8%8E%E5%85%B6%E4%BB%96%E5%B7%A5%E5%85%B7%E5%AF%B9%E6%AF%94%E5%8F%82%E8%80%83)
16. [参考资料](https://zhuanlan.zhihu.com/p/2011904144760410797/edit#16-%E5%8F%82%E8%80%83%E8%B5%84%E6%96%99)

---

## 1. GPT-5.3-Codex 概述

### 1.1 什么是 GPT-5.3-Codex

GPT-5.3-Codex 于 **2026 年 2 月 5 日**发布，是 OpenAI 迄今最强大的智能编码代理模型。 它融合了 GPT-5.2-Codex 的前沿编程能力与 GPT-5.2 的推理和专业知识， 从”能写代码和审查代码”的代理进化为”几乎能完成开发者和专业人士在电脑上做的一切”的通用代理。

### 1.2 核心能力

|能力|说明|
|---|---|
|全生命周期覆盖|调试、部署、监控、编写 PRD、文案编辑、用户研究、测试、指标分析|
|实时交互|工作过程中可随时介入引导，不会丢失上下文|
|深度 Diff|提供推理透明性，展示每个变更的”为什么”而非仅呈现最终结果|
|更快更省|比 GPT-5.2-Codex 快 25%，使用更少的 token 完成同等任务|
|多平台可用|Codex App、CLI、IDE 扩展、Web 全平台可用|

### 1.3 基准测试表现

|基准|得分|说明|
|---|---|---|
|SWE-Bench Pro|行业最高|真实软件工程任务|
|Terminal-Bench 2.0|77.3%|终端和工具使用任务|
|[OSWorld-Verified](https://zhida.zhihu.com/search?content_id=270874011&content_type=Article&match_order=1&q=OSWorld-Verified&zd_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJ6aGlkYV9zZXJ2ZXIiLCJleHAiOjE3NzQ0ODk0NjEsInEiOiJPU1dvcmxkLVZlcmlmaWVkIiwiemhpZGFfc291cmNlIjoiZW50aXR5IiwiY29udGVudF9pZCI6MjcwODc0MDExLCJjb250ZW50X3R5cGUiOiJBcnRpY2xlIiwibWF0Y2hfb3JkZXIiOjEsInpkX3Rva2VuIjpudWxsfQ.jmjquuz_CDXs4ZQ3Urzm_XsMtyXEuZKRnTEXgPiNSwA&zhida_source=entity)|64.7%|操作系统级操作任务|
|[网络安全 CTF](https://zhida.zhihu.com/search?content_id=270874011&content_type=Article&match_order=1&q=%E7%BD%91%E7%BB%9C%E5%AE%89%E5%85%A8+CTF&zd_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJ6aGlkYV9zZXJ2ZXIiLCJleHAiOjE3NzQ0ODk0NjEsInEiOiLnvZHnu5zlronlhaggQ1RGIiwiemhpZGFfc291cmNlIjoiZW50aXR5IiwiY29udGVudF9pZCI6MjcwODc0MDExLCJjb250ZW50X3R5cGUiOiJBcnRpY2xlIiwibWF0Y2hfb3JkZXIiOjEsInpkX3Rva2VuIjpudWxsfQ.aFIgdZCaQzTyNU_C0d_0MaWB9Ld9o82BzRfLHKtGLbY&zhida_source=entity)|77.6%|安全攻防能力|

### 1.4 定价（API）

|类型|价格|
|---|---|
|输入|3.50 / 百万 token \|  <br>\| 输出 \| 28.00 / 百万 token|

> 对比：[Claude Opus 4.6](https://zhida.zhihu.com/search?content_id=270874011&content_type=Article&match_order=1&q=Claude+Opus+4.6&zd_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJ6aGlkYV9zZXJ2ZXIiLCJleHAiOjE3NzQ0ODk0NjEsInEiOiJDbGF1ZGUgT3B1cyA0LjYiLCJ6aGlkYV9zb3VyY2UiOiJlbnRpdHkiLCJjb250ZW50X2lkIjoyNzA4NzQwMTEsImNvbnRlbnRfdHlwZSI6IkFydGljbGUiLCJtYXRjaF9vcmRlciI6MSwiemRfdG9rZW4iOm51bGx9.WJN6ZHaR-FSras9GRlxcq3lNGnQts7kbXd1FuWkL4lU&zhida_source=entity) 为 75，[Gemini 3.1 Pro](https://zhida.zhihu.com/search?content_id=270874011&content_type=Article&match_order=1&q=Gemini+3.1+Pro&zd_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJ6aGlkYV9zZXJ2ZXIiLCJleHAiOjE3NzQ0ODk0NjEsInEiOiJHZW1pbmkgMy4xIFBybyIsInpoaWRhX3NvdXJjZSI6ImVudGl0eSIsImNvbnRlbnRfaWQiOjI3MDg3NDAxMSwiY29udGVudF90eXBlIjoiQXJ0aWNsZSIsIm1hdGNoX29yZGVyIjoxLCJ6ZF90b2tlbiI6bnVsbH0.TI2fMJIBRceujdXyZiHLp8_yZLd2T1D4iioxzaxIlE0&zhida_source=entity) 为 12。

### 1.5 变体：[Codex-Spark](https://zhida.zhihu.com/search?content_id=270874011&content_type=Article&match_order=1&q=Codex-Spark&zd_token=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJ6aGlkYV9zZXJ2ZXIiLCJleHAiOjE3NzQ0ODk0NjEsInEiOiJDb2RleC1TcGFyayIsInpoaWRhX3NvdXJjZSI6ImVudGl0eSIsImNvbnRlbnRfaWQiOjI3MDg3NDAxMSwiY29udGVudF90eXBlIjoiQXJ0aWNsZSIsIm1hdGNoX29yZGVyIjoxLCJ6ZF90b2tlbiI6bnVsbH0.1irS_ao3kr33O-8B6-rPebmG38Qs2M1lDHLLWLsNJa4&zhida_source=entity)

GPT-5.3-Codex-Spark 是更小更快的变体，专为实时编码设计， 在超低延迟硬件上可达 **1000+ tokens/秒**，适合需要即时反馈的交互场景。

---

## 2. 环境搭建与基本配置

### 2.1 安装 Codex CLI

```text
# 使用 npm 全局安装（CLI 基于 Rust 构建，npm 仅作分发渠道）
npm install -g @openai/codex

# 验证安装
codex --version

# 设置 API Key
export OPENAI_API_KEY="sk-..."
```

### 2.2 基础配置文件

Codex 的配置文件位于 `~/.codex/config.toml`：

```text
# ~/.codex/config.toml

# 默认模型
model = "gpt-5.3-codex"

# 默认审批模式: "suggest" | "auto-edit" | "full-auto"
approval_mode = "suggest"

# AGENTS.md 最大读取字节数（默认 32KB）
project_doc_max_bytes = 32768

# 当目录中没有 AGENTS.md 时的备选文件名
project_doc_fallback_filenames = ["CLAUDE.md", "TEAM_GUIDE.md"]

# 实验性功能
[features]
child_agents_md = true
multi_agents = true
```

### 2.3 前置要求

```text
# 确保项目在 Git 版本控制下
git init  # 如果还不是 Git 仓库

# Codex 在非 Git 目录下会发出警告
# 始终在 Git 跟踪的目录中运行 Codex
```

---

## 3. AGENTS.md 配置指南

### 3.1 什么是 AGENTS.md

AGENTS.md 是 Codex 的项目指导文件，相当于”给 AI 代理看的 README”。 它已被 60,000+ 开源项目采用，由 Linux 基金会下的 Agentic AI Foundation 管理， 并且已成为跨平台标准——同一份 AGENTS.md 可在 Codex、Claude Code、 Cursor、GitHub Copilot 等 30+ 代理平台上通用。

### 3.2 文件发现与合并顺序

```text
Codex 检查每个目录的文件顺序：
  1. AGENTS.override.md  （最高优先级，用于临时覆盖）
  2. AGENTS.md            （标准项目指导）
  3. 备选文件名            （config.toml 中配置的 fallback）

合并规则：从项目根目录向下拼接，靠近当前工作目录的内容优先级更高。
```

### 3.3 配置示例

### 全局默认（`~/.codex/AGENTS.md`）

```text
## 工作约定
- 修改 JavaScript/TypeScript 文件后始终运行 `npm test`
- 优先使用 `pnpm` 安装依赖
- 添加新的生产依赖前请先确认
- 提交信息使用 Conventional Commits 格式
```

### 项目根目录（`AGENTS.md`）

```text
# MyApp 项目指南

## 项目概述
这是一个 B2B SaaS 项目管理平台，使用以下技术栈：
- 前端：React 18 + TypeScript + Tailwind CSS
- 后端：Node.js + Fastify + PostgreSQL
- 构建工具：Vite
- 包管理器：pnpm

## 常用命令
- 启动开发服务器：`pnpm dev`
- 运行全部测试：`pnpm test`
- 运行单个测试文件：`pnpm test -- path/to/test`
- 类型检查：`pnpm typecheck`
- Lint 检查：`pnpm lint`
- 构建生产版本：`pnpm build`

## 目录结构
- `src/components/` — 可复用 UI 组件
- `src/features/` — 按业务功能组织的模块
- `src/lib/` — 工具函数和 API 客户端
- `src/stores/` — 状态管理（Zustand）
- `src/types/` — 全局 TypeScript 类型定义
- `prisma/` — 数据库 Schema 和 Migration

## 代码风格
- 使用函数式组件和 React Hooks
- API 调用统一使用 `src/lib/api-client.ts` 的封装
- 样式使用 Tailwind CSS，不使用 CSS Modules
- 文件命名使用 kebab-case，组件命名使用 PascalCase
- 导出组件使用 named export，不使用 default export

## 测试规范
- 使用 Vitest + React Testing Library
- 新增组件必须有对应测试文件
- 测试遵循 AAA 模式（Arrange, Act, Assert）
- 测试文件放在 `__tests__/` 目录下

## 安全注意事项
- 绝不在代码中硬编码 API 密钥或密码
- 不要直接修改 `prisma/migrations/` 下的已有文件
- 认证和权限相关的修改必须运行完整测试套件
```

### 子目录覆盖（`services/payments/AGENTS.override.md`）

```text
# 支付服务特殊规则

- 所有变更必须经过人工审查
- 运行测试命令：`pnpm test:payments --coverage`
- 金额计算必须使用 Decimal.js，不要使用浮点数
- PCI DSS 合规要求：不记录任何卡号信息
```

### 3.4 AGENTS.md 编写原则

|原则|说明|
|---|---|
|像写给新同事|提交消息规范、安全注意事项、部署步骤——你会告诉新人的内容都写上|
|控制篇幅|默认限制 32KB，超出会被截断；保持简洁、聚焦|
|结构化组织|使用清晰的标题和列表，方便 Codex 快速定位相关内容|
|避免与 Linter 重复|格式化规则交给 ESLint/Prettier，AGENTS.md 聚焦于架构和流程|
|持续维护|项目演进时同步更新，过时的指导比没有指导更糟糕|

---

## 4. 审批模式选择

Codex CLI 提供三种审批模式，控制代理的自主程度：

### 4.1 三种模式对比

|模式|文件操作|Shell 命令|适用场景|
|---|---|---|---|
|Suggest（建议）|需确认|需确认|学习代码库、审查代码、安全敏感操作|
|Auto Edit（自动编辑）|自动执行|需确认|日常开发、重构、批量修改|
|Full Auto（全自动）|自动执行|自动执行|原型开发、修复构建、信任度高的场景|

### 4.2 推荐的渐进式信任策略

```text
阶段 1 — 新项目/新代码库
└── 使用 Suggest 模式，逐步了解 Codex 的行为模式

阶段 2 — 建立信任后
└── 切换到 Auto Edit，让 Codex 自由编辑文件
    但仍需确认 Shell 命令

阶段 3 — 高度信任的成熟项目
└── 在 Git 跟踪下使用 Full Auto
    确保有沙盒隔离和网络限制
```

### 4.3 使用方式

```text
# 启动时指定模式
codex --approval-mode auto-edit

# 或在交互中切换
# 输入 /mode 可以切换审批模式
```

> **安全提醒**：Full Auto 模式下 Codex 会自动禁用网络访问，并在沙盒环境中运行。

---

## 5. 提示词工程

### 5.1 核心原则

|原则|说明|
|---|---|
|说明意图而非步骤|告诉 Codex “为什么”要做，而不仅仅是”做什么”|
|提供验证标准|给出测试命令、预期输出或截图，让 Codex 自我验证|
|限定范围|明确指出需要修改的文件/目录/模块|
|引用参考|指向现有代码作为风格和模式的参考|
|避免输出规划|不要提示 Codex 输出执行计划或状态更新（官方建议）|

### 5.2 提示词模板

### 反面示例

```text
做一个用户管理页面
```

### 正面示例

```text
【业务背景】
我们的 SaaS 平台需要一个管理员用户管理页面。
管理员需要查看所有用户、搜索用户、禁用/启用账户。

【技术上下文】
- 项目使用 React + TypeScript + Tailwind CSS
- 现有的表格组件在 src/components/data-table.tsx
- API 客户端在 src/lib/api-client.ts
- 用户相关 API 端点：
  GET /api/admin/users（支持 ?search=&page=&limit= 参数）
  PATCH /api/admin/users/:id（修改用户状态）

【参考实现】
参考 src/features/products/product-list.tsx 的列表页面模式

【验收标准】
- 支持按邮箱和用户名搜索
- 分页展示，每页 20 条
- 每行有"禁用/启用"操作按钮，带确认弹窗
- 操作后显示 toast 通知
- 完成后运行 pnpm test 确保无回归
```

### 5.3 推理强度选择

|强度|适用场景|特点|
|---|---|---|
|medium|日常交互式编码|速度与智能的最佳平衡（推荐默认）|
|high|复杂功能实现、架构决策|更深入的推理，速度略慢|
|xhigh|最困难的任务、长时间自主工作|最强推理能力，成本最高|

### 5.4 图片输入

Codex 支持附加截图或设计稿作为提示的一部分：

```text
请参考附加的设计稿截图，实现这个用户资料页面。
保持与设计稿一致的间距、颜色和布局。
使用 Tailwind CSS 实现样式。

[附加截图]
```

### 5.5 长任务提示技巧

对于需要长时间自主运行的复杂任务（官方建议）：

1. **充分规划**：提示 Codex 在开始前将任务分解为子任务
2. **使用 TODO 工具**：让 Codex 通过 TODO 列表追踪工作流进度
3. **完整解决**：指示 Codex 在交还控制权前完成全部子任务
4. **每次工具调用后反思**：要求 Codex 在每次操作后确认完成度

---

## 6. 上下文窗口管理

### 6.1 为什么上下文管理很重要

上下文窗口保存了整个会话的所有消息、文件内容和命令输出。 随着窗口填满，会出现两个问题：

- **上下文污染**：有用信息被噪声中间输出淹没
- **上下文腐烂**：性能随着不相关细节的积累而下降

### 6.2 管理策略

|策略|操作|说明|
|---|---|---|
|一任务一会话|每个独立任务使用新会话|最有效的预防措施|
|压缩|/compact|生成压缩后的新上下文窗口，保留关键信息|
|会话恢复|codex resume|从本地存储的转录中恢复之前的会话|
|清理|新建会话|当纠错超过 2 次时，重新开始|

### 6.3 压缩（Compaction）

压缩是 Codex 支持多小时推理的关键机制：

```text
场景：实现一个复杂功能，预计需要很多轮对话

推荐流程：
1. 开始实现 → 完成核心逻辑
2. 运行 /compact → 压缩上下文
3. 继续实现 → 完成测试和边界处理
4. 运行 /compact → 再次压缩
5. 最终验证 → 完成

这样可以在不丢失关键上下文的情况下持续工作数小时。
```

---

## 7. Agent Skills（技能系统）

### 7.1 什么是 Skills

技能是打包了指令、资源和可选脚本的目录，让 Codex 可以可靠地遵循特定工作流。 技能系统已成为跨平台标准，同一技能可在 Codex、Claude Code、Cursor、 GitHub Copilot 等 30+ 平台上使用。

> **注意**：Custom Prompts 已被废弃，改用 Skills。

### 7.2 技能结构

```text
.codex/skills/
└── api-design/
    ├── SKILL.md           # 技能说明和指令（必需）
    ├── agents/
    │   └── openai.yaml    # UI 元数据和调用策略（可选）
    └── templates/          # 参考模板（可选）
        └── endpoint.ts
```

### 7.3 SKILL.md 示例

```text
<!-- .codex/skills/api-design/SKILL.md -->
---
name: API Design
description: 遵循项目 RESTful API 设计规范创建后端端点
---

# API 设计规范

## 端点约定
- GET /api/resources — 列表查询（支持分页、排序、过滤）
- GET /api/resources/:id — 单个查询
- POST /api/resources — 创建
- PUT /api/resources/:id — 全量更新
- PATCH /api/resources/:id — 部分更新
- DELETE /api/resources/:id — 删除

## 请求/响应格式
成功响应：{ "data": ..., "meta": { "page": 1, "total": 100 } }
错误响应：{ "error": { "code": "VALIDATION_ERROR", "message": "..." } }

## 实现步骤
1. 在 `src/routes/` 下创建路由文件
2. 在 `src/services/` 下创建业务逻辑
3. 在 `src/schemas/` 下定义 Zod 验证 Schema
4. 为每个端点编写集成测试
5. 运行 `pnpm test` 验证
```

### 7.4 技能调用方式

```text
# 显式调用（CLI 中）
/skills             # 列出可用技能
$ api-design        # 通过 $ 前缀引用技能

# 隐式调用
# Codex 在任务匹配技能描述时会自动加载
# 因此技能的 description 要写得清晰、边界明确

# 安装社区技能
$ skill-installer
```

### 7.5 技能编写原则

- **单一职责**：每个技能聚焦一个任务
- **指令优于脚本**：除非需要确定性行为，否则用指令代替脚本
- **显式输入输出**：写明期望的输入和输出格式
- **渐进披露**：Codex 只在需要时加载完整 SKILL.md，元数据先行

---

## 8. 多代理工作流

### 8.1 概述

多代理工作流允许 Codex 生成多个专门化代理并行工作， 然后收集结果统一响应。适用于高度并行的复杂任务。

### 8.2 启用方式

```text
# 在 CLI 中启用（实验性功能）
/experimental
# 选择启用 Multi-agents，然后重启 Codex
```

或在配置文件中：

```text
# ~/.codex/config.toml
[features]
multi_agents = true
```

### 8.3 代理角色配置

```text
# ~/.codex/config.toml 或 .codex/config.toml

[agents.reviewer]
description = "专注于代码审查，检查安全漏洞、性能问题和最佳实践"
config_file = ".codex/agents/reviewer.toml"

[agents.test-writer]
description = "专注于编写和维护测试用例"
config_file = ".codex/agents/test-writer.toml"

[agents.explorer]
description = "只读代理，专注于代码库探索和分析"
config_file = ".codex/agents/explorer.toml"
```

### 8.4 多代理使用模式

|模式|说明|适用场景|
|---|---|---|
|并行读取|多个代理同时探索代码库不同部分|代码库分析、测试分类|
|Writer/Reviewer|一个代理写代码，另一个代理审查|高质量代码交付|
|扇出(Fan-out)|从 CSV 或任务列表批量分发工作|批量迁移、多文件重构|
|监控(Monitor)|等待和轮询长时间运行的命令|CI/CD 状态检查、部署监控|

### 8.5 安全注意事项

- 子代理继承当前沙盒策略
- 子代理使用非交互式审批（不会弹出确认提示）
- 需要新权限的操作会失败并上报给父工作流
- 可以为特定角色覆盖沙盒配置（如设为只读模式）

### 8.6 MCP Server 编排

```text
# 将 Codex CLI 作为 MCP Server 运行
codex --mcp-server

# 暴露两个工具：
# codex()       — 开始新对话
# codex-reply() — 继续已有对话
# 其他 MCP 客户端可调用这些工具进行编排
```

---

## 9. CLI 与 Cloud 混合使用

### 9.1 推荐的混合策略

|场景|推荐使用|原因|
|---|---|---|
|快速迭代、即时反馈|CLI|本地执行，延迟低|
|跨仓库重构、完整测试|Cloud|隔离容器，不影响本地环境|
|原型开发、探索性编码|CLI (Full Auto)|快速试验|
|长时间运行的自主任务|Cloud|可后台运行，不占用本地终端|
|安全敏感操作|CLI (Suggest)|本地控制，逐步确认|

### 9.2 Cloud 任务的特点

- 在隔离容器中运行，默认无网络访问
- 提供完整的任务执行转录（Trace）
- 支持异步查看结果
- 适合团队协作场景

---

## 10. 安全与沙盒配置

### 10.1 安全架构

```text
┌─────────────────────────────┐
│         用户交互             │
├─────────────────────────────┤
│     审批模式（三级控制）      │ ← Suggest / Auto Edit / Full Auto
├─────────────────────────────┤
│     沙盒隔离层              │ ← 文件系统隔离 + 网络隔离
├─────────────────────────────┤
│     Git 版本控制            │ ← 所有变更可追溯、可回滚
└─────────────────────────────┘
```

### 10.2 沙盒最佳实践

|实践|说明|
|---|---|
|最小权限|沙盒只授予完成任务所需的最少命令和路径|
|隔离密钥|不要将 .env、凭证文件暴露给 Codex|
|审计转录|端到端审查任务执行记录|
|网络隔离|Full Auto 模式自动禁用网络，Cloud 默认无网络|

### 10.3 安全红线

- **手动审查**：认证、支付、数据变更相关代码
- **不提交**：`.env`、密钥、凭证等敏感文件
- **不执行**：`rm -rf`、`git push --force`、数据库删除等不可逆操作（除非明确要求）
- **版本控制**：所有变更在 Git 跟踪下进行，随时可回滚

---

## 11. 代码审查与质量保障

### 11.1 利用 Codex 进行代码审查

```text
# 在 CLI 中对当前变更进行代码审查
codex "review the current staged changes for security issues,
performance problems, and adherence to our coding standards"

# 使用独立代理审查（推荐，避免偏见）
# 写代码和审查代码使用不同的会话/代理
```

### 11.2 验证驱动开发

```text
最高杠杆实践：给 Codex 提供验证标准

✅ "完成后运行 pnpm test 确保所有测试通过"
✅ "参考 product-list.tsx 的实现模式来实现"
✅ "请审查你的代码，检查 XSS、注入等安全问题"
✅ "确保类型检查通过：pnpm typecheck"
```

### 11.3 Trace 审计

Codex 自动记录 Trace，捕获每个提示、工具调用和代理切换。 多代理任务完成后，可通过 Traces 面板检查执行时间线。

```text
评估 Codex 在你的代码库上的表现：
1. 从有确定性测试支持的限定任务开始
2. 要求 "从失败到通过" 的完整执行
3. 将每次变更保持在 PR 之后
4. 审查 Trace 中的每一步决策
```

---

## 12. Git 工作流集成

### 12.1 推荐流程

```text
# 1. 创建功能分支
git checkout -b feature/user-management

# 2. 启动 Codex
codex --approval-mode auto-edit

# 3. 描述需求，Codex 实现

# 4. 审查变更
git diff

# 5. 提交（让 Codex 生成规范的提交信息）
codex "commit the current changes with a conventional commit message"

# 6. 代码审查（用新会话）
codex "review the changes on this branch compared to main"

# 7. 创建 PR
codex "create a PR for this branch with a summary of all changes"
```

### 12.2 安全原则

- 始终在 Git 跟踪目录中工作
- 使用分支隔离功能开发
- 变更后先 `git diff` 审查，再提交
- 不要让 Codex 执行 `--force` 推送
- 利用 Git 的回滚能力作为安全网

---

## 13. 需求开发完整流程模板

```text
┌──────────────────────────────────────────────────────┐
│          Phase 1：准备（5 分钟）                       │
├──────────────────────────────────────────────────────┤
│ 1. 确保 AGENTS.md 已配置并反映当前项目状态              │
│ 2. 创建功能分支：git checkout -b feature/xxx          │
│ 3. 选择合适的审批模式（建议从 Auto Edit 开始）           │
│ 4. 准备好需求描述（包含业务背景和验收标准）               │
└──────────────────────┬───────────────────────────────┘
                       ▼
┌──────────────────────────────────────────────────────┐
│          Phase 2：需求分析与规划                       │
├──────────────────────────────────────────────────────┤
│ 1. 向 Codex 描述需求（使用结构化提示词）                 │
│ 2. 让 Codex 分解为子任务并确认实现方案                   │
│ 3. 审查方案，提出修改意见                               │
│ 4. 确认方案后进入实现阶段                               │
│                                                      │
│ 💡 推理强度设为 high，确保深入思考                       │
└──────────────────────┬───────────────────────────────┘
                       ▼
┌──────────────────────────────────────────────────────┐
│          Phase 3：分步实现                             │
├──────────────────────────────────────────────────────┤
│ 1. 按子任务逐步实现                                    │
│ 2. 每完成一个模块运行相关测试                            │
│ 3. 上下文变大时用 /compact 压缩                        │
│ 4. 每 2-3 轮检查一次代码质量                            │
│                                                      │
│ 💡 复杂任务可并行启动多个代理                            │
│ 💡 长时间任务可使用 Cloud 模式后台运行                    │
└──────────────────────┬───────────────────────────────┘
                       ▼
┌──────────────────────────────────────────────────────┐
│          Phase 4：测试与审查                           │
├──────────────────────────────────────────────────────┤
│ 1. 运行完整测试套件：pnpm test                         │
│ 2. 运行类型检查：pnpm typecheck                       │
│ 3. 打开新会话（或使用 Reviewer 代理）进行独立审查         │
│ 4. 人工审查安全敏感代码                                 │
│ 5. 审查 Trace 中的执行记录                             │
└──────────────────────┬───────────────────────────────┘
                       ▼
┌──────────────────────────────────────────────────────┐
│          Phase 5：提交与交付                           │
├──────────────────────────────────────────────────────┤
│ 1. git diff 最终审查所有变更                            │
│ 2. 提交代码（Conventional Commits 格式）                │
│ 3. 创建 PR 并让 Codex 生成描述                         │
│ 4. 团队代码审查 → 合并                                 │
└──────────────────────────────────────────────────────┘
```

---

## 14. 常见反模式与避坑指南

### 14.1 反模式列表

|反模式|问题|解决方案|
|---|---|---|
|无 AGENTS.md|60% 的支持工单源于”幽灵上下文”问题|花 15 分钟配置 AGENTS.md|
|马拉松会话|上下文污染和腐烂导致质量下降|一任务一会话，及时 /compact|
|命令式提示|“做个仪表板”缺乏背景和标准|说明业务目标、用户场景、验收标准|
|过度委托|完全不审查，尤其是安全代码|始终人工审查关键代码路径|
|跳过 Git|在非版本控制目录中工作|始终使用 Git，保留回滚能力|
|全局 Full Auto|所有场景都用全自动模式|渐进式信任：Suggest → Auto Edit → Full Auto|
|循环纠错|在长会话中反复修正同一问题|新建会话 + 更精确的提示词|
|提示输出规划|要求 Codex 先输出计划再执行|官方建议移除规划提示（推理摘要已内置）|
|忽视 Skills|仍在使用已废弃的 Custom Prompts|迁移到 Skills 系统|

### 14.2 快速排障

```text
Q: Codex 生成的代码风格不一致？
A: 检查 AGENTS.md 是否指定了参考文件和风格要求。
   在提示中显式引用示例文件。

Q: Codex 执行了不期望的操作？
A: 降低审批模式级别（Auto Edit → Suggest），
   在 AGENTS.md 中添加明确的限制规则。

Q: 长会话中 Codex 开始"遗忘"早期指令？
A: 运行 /compact 压缩上下文，或开新会话。

Q: 多代理工作流中出现冲突？
A: 并行写入操作容易冲突。将写入密集的任务串行化，
   只对读取密集的任务使用并行代理。

Q: 任务执行太慢？
A: 考虑将推理强度从 xhigh 降到 medium；
   对于实时交互场景使用 Codex-Spark 变体。
```

---

## 15. 与其他工具对比参考

|维度|GPT-5.3-Codex|Claude Code|GitHub Copilot|
|---|---|---|---|
|模型|GPT-5.3-Codex|Claude Opus 4.6 / Sonnet 4.6|多模型支持|
|项目配置|AGENTS.md|CLAUDE.md|.github/copilot|
|运行方式|CLI + Cloud + App + IDE|CLI + IDE|IDE 内置|
|审批模式|3 级（Suggest/Auto Edit/Full Auto）|按工具粒度配置|建议式为主|
|多代理|内置支持（实验性）|通过子代理实现|有限支持|
|技能系统|Skills（跨平台标准）|Skills（兼容）|Extensions|
|长任务|Cloud 异步 + Compaction|Compaction|受限|
|定价|3.50/28 per M tokens|15/75 per M tokens|订阅制|

---

## 16. 参考资料

### 官方文档

- [GPT-5.3-Codex 发布公告](https://link.zhihu.com/?target=https%3A//openai.com/index/introducing-gpt-5-3-codex/)
- [GPT-5.3-Codex System Card](https://link.zhihu.com/?target=https%3A//openai.com/index/gpt-5-3-codex-system-card/)
- [Codex CLI 文档](https://link.zhihu.com/?target=https%3A//developers.openai.com/codex/cli/)
- [Codex CLI 功能特性](https://link.zhihu.com/?target=https%3A//developers.openai.com/codex/cli/features/)
- [Codex CLI 命令参考](https://link.zhihu.com/?target=https%3A//developers.openai.com/codex/cli/reference/)
- [AGENTS.md 配置指南](https://link.zhihu.com/?target=https%3A//developers.openai.com/codex/guides/agents-md/)
- [Codex Prompting Guide](https://link.zhihu.com/?target=https%3A//developers.openai.com/cookbook/examples/gpt-5/codex_prompting_guide/)
- [Agent Skills](https://link.zhihu.com/?target=https%3A//developers.openai.com/codex/skills/)
- [多代理工作流](https://link.zhihu.com/?target=https%3A//developers.openai.com/codex/multi-agent/)
- [Agents SDK 集成](https://link.zhihu.com/?target=https%3A//developers.openai.com/codex/guides/agents-sdk/)
- [高级配置](https://link.zhihu.com/?target=https%3A//developers.openai.com/codex/config-advanced/)
- [配置参考](https://link.zhihu.com/?target=https%3A//developers.openai.com/codex/config-reference/)

### 社区资源

- [Codex Agent Loop 原理解析 — OpenAI](https://link.zhihu.com/?target=https%3A//openai.com/index/unrolling-the-codex-agent-loop/)
- [How Codex is Built — Pragmatic Engineer](https://link.zhihu.com/?target=https%3A//newsletter.pragmaticengineer.com/p/how-codex-is-built)
- [社区 Tips and Tricks](https://link.zhihu.com/?target=https%3A//community.openai.com/t/tips-and-tricks-for-using-codex/1373143)
- [AGENTS.md 标准](https://link.zhihu.com/?target=https%3A//agents.md/)
- [Skills GitHub 仓库](https://link.zhihu.com/?target=https%3A//github.com/openai/skills)
- [OpenAI Codex CLI Guide 2026](https://link.zhihu.com/?target=https%3A//serenitiesai.com/articles/openai-codex-cli-guide-2026)
- [Codex 101 完整指南](https://link.zhihu.com/?target=https%3A//sidsaladi.substack.com/p/openai-codex-101-the-complete-guide)

---

> **总结**：高效使用 GPT-5.3-Codex 的核心在于——**配置好 AGENTS.md**（让 Codex 理解你的项目）， **写好提示词**（说明意图和验收标准），**管理好上下文**（一任务一会话 + Compaction）， **渐进式信任**（Suggest → Auto Edit → Full Auto）， 并始终保持**人工审查关键代码**和**Git 版本控制**的习惯。 善用 **Skills 系统**和**多代理工作流**可进一步提升复杂项目的开发效率。

发布于 2026-03-02 20: