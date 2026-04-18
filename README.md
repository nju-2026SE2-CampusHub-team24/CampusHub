# CampusHub

校园互助服务平台课程项目仓库。

## 1. 项目概述

- 项目名称：CampusHub（校园互助服务平台）
- 课程名称：软件工程与计算 II
- 团队名称：我竟无言以队
- 建立日期：2026年3月20日
- 仓库地址：https://github.com/nju-2026SE2-CampusHub-team24/CampusHub

本项目面向校园场景，围绕“互助需求发布、接单与履约”构建可持续迭代的软件系统，按课程阶段推进需求分析、架构设计、编码实现、测试与交付。

## 2. 团队成员与初始角色

| 姓名 | 学号 | 专业/班级 | 初始角色 |
|------|------|-----------|----------|
| 陈益民 | 241880528 | 智能软件与工程 | 需求负责人 |
| 刘庭毅 | 241880492 | 智能软件与工程 | 架构负责人 |
| 滕明杰 | 241880546 | 智能软件与工程 | 开发负责人 |
| 潘孝涛 | 241880529 | 智能软件与工程 | 测试负责人 |

角色职责详见：docs/P0/团队章程.md。

## 3. P0 阶段目标

P0（项目启动与 AI 协作契约）阶段主要完成：

- 明确团队角色分工与协作机制
- 完成 AI 工具链选型与使用规范
- 签署《AI 协作契约》并落地过程约束
- 完成仓库基础设施搭建与目录初始化

### 3.1 技术栈选型

- 后端：Spring Boot（Java）
- 前端：Vue 3 + Element Plus
- 数据库：MySQL
- CI/CD：GitHub Actions

选型说明：

- Spring Boot 生态成熟，适合快速构建分层后端与 REST API。
- Vue 3 + Element Plus 上手成本低，适合课程项目快速实现中后台交互界面。
- MySQL 适配常见业务场景，便于本地开发和后续部署。
- GitHub Actions 与仓库原生集成，便于持续集成与质量门禁。

## 4. AI 工具链选型

### 4.1 AI 对话工具

- ChatGPT
- Google Gemini

选择理由：用于需求分析、文档初稿生成、问题答疑与思路拓展，便于交叉验证与统一协作。

### 4.2 AI 编程助手

- GitHub Copilot

选择理由：与开发环境集成度高，可提升代码补全、样板代码编写和测试编写效率。

### 4.3 AI 代码审查方式

- 人工 Code Review
- coderabbit

选择理由：以人工审查为主，AI 辅助发现潜在问题和改进点。

### 4.4 AI 测试辅助

- GitHub Copilot

选择理由：辅助生成测试样例、补全边界情况与测试思路。

## 5. AI 协作契约（执行摘要）

完整契约文件：docs/P0/AI协作契约.pdf。

### 5.1 使用原则

- AI 是工具，工程师是责任主体
- 所有 AI 输出必须人工审查后方可合入
- AI 只能辅助，不替代团队成员独立思考
- 最终文档、代码、测试结果由团队成员负责

### 5.2 使用范围

- 允许使用：需求分析、文档初稿、用户故事整理、代码补全、样板代码、测试思路、问题答疑与 Bug 排查
- 需额外审查后使用：核心业务逻辑代码、数据库设计、安全相关代码、正式提交文档与答辩材料
- 完全禁止：伪造调研数据、伪造测试结果、提交未经检查的 AI 输出、违反课程诚信的行为

### 5.3 过程记录要求

- 保留 Prompt 交互日志
- Commit Message 必须标注 [AI-assisted] 或 [Human-written]
- 每阶段填写 AI 协作反思日志

### 5.4 代码合入规则

- AI 生成代码必须经过至少 1 名成员 Code Review
- 每位成员每个编码阶段至少完成 2 个手写核心函数
- 核心模块不得未经测试直接合入主分支
- 合入代码需保证可运行且不破坏基本功能

### 5.5 违约处理

- 首次违规：团队内部提醒并要求修改
- 多次违规：由阶段负责人记录并督促整改
- 严重违规：如实记录并按课程要求处理

## 6. 分支与协作策略

- 主分支：main（稳定可交付）
- 开发分支：dev（阶段性集成）
- 功能分支命名：feature/*
- 修复分支命名：fix/*
- 文档分支命名：docs/*

合并规则：

- 原则上不直接向 main 提交
- 重要修改至少 1 人 Review
- 核心改动先在 dev 或功能分支验证后再合并

## 7. 目录结构

当前仓库目录：

```text
CampusHub/
	.github/
		workflows/
			ci.yml
	backend/
		src/
		pom.xml
	frontend/
		src/
		package.json
	db/
		init/
			schema.sql
	docs/
		P0/
			团队章程.md
			AI协作契约.pdf
	.gitignore
	README.md
```

后续阶段文档将按课程节奏扩展到 docs/P1 至 docs/P7。

## 8. 快速开始

### 8.0 环境要求

- JDK 17
- Maven 3.9+
- Node.js 20 LTS
- npm 10+
- MySQL 8.0
- Git

### 8.1 后端

```bash
cd backend
mvn spring-boot:run
```

### 8.2 前端

```bash
cd frontend
npm install
npm run dev
```

### 8.3 数据库

执行 `db/init/schema.sql` 完成数据库初始化。

### 8.4 本地质量检查

后端编译与风格检查：

```bash
cd backend
mvn -DskipTests compile
mvn checkstyle:check
```

前端构建与风格检查：

```bash
cd frontend
npm run build
npm run lint
```

## 9. CI 配置说明

CI 工作流文件：`.github/workflows/ci.yml`。

- 后端：编译检查（Maven Compile）+ 代码风格检查（Checkstyle）
- 前端：构建检查（Vite Build）+ 代码风格检查（ESLint）

当向 `main` 或 `dev` 推送，或提交到 `main` / `dev` 的 Pull Request 时自动触发。

## 10. 开发与质量约定

- 关键模块需具备基础测试
- 文档、代码、测试同步推进
- 保证提交内容可检查、可追踪、可复现

## 11. P0 交付物对照

- 团队章程文档：已提供（docs/P0/团队章程.md）
- AI 协作契约：已提供（docs/P0/AI协作契约.pdf）
- 项目 README：本文件

P0 要求中的 README、.gitignore、基础项目结构与基础 CI 已完成。
