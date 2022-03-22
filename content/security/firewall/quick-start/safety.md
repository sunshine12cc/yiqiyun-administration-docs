---
title: "安全策略"
linkTitle: "安全策略"
date: 2020-02-28T10:08:56+09:00
description:
draft: false
weight: 3
---

云防火墙产品提供四种安全策略来保证用户资产的安全。

策略生效顺序将按照黑名单、白名单、访问控制策略、入侵防御策略执行。

## 访问控制策略

访问控制策略具体包括互联网防火墙，针对云上公网IP和互联网之间制定内访外和外访内的控制策略，满足云用户对于互联网流量访问控制的管理与安全防护需求。

<img src="../_images/firewall.png" style="zoom:33%;" />

## 入侵防御策略

可以识别访问控制策略以外的未知风险，对互联网上的恶意流量入侵活动和常规攻击行为进行实时阻断和拦截，并提供精准的威胁检测虚拟补丁，智能阻断入侵风险。

<img src="../_images/ips.png" style="zoom:33%;" />

## 流量控制策略

流量控制策略可针对全平台设置内访外和外访内的最大带宽及保障带宽。

<img src="../_images/data_control.png" style="zoom:30%;" />

## 黑白名单

通过配置黑白名单规则，放行指定IP的访问请求，即设置IP黑白名单。

<img src="../_images/blacklist.png" alt="黑名单" style="zoom:33%;" />

<img src="../_images/whitelist.png" alt="白名单" style="zoom:33%;" />
