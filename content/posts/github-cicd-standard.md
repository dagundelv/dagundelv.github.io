+++
title = "GitHub CI/CD 标准化：从 dev 到 main 的自动部署"
date = 2026-02-28T09:05:00+08:00
draft = false
tags = ["CI/CD", "GitHub Actions", "部署", "Vite"]
categories = ["工程实践"]
description = "一套稳定的 CI/CD 触发规则与前端部署脚本模板。"
+++

## 1. 推荐触发规则

- `dev` 分支更新：自动部署到测试环境。
- `main` 分支更新：自动部署到生产环境。

这能保证开发验证与生产发布分离，减少误发布。

## 2. 标准部署步骤

```bash
git pull
npm ci
npx vite build
# 拷贝 dist 到站点目录
```

关键点：

- 用 `npm ci` 替代 `npm install`，更快、更稳定、更可复现。
- 用 `npx vite build` 避免找不到本地命令。

## 3. 常见报错与修复

报错：`vite: command not found`

原因：依赖未安装或脚本没用 `npx`。

修复：

```bash
git pull
npm ci
npx vite build
```

## 4. 发布前检查清单

- 工作流触发条件是否正确（分支名无误）。
- 构建命令是否与项目一致。
- 构建产物目录（如 `dist`）是否正确发布。
- 失败时是否保留日志便于回滚定位。

CI/CD 目标不是“自动”，而是“稳定可重复”。
