---
title: "在Linux CentOS 6.6上安装Python 2.7.9"
date: 2017-02-15T00:00:00+08:00
categories: 
  - 服务器
  - WEB服务器
tags: 
  - python
  - centos
  - linux
draft: false
---

The blog post provides a step-by-step guide to installing Python 2.7.9 on CentOS 6.6, which originally comes with Python 2.6.6. The steps include:

1. Install development tools: `yum groupinstall "Development tools"`
2. Install required packages:
   - zlib-devel
   - bzip2-devel
   - openssl-devel
   - ncurses-devel
   - sqlite-devel

3. Download Python 2.7.9 source code
4. Compile and install:
   ```bash
   ./configure --prefix=/usr/local
   make && make altinstall
   ```
5. Create symlink: `ln -s /usr/local/bin/python2.7 /usr/local/bin/python`
6. Verify installation: `python -V` (which should show Python 2.7.9)

The motivation was to have a Python version ≥ 2.7 for compiling LLVM.