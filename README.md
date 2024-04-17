# IM

该项目使用了Springboot技术开发Spring程序，使用了mybatisplus框架，mysql，redis数据库，以及hutool工具类，jastpt加密，阿里云OSS对象存储，SpringSecurity安全框架，netty增强WebSocket，RabbitMQ等技术

## 项目主要结构

***聊天命令包***（所有聊天的指令）

***配置包***（包含跨域请求处理过滤器，雪花算法传递问题处理器，SpringSecurity配置类，RabbitMQ错误队列配置类）

***表现层包***（包含全局异常处理器）

***实体类包***

***dto传输数据包***

***实体类包***

***自定义异常包***

***过滤器包***（用户登录token处理过滤器）

***处理器包***（WebSocket聊天业务的各个处理器）

***RabbitMQ监听器包***

***数据层包***

***业务层包***（包含UserDetail的具体实现，上传图片业务，WebSockethandler事务业务）

***Session包***（存储用户的channel信息）

***utils工具包***（各种常量，以及加解密工具类，oos对象上传工具类，更改返回请求信息到前端的web工具类，雪花算法传递json处理工具类，分析token工具类等）

***WebSocket包***（包含所有指令的父类指令，各个指令类型的枚举类，和netty的服务器类）

## 项目功能介绍

该项目搭建了一个基于WebSocket的在线聊天室，支持单聊群聊，离线在线，图片文字聊天，支持好友申请，屏蔽功能等一系列功能

## 项目亮点

使用RabbitMQ异步提交聊天的信息到数据库来增强聊天业务的性能，优化用户体验，频繁查询的数据使用了redis缓存功能，减小数据库压力，利用redis完成用户上线主动向用户推送好友申请的结果

## 项目待改进点

对于群聊的创建暂未添加拉取群聊时对于对方是否是自己的联系人的判断，未读消息数，以及用户阅读消息后更改消息的状态为已读尚未完成，早期设计向用户发消息使用的是用户名，而向群发消息则用的是群ID，导致逻辑有些混乱，使用用户Id还可以在某种程度上减少对数据库的查询增强项目的性能

## 项目如何启动

通过dockerfile部署项目，部署对应的mysql与redis后，以及RabbitMQ可启动