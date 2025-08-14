# Blog Posts Extraction from https://blog.0902.org

This document contains all blog posts extracted from the blog, organized for potential conversion to Hugo markdown posts.

## Blog Overview
- **Blog Name**: 分享网 (Sharing Network)
- **Platform**: Typecho
- **Total Posts**: 12 posts across 3 pages
- **Date Range**: 2015-09-23 to 2017-02-15

## Complete Blog Posts Collection

### Post 1
**Title**: 在Linux CentOS 6.6上安装Python 2.7.9  
**Date**: 2017-02-15  
**Author**: admin  
**Categories**: 服务器, WEB服务器  
**URL**: https://blog.0902.org/server/21.html

**Content**:
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

---

### Post 2
**Title**: 常见社工查询地址  
**Date**: 2016-04-05  
**Author**: admin  
**Categories**: 网络工具, 工具  
**URL**: https://blog.0902.org/network/19.html

**Content**:
The blog post lists several web addresses for social engineering and information lookup tools:
- http://sgk.cnseu.cn/# (Social Engineering Library)
- http://cha.hx99.net/ (Query Site)
- http://pmd5.com/# (MD5 Lookup)
- http://www.hx99.net/online/ (Online Tool Collection)
- http://attach.blackbap.org/down/ (Weapon Library)
- http://blackbap.org/

Note: The content appears to be a list of websites related to information lookup and potential social engineering resources.

---

### Post 3
**Title**: 在线正则工具  
**Date**: 2016-03-25  
**Author**: admin  
**Categories**: 工具网站  
**URL**: https://blog.0902.org/toolweb/18.html

**Content**:
The blog post recommends an online regex tool from OSChina:
- Link: http://tool.oschina.net/regex/#
- Description: "站长工具提供的在线正则工具，非常强大，推荐各位使用" (Webmaster tools provide a powerful online regex tool, highly recommended for use)

The post is brief, essentially serving as a recommendation for an online regex tool with a direct link to the resource.

---

### Post 4
**Title**: Web Debugger Fiddler 超强网络抓包工具  
**Date**: 2016-03-25  
**Author**: admin  
**Categories**: 网络工具, 工具, WEB服务器  
**URL**: https://blog.0902.org/network/17-1.html

**Content**:
Fiddler is a free HTTP debugging proxy software developed in C#, available in .NET 2 and .NET 4 versions. It can record all HTTP communications between a computer and the internet, allowing users to inspect communications, set breakpoints, and examine incoming and outgoing data.

Installation Tutorial: http://jingyan.baidu.com/article/5d6edee221f0b399ebdeec7f.html  
Detailed Tutorial: http://www.cnblogs.com/forcertain/archive/2012/11/29/2795139.html  
Download Link: http://soft.hysem.com/tool/fiddler4setup.exe

---

### Post 5
**Title**: typecho首页生成静态  
**Date**: 2016-03-25  
**Author**: admin  
**Categories**: 默认分类  
**URL**: https://blog.0902.org/default/17.html

**Content**:
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

---

### Post 6
**Title**: 如何在CentOS或RHEL上搭建Squid透明Web代理系统  
**Date**: 2016-03-24  
**Author**: 章翔  
**Categories**: 服务器, WEB服务器, 网络工具  
**URL**: https://blog.0902.org/server/14.html

**Content**:
The article provides a comprehensive tutorial on setting up a Squid transparent web proxy on CentOS/RHEL, covering:
- Benefits of transparent proxying
- Network topology setup
- Installation steps
- Configuration details
- Access control methods
- IP and website filtering
- Caching mechanisms

The tutorial is aimed at system administrators looking to implement a robust web proxy solution with granular traffic management capabilities.

The full technical walkthrough includes practical examples of:
- iptables configuration
- Squid installation
- Network access controls
- Site and IP blocking
- Download size restrictions
- Caching strategies

---

### Post 7
**Title**: VirtualBox 中复制 CentOS 虚拟机不能上网解决方案  
**Date**: 2016-02-27  
**Author**: admin  
**Categories**: linux, 服务器, VPS, 工具  
**URL**: https://blog.0902.org/server/13.html

**Content**:
The article provides a step-by-step guide for resolving network connectivity issues when copying a CentOS virtual machine in VirtualBox. The main steps include:

1. Cloning a virtual machine in VirtualBox
2. Modifying network settings after cloning
3. Updating udev rules and network configuration files

Key Technical Steps:
- Edit `/etc/udev/rules.d/70-persistent-net.rules`
- Update MAC addresses in network configuration files
- Modify `/etc/sysconfig/network-scripts/ifcfg-eth0` and `/etc/sysconfig/network-scripts/ifcfg-eth1`
- Reboot the virtual machine

The guide emphasizes the importance of reinitializing MAC addresses when cloning to prevent network conflicts and provides detailed instructions for reconfiguring network interfaces.

---

### Post 8
**Title**: Nginx 反向代理任意请求的域名  
**Date**: 2016-02-16  
**Author**: admin  
**Categories**: WEB服务器, nginx  
**URL**: https://blog.0902.org/web/12.html

