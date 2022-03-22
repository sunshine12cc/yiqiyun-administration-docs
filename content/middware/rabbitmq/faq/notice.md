---
title: "消息数据如何持久化"
description: test
weight: 27
draft: false
---

RabbitMQ 支持消息的持久化，也就是数据写在磁盘上，为了数据安全考虑，大多数用户可能都会选择持久化。

> **注意**
>
> RabbitMQ作为传统消息队列，在消息未持久化的情况下，如果您重启或者关闭消息所在节点，会造成消息丢失；如果设置了持久化的策略，但未设置 HA 镜像队列模式，删除消息所在的单节点也会造成数据丢失。
>
> 当您有非常重要的队列消息需要存储的时候，建议持久化并[设置镜像队列HA](../../manual/setup_mirror/)。删除节点的时候，为避免消息丢失，请不要把消息所在节点全部删除。

消息队列持久化包括3个部分：

- exchange持久化，在声明时指定durable =>1（true）
- queue持久化，在声明时指定durable =>1 （true）
- 消息持久化，在投递时指定delivery_mode =>2（1是非持久化）

如果exchange和queue都是持久化的，那么它们之间的binding也是持久化的。如果exchange和queue两者之间有一个持久化，一个非持久化，就不允许建立绑定。即使设置了持久化，也不能百分百保证消息不会丢失。有很小的概率在RabbitMQ接受到消息后，还没来得及写到磁盘，就发生重启了，所以写消息的时候尽量不要重启节点，例如：新增减少磁盘节点、修改参数、扩容伸缩集群都会导致集群的重启。如果需要加强的安全保证，可以把发布消息的代码封装在事务里。 如果您的消息需要持久化，请务必保证queue是持久化的，并在投递消息的时候设置delivery_mode =2。