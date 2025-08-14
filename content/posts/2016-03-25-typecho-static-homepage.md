---
title: "typecho首页生成静态"
date: 2016-03-25T00:00:00+08:00
categories: 
  - 默认分类
tags: 
  - typecho
  - 静态化
  - 性能优化
draft: false
---

The blog post describes how to generate a static HTML homepage for a Typecho-based blog. The author shares a PHP script that can be used to automatically create a static index.html file every 10 minutes. Key steps include:

1. Upload a PHP script to the website root directory
2. Configure the script to generate index.html
3. Add a small JavaScript snippet to refresh the static page

Key Code Snippet:
```php
<?php
$nowtime=time();
$pastsec = $nowtime - $_GET["t"];
if($pastsec<600)
{
exit; //10分钟更新一次，时间可以自己调整
}
// ... rest of the script
?>
```

The author notes this method is simpler than using a plugin and can help improve site performance by generating a static homepage.