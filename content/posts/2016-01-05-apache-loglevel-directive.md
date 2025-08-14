---
title: "apache配置文件里的LogLevel 指令"
date: 2016-01-05T00:00:00+08:00
categories: 
  - apache
  - 服务器
  - WEB服务器
tags: 
  - apache
  - 日志配置
  - loglevel
draft: false
---

The article explains the Apache LogLevel directive, which controls the verbosity of error logging. Key points include:

- Purpose: Adjust the detail level of information recorded in error logs
- Syntax: `LogLevel <level>`
- Default Setting: `LogLevel warn`

Log Levels (from most to least critical):
1. emerg (Emergency)
2. alert
3. crit (Critical)
4. error
5. warn (Warning)
6. notice
7. info
8. debug

Notable Quote: "当指定了特定级别时，所有级别高于它的信息也会同时报告。" (When a specific level is specified, all information at higher levels will also be reported.)

Recommendation: "建议至少要使用crit级别。" (It is recommended to use at least the crit level.)

Example Configuration: `LogLevel notice`