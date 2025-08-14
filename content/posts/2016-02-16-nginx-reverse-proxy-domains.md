---
title: "Nginx 反向代理任意请求的域名"
date: 2016-02-16T00:00:00+08:00
categories: 
  - WEB服务器
  - nginx
tags: 
  - nginx
  - 反向代理
  - 域名代理
draft: false
---

The article describes a solution for reverse proxying any domain using Nginx. The author's original approach involved crawling domains and generating Nginx configuration files. The key challenge was correctly handling resource references across subdomains.

The solution involves using a Nginx configuration with a regex to extract the target domain from the subdomain, enabling proxy passing. The provided configuration:
- Listens on port 80
- Uses a wildcard server name
- Extracts the target domain from the subdomain
- Sets appropriate proxy headers
- Uses a substitution filter to rewrite URLs

Nginx Configuration Snippet:
```nginx
server {
    listen 80;
    server_name _;
    location / {
        resolver 8.8.8.8;
        if ($host ~ (.*)\.qiyichao\.cn) {
            proxy_pass http://$1;
        }
        # Additional proxy and header configurations...
    }
}
```

The configuration allows proxying requests like `baidu.example.com` to `www.baidu.com`.