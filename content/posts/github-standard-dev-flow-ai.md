+++
title = "企业级 GitHub 标准开发流程：分支、数据库、多人协作与 AI 开发流"
date = 2026-02-28T09:40:00+08:00
draft = false
tags = ["Git", "GitHub", "CI/CD", "MySQL", "AI开发"]
categories = ["工程实践"]
description = "一套可直接落地的 GitHub 标准开发流程，覆盖分支规范、数据库同步、多人分模块协作与 AI 工具实践。"
+++

这篇文章整理了一套适合中小团队、可直接执行的 GitHub 企业级开发流程，特别适用于多环境部署、自动发布、前后端分离和医疗类项目。

## 一、标准分支模型

推荐采用 `main + dev` 双主干模型：

- `main`：生产分支，始终可部署、稳定。
- `dev`：开发分支，所有功能先合并到这里。

功能开发统一从 `dev` 拉临时分支：

- `feature/xxx`：新功能
- `fix/xxx`：缺陷修复
- `refactor/xxx`：重构优化
- `chore/xxx`：脚本或配置维护

## 二、标准开发流程（端到端）

1. 拉取最新代码并创建功能分支

```bash
git checkout dev
git pull
git checkout -b feature/xxx
```

2. 本地开发与提交

```bash
git add .
git commit -m "feat: 完成xxx功能"
```

3. 推送并发起 PR

```bash
git push origin feature/xxx
```

4. 代码评审 + CI 检查（lint / build / test）
5. 合并到 `dev`，自动部署到测试环境
6. 测试通过后 `dev -> main`，自动部署生产环境

一句话总结：**开分支 -> 开发 -> PR -> 合并 dev -> 测服验证 -> 合并 main -> 生产部署**。

## 三、CI/CD 触发与部署脚本规范

建议触发规则：

- `dev` 更新：部署测试环境
- `main` 更新：部署生产环境

部署脚本最小标准：

```bash
git pull
npm ci
npx vite build
# 拷贝 dist 到站点目录
```

`vite: command not found` 的本质就是依赖未安装或构建命令不规范，`npm ci + npx vite build` 能稳定规避。

## 四、数据库分离与同步（重点）

核心原则：

- `dev_db` 与 `prod_db` 必须物理隔离。
- **只同步结构，不同步生产业务数据**。
- 结构变更必须脚本化、版本化。

推荐目录：

```text
db/
  v1.0_init.sql
  v1.1_add_user_table.sql
  v1.2_add_hospital_field.sql
```

上线顺序必须固定：

1. 备份生产库
2. 执行 SQL 升级脚本
3. 部署代码
4. 回归验证

禁止事项：

- 直接手工改生产表结构
- 生产数据拉到本地开发使用
- 不留脚本记录的结构变更

## 五、多人分模块协作规范

团队统一规则：

- 长期分支只有 `main` 和 `dev`
- 一人一分支，一模块一分支，不共用临时分支
- 功能分支都从 `dev` 创建并回合到 `dev`

示例：

```text
main
└── dev
    ├── feature/user
    ├── feature/hospital
    ├── feature/order
    ├── fix/login-bug
    └── refactor/api
```

## 六、AI 驱动开发流（Cloud Code / Codex / Copilot）

推荐模式：**AI 写实现，人控架构与质量**。

- 人负责：模块拆分、表结构、权限模型、业务边界。
- AI 负责：CRUD 页面、接口样板、SQL 草稿、部署脚本、文档初稿。

最关键的 4 条纪律：

1. AI 不做架构决策，人来定。  
2. AI 代码必须人工复核后再合并。  
3. Git 分支规范不能因为 AI 而放松。  
4. 数据库变更必须走版本 SQL，不允许 AI 直接操作生产库。  

## 七、落地清单（可直接执行）

- 建立 `main + dev` 双主干
- 建立 PR 审查与 CI 门禁
- 建立 `db/` 版本化 SQL 目录
- 配置 `dev`/`main` 分环境自动部署
- 团队统一 commit 与分支命名规范
- AI 仅提效，不替代审查与决策

这套流程的核心不是“复杂”，而是“可重复、可审计、可回滚”。只要团队坚持执行，协作效率和上线稳定性会显著提升。
