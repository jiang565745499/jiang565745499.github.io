---
title: Mybatis
tags: Java
article_header:
  type: cover
  image:
    src: /screenshot.jpg
---



# Mybatis

```
Hibernate:全自动全映射ORM框架,旨在消除sql.
Mybatis:半自动化的持久层框架.sql与java编码分离,sql是开发人员控制
```

```
SqlSession代表和数据库的一次会话,用完必须关闭,它和connection一样都是非线程安全的,每次使用都应该去获取新的对象.
mapper接口,没有实现类,但是mybatis会为这个接口生成一个代理对象.(接口和xml进行绑定)
两个重要的配置文件
	1)mybatis全局配置文件,包含数据库连接池信息,事务管理器信息等...系统运行环境信息
	2)sql映射文件,保存了每一个sql语句的映射信息.
```

