---
title: "Apache 关闭 access_log 并优化 error_log"
date: 2016-01-05T00:00:00+08:00
categories: 
  - 默认分类
  - 服务器
  - WEB服务器
tags: 
  - apache
  - 日志优化
  - 性能优化
draft: false
---

The article provides instructions for optimizing Apache web server logging:

1. In the Apache configuration file, comment out the following log configuration sections:
```apache
#<IfModule log_config_module>
# LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
# LogFormat "%h %l %u %t \"%r\" %>s %b" common

# <IfModule logio_module>
# LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\" %I %O" combinedio
# </IfModule>

# CustomLog logs/access_log common
#</IfModule>
```

2. Change the error log level from:
`LogLevel warn`
to:
`LogLevel crit`

The author notes this optimization was inspired by studying large Web 2.0 sites, particularly LiveJournal's experiences.