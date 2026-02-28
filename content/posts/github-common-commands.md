+++
title = "GitHub 经常使用到的命令（按场景整理）"
date = 2026-02-28T10:00:00+08:00
draft = false
tags = ["Git", "GitHub", "命令行", "工程实践"]
categories = ["开发工具"]
description = "覆盖从初始化仓库到多人协作的 GitHub 常用 Git 命令清单。"
+++

你想了解在日常使用 GitHub 时最常用的 Git 命令，我按使用场景整理了一套高频且实用的命令清单，覆盖从初始化仓库到协作开发的全流程。

## 一、基础配置（首次使用必做）

这些命令用于配置 Git 的身份信息，确保提交记录能正确关联到你的 GitHub 账号。

```bash
# 配置全局用户名（建议与 GitHub 用户名一致）
git config --global user.name "Your GitHub Username"

# 配置全局邮箱（必须是 GitHub 账号绑定的邮箱）
git config --global user.email "your_email@example.com"

# 查看已配置的信息，验证是否设置成功
git config --list
```

## 二、仓库操作

### 1. 本地初始化新仓库

```bash
# 在当前目录初始化 Git 仓库
git init

# 将本地仓库关联到 GitHub 远程仓库（替换为你的仓库地址）
git remote add origin https://github.com/你的用户名/仓库名.git
```

### 2. 克隆远程仓库到本地

```bash
# 克隆公开仓库（HTTPS 方式，新手推荐）
git clone https://github.com/用户名/仓库名.git

# 克隆公开仓库（SSH 方式，需配置 SSH 密钥，免重复输密码）
git clone git@github.com:用户名/仓库名.git
```

## 三、日常开发核心命令

### 1. 查看仓库状态

```bash
# 查看文件修改状态（最常用，知道哪些文件被改/新增/删除）
git status
```

### 2. 暂存与提交

```bash
# 暂存指定文件（比如暂存 README.md）
git add README.md

# 暂存所有修改/新增的文件（推荐日常使用）
git add .

# 提交暂存区的文件到本地仓库，必须写提交说明（描述修改内容）
git commit -m "feat: 新增登录功能"

# 撤销最后一次提交（未推送到远程时可用，保留修改内容）
git reset --soft HEAD^
```

### 3. 同步远程仓库

```bash
# 拉取远程仓库的最新代码（日常开发前先拉取，避免冲突）
git pull origin 分支名  # 比如 main/master

# 将本地提交推送到 GitHub 远程仓库
git push origin 分支名  # 比如 main/master

# 首次推送时绑定本地分支与远程分支（后续可直接 git push）
git push -u origin main
```

## 四、分支管理（协作开发核心）

```bash
# 查看所有分支（* 表示当前所在分支）
git branch

# 创建新分支（比如创建 feature/login 分支）
git branch feature/login

# 切换到指定分支
git checkout feature/login

# 创建并直接切换到新分支（最常用）
git checkout -b feature/login

# 删除本地分支（分支已合并后清理）
git branch -d feature/login

# 推送本地新分支到远程
git push origin feature/login

# 删除远程分支
git push origin --delete feature/login
```

## 五、解决冲突 / 撤销操作

```bash
# 放弃单个文件的本地修改（恢复到最近提交状态）
git checkout -- README.md

# 放弃所有本地修改（谨慎使用，未提交的修改会丢失）
git checkout .

# 拉取远程代码并自动合并（冲突时需手动解决）
git pull

# 解决冲突后，重新暂存并提交
git add .
git commit -m "fix: 解决分支合并冲突"
```

## 六、其他高频命令

```bash
# 查看提交历史（简洁版）
git log --oneline

# 查看提交历史（含分支走向，可视化）
git log --graph --oneline --all

# 查看本地与远程仓库的关联信息
git remote -v

# 移除本地与远程仓库的关联
git remote remove origin
```

## 总结

核心流程：`git clone`（克隆）→ `git checkout -b 新分支`（建分支）→ `git add .`（暂存）→ `git commit`（提交）→ `git push`（推送）→ `git pull`（拉取最新）。

首次配置：必须先执行 `git config --global` 配置用户名和邮箱，否则无法提交代码。

分支规范：协作开发时建议为每个功能 / 修复创建独立分支，避免直接修改 `main/master` 分支。