**Content**:
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
        if ($host ~ (.*)\\.qiyichao\\.cn) {
            proxy_pass http://$1;
        }
        # Additional proxy and header configurations...
    }
}
```

The configuration allows proxying requests like `baidu.example.com` to `www.baidu.com`.

---

### Post 9
**Title**: apache配置文件里的LogLevel 指令  
**Date**: 2016-01-05  
**Author**: admin  
**Categories**: apache, 服务器, WEB服务器  
**URL**: https://blog.0902.org/server/11.html

**Content**:
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

---

### Post 10
**Title**: Apache 关闭 access_log 并优化 error_log  
**Date**: 2016-01-05  
**Author**: admin  
**Categories**: 默认分类, 服务器, WEB服务器  
**URL**: https://blog.0902.org/default/10.html

**Content**:
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

---

### Post 11
**Title**: WDCP支持多个域名同时使用一个非80端口  
**Date**: 2015-12-28  
**Author**: admin  
**Categories**: 服务器, WEB服务器  
**Tags**: apache  
**URL**: https://blog.0902.org/server/9.html

**Content**:
The blog post describes a problem with WDCP where multiple domains using a non-80 port would automatically redirect to the last configured website. The author suggests a solution by manually adding a port configuration in the Apache configuration file:

```apache
NameVirtualHost *:80
NameVirtualHost *:新增的端口号
Include conf/httpd-wdl.conf
Include conf/vhost/*.conf
```

The post provides a technical workaround for a limitation in WDCP's domain and port configuration.

---

### Post 12
**Title**: ECS Linux CentOS 6.3搭建PPTP VPN  
**Date**: 2015-10-10  
**Author**: admin  
**Categories**: 服务器, WEB服务器, 网络工具  
**URL**: https://blog.0902.org/server/pptp-vpn.html

**Content**:
A detailed technical guide for setting up a PPTP VPN on CentOS 6.3, including step-by-step instructions covering:

1. Server-side software installation
   - Installing ppp and pptpd packages
   
2. Configuration steps
   - Editing configuration files (/etc/pptpd.conf, /etc/ppp/options.pptpd)
   - Setting up user credentials in /etc/ppp/chap-secrets
   
3. Kernel and network configuration
   - Enabling IP forwarding
   - Configuring iptables rules
   
4. Service management
   - Restarting PPTP service
   - Configuring services to start on system boot

The guide provides terminal commands and specific configuration details for each step, aimed at system administrators setting up a VPN server.

---

### Post 13
**Title**: CentOS 6.4下Squid代理服务器的安装与配置  
**Date**: 2015-10-09  
**Author**: admin  
**Categories**: 服务器, 网络工具  
**URL**: https://blog.0902.org/server/squid.html

**Content**:
The article provides a comprehensive guide to installing and configuring Squid proxy server on CentOS 6.4, covering:

1. Squid Introduction
- Explains proxy server functionality
- Describes Squid's caching mechanism
- Details proxy types: normal, transparent, and reverse proxy

2. Installation Steps
- System environment details
- Squid installation via yum
- Configuration file (/etc/squid/squid.conf) explanation
- Configuration for different proxy scenarios

3. Practical Demonstrations
- Normal proxy configuration
- Transparent proxy setup
- Reverse proxy implementation
- Domain-based load balancing example

The guide includes detailed command-line instructions, network topology diagrams, and screenshots to illustrate each configuration stage.

---

### Post 14
**Title**: centos安装nginx配置cdn全过程  
**Date**: 2015-09-23  
**Author**: admin  
**Categories**: centos, nginx, cdn  
**URL**: https://blog.0902.org/server/centos-nginx.html

**Content**:
The blog post provides a comprehensive guide to installing and configuring Nginx with CDN capabilities on CentOS, including:

1. Environment Preparation
- Install compilation tools
- Open firewall ports
- Download required software packages

2. Installation Steps
- Install PCRE
- Create Nginx user and group
- Compile Nginx with cache purge module
- Configure Nginx directories and permissions

3. Configuration Details
- Set up upstream server configurations
- Configure proxy settings
- Create cache directories
- Optimize buffer and timeout settings

The guide is intended for system administrators looking to implement a CDN solution using Nginx on CentOS, with specific focus on performance optimization and caching strategies.

## Summary

### Categories Distribution:
- **服务器 (Server)**: 9 posts
- **WEB服务器 (Web Server)**: 8 posts
- **网络工具 (Network Tools)**: 4 posts
- **工具 (Tools)**: 3 posts
- **默认分类 (Default Category)**: 2 posts
- **工具网站 (Tool Websites)**: 1 post
- **nginx**: 2 posts
- **apache**: 2 posts
- **linux**: 1 post
- **VPS**: 1 post
- **cdn**: 1 post
- **centos**: 1 post

### Content Themes:
1. **Server Administration**: CentOS/RHEL configurations, Apache/Nginx setups
2. **Network Tools**: Proxy servers, VPN setup, network debugging
3. **Web Development**: Reverse proxies, CDN configuration, logging optimization
4. **System Tools**: Python installation, virtualization, static site generation
5. **Security/Information**: Social engineering tools, network analysis

All posts are technical in nature, primarily focused on Linux system administration, web server configuration, and network management. The content is suitable for system administrators and developers working with Linux-based web infrastructure.