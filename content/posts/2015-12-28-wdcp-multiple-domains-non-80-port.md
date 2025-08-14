---
title: "WDCP支持多个域名同时使用一个非80端口"
date: 2015-12-28T00:00:00+08:00
categories: 
  - 服务器
  - WEB服务器
tags: 
  - apache
  - wdcp
  - 域名配置
  - 端口配置
draft: false
---

The blog post describes a problem with WDCP where multiple domains using a non-80 port would automatically redirect to the last configured website. The author suggests a solution by manually adding a port configuration in the Apache configuration file:

```apache
NameVirtualHost *:80
NameVirtualHost *:新增的端口号
Include conf/httpd-wdl.conf
Include conf/vhost/*.conf
```

The post provides a technical workaround for a limitation in WDCP's domain and port configuration.