+++
title = "GitHub 分支与 PR 标准流程（多人协作版）"
date = 2026-02-28T09:10:00+08:00
draft = false
tags = ["Git", "GitHub", "分支管理", "PR"]
categories = ["工程实践"]
description = "main + dev 双主干下的分支命名、PR 流程与多人分模块协作规范。"
+++

## 1. 固定主干分支

- `main`：生产分支，只放可上线代码。
- `dev`：开发分支，所有功能先合并到这里。

长期分支只保留这两条，其它分支都临时创建、用完即删。

## 2. 临时分支命名

- `feature/xxx`：新功能
- `fix/xxx`：缺陷修复
- `refactor/xxx`：重构优化
- `chore/xxx`：脚本或配置维护

## 3. 日常开发流程

```bash
git checkout dev
git pull
git checkout -b feature/xxx
# 开发...
git add .
git commit -m "feat: 完成xxx"
git push origin feature/xxx
```

然后在 GitHub 发起 PR：`feature/xxx -> dev`。

## 4. 评审与合并规则

- 必须走 PR，禁止直接 push `main`。
- PR 必须通过 CI（lint / build / test）。
- 一个分支只做一件事，避免混改多个模块。

## 5. 上线流程

1. `feature/* -> dev`：完成开发与联调。
2. `dev -> main`：测试通过后提发布 PR。
3. 合并 `main` 后触发生产部署。

一句话：**从 dev 拉分支，回 dev 合并；上线时再从 dev 进 main。**
