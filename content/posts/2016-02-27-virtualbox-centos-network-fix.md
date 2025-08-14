---
title: "VirtualBox 中复制 CentOS 虚拟机不能上网解决方案"
date: 2016-02-27T00:00:00+08:00
categories: 
  - linux
  - 服务器
  - VPS
  - 工具
tags: 
  - virtualbox
  - centos
  - 网络配置
  - 虚拟机
draft: false
---

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