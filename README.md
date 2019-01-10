# Gupao-mall

## 项目的目的（这些都会在课堂中间讲到具体某个知识的时候去分析）

> 帮助大家对分布式架构和应用有一个整体认识
> 明白自己学到的技术真正应用到实战中是如何去解决问题的
> 帮助大家建立解决问题的思路

# 架构图

![架构图](架构图.png)

## 模块

![技术模块](技术模块.png)




# 代码更新进度

1. 完成单点登录开发
2. 完成转盘抽奖域的设计
3. 完成收银台页面及业务领域模块的构建
4. 支付模块的代码设计和开发
5. 抽奖模块的核心代码开发及表结构设计（待测试）
6. 支付宝接口联调（由于域名环境还没准备好，还没有正式调通）
7. 增加assembly打包功能
8. 完成支付宝、微信的回调逻辑的代码开发


# 使用技术
使用Dubbo+spring 构建整个项目

Maven构建项目

Jenkins作为持续集成

使用 Apollo 配置中心

使用Spring+Spring MVC+MyBatisSSM框架

数据库连接池使用druid

数据库使用MySQL和Redis

前后端完全分离

采用ElasticSearch实现搜索服务

负载均衡使用Nginx、keepalived实现高可用

消息中间件采用ActiveMQ

在分布式事务上则采用了TCC解决时效性要求性高的分布式事务

可靠的消息服务则来解决时效性要求低的分布式事务.

# 服务列表服务

| 项目      |  描述 | 端口 | 备注  |
| :-------- | --------:| :--: | ---- |
| gpmall-activity | 产品服务子域 转盘抽奖 | 8081 |  转盘抽奖 |
| gpmall-common | 无须运行，直接添加到依赖 |  无  |  公共服务包  |
| gpmall-parent | 父控项目，用来管理mave依赖的jar的版本 | 无 | 父控  |
| gpmall-sso  | 对应产品服务 登录子域,tomcat运行 | 8080 | 登录子域 |
| user-service | 对应核心业务服务子域`用户服务`，dubbo服务 | 20880 | 用户服务 |
| gpmall-cashier | 收银台服务 | 8082 | 收银台 |
| activity-service | dubbo服务 | 20881 | 营销平台 |
| pay-service | 支付核心-dubbo服务 | 20882 | 支付核心 |
|  |  |  |  |

# 部署说明

1. 需要先构建基础服务，讲gpmall-common/gpmall-parent这两个基础服务先install到本地私服
2. 启动dubbu服务，user-service 。 暂时需要依赖zookeeper
3. 运行相应的产品服务，gpmall-sso/gpmall-activity/gpmall-cashier等