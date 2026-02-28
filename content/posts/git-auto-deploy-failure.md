+++
title = "Git 自动部署失败：从报错到稳定上线"
date = 2026-02-28T09:00:00+08:00
draft = false
tags = ["Git", "CI/CD", "GitHub Pages", "Hugo"]
categories = ["工程实践"]
description = "一次自动部署失败的完整排查记录：定位、修复和防复发。"
+++

这篇文章整理自你提供的豆包话题《Git 自动部署失败》，并结合可落地的 Hugo + GitHub Pages 实践，给出一套可复用排查路径。

## 1. 常见失败信号

- Push 后仓库没有触发工作流。
- 工作流触发了，但 `build` 失败。
- `build` 成功，Pages 仍是旧页面或 404。

先看日志再改代码，避免“边猜边改”。

## 2. 最小排查清单

1. 仓库名是否是 `dagundelv.github.io`（用户主页仓库建议使用该命名）。
2. `hugo.toml` 的 `baseURL` 是否是 `https://dagundelv.github.io/`。
3. 工作流是否安装了 Hugo Extended，并执行了 `hugo` 构建。
4. Pages Source 是否配置为 GitHub Actions。
5. 是否把无效主题配置留在 `hugo.toml`（例如 `theme` 指向不存在目录）。

## 3. 直接可用的修复方案

本仓库采用以下策略避免再次踩坑：

- 使用仓库内置模板（`layouts/` + `static/css/`），不依赖远端主题拉取。
- 用 GitHub Actions 自动构建并部署到 Pages。
- 文章与配置分离，先保证站点能稳定出包。

## 4. 防复发建议

- 每次改配置后本地先执行一次：

```bash
hugo
```

- 每次推送前检查：

```bash
hugo server -D
```

- 变更主题时同步检查 `hugo.toml` 和 `themes/`，避免“配置有、目录无”。

## 5. 小结

自动部署失败通常不是单点问题，而是“配置 + 构建 + 发布链路”某一环断裂。  
把排查流程固定下来，比临时修 bug 更重要。
