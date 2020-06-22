---
title: Spring
tags: Java
article_header:
  type: cover
  image:
    src: /screenshot.jpg
---



# Spring

### Spring框架概述

```
Spring是轻量级的开源的JavaEE框架
Spring可以解决企业应用开发的复杂性
Spring有两个核心部分:IOC和Aop
	1)IOC:控制反转,把创建对象的过程交给Spring1进行管理
	2)AOP:面向切面,不修改源代码进行功能增强
Spring特点
	1)方便解耦,简化开发
	2)AOP编程的支持
	3)方便程序的测试
	4)方便集成各种优秀框架
	5)方便进行事务操作
	6)降低API开发难度
```



### IOC容器

#### IOC概念和原理

```
什么是IOC
	1)控制反转,把对象创建和对象之间的调用过程,交给Spring进行管理
	2)使用IOC目的:为了耦合度降低
```

#### IOC(接口)

````
IOC思想基于IOC容器完成,IOC容器底层就算对象工厂
Spring提供IOC容器实现方式:(两个接口)
	1)BeanFactory:IOC容器基本实现,是Spring中内部的使用接口,不提供开发人员使用
		*加载配置文件时不会创建对象,在获取对象(使用对象时)才会创建对象
	2)AplicationContext:BeabFactory接口的子接口,提供更多更强大的功能,一般由开发人员进行使用
		*加载配置文件时就会把配置文件对象进行创建
	3)ApplicationContext接口有实现类
````

#### IOC操作Bean管理

```
什么是Bean管理:
	Spring创建对象
	Spring属性注入
	
Bean管理操作有两种方式:
	基于xml配置文件方式实现
		
	基于注解方式实现
		1)DI:依赖注入,注入属性
			*使用set方式注入
			*使用有参构造注入



<!--set方法注入属性-->
<bean id="book" class="com.spring5.Book">
    <property name="bname" value="西游记"></property>
	<property name="bauther" value="无尘嗯"></property>
</bean>

<!--设置属性null值-->
<property name="address">
	<null></null>
</property>

<!--向属性中设置特殊符号-->
<property name="address">
	<value> <![CDATA[<<南京 >>]]> </value>
</property>

<!--构造方法注入-->
<bean id="orders" class="com.spring5.Orders">
	<constructor-arg index="0" value="冰激凌"/>
	<constructor-arg index="1" value="青青草原"/>
</bean>

<!--构造方法注入-->
<bean id="orders" class="com.spring5.Orders">
	<constructor-arg name="oname" value="冰激凌"/>
	<constructor-arg name="address" value="青青草原"/>
</bean>

<!--内部bean-->
    <bean id="emp" class="com.spring5.bean.Emp">
        <property name="ename" value="张三"></property>
        <property name="gender" value="男"></property>
        <property name="dept">
            <bean id="dept" class="com.spring5.bean.Dept">
                <property name="dname" value="测试部"></property>
            </bean>
        </property>
    </bean>
    
<!--外部bean-->
    <bean id="userService" class="com.spring5.service.UserService">
        <!--注入userDao对象-->
        <property name="userDao" ref="userDao"></property>
    </bean>
    <bean id="userDao" class="com.spring5.dao.UserDaoImpl"></bean>
    
<!--级联赋值-->
    <bean id="emp" class="com.spring5.bean.Emp">
        <property name="ename" value="张三"></property>
        <property name="gender" value="男"></property>
        <!--需要生成dept的get方法-->
        <property name="dept.dname" value="技术部"></property>
    </bean>
```



```
bean的作用域
在Spring里面,创建bean实例默认是单实例
	通过设置scope的值来设置(singleton单实例 prototype多实例)
		设置scope值是singleton时,加载Spring配置文件时就会创建实例对象
		设置scope值是prototype时,调用getBean方法时才创建实例对象
		
bean的生命周期
第一步 执行无参构造,创建bean实例
第二步 调用set方法设置值
*把bean实例传递bean后置处理器的方法
第三步 执行初始化的方法
*把bean实例传递bean后置处理器的方法
第四步 获取创建bean实例对象
第五步 执行销毁的方法
```

```
xml自动装配
什么时自动装配
	根据指定装配规则(属性名称或属性类型),Spring自动将匹配的属性值进行注入
	
装配方法
 <!--实现自动装配
        bean标签属性autowire,配置自动装配
        autowire属性常用两个值:
        byName根据属性名注入 ,注入值bean的id值和类属性名称要一样
        byType根据属性类型注入
    -->
```



#### IOC底层原理

```
xml解析,工厂模式,反射 
```

#### IOC接口(BeanFactory)

```
Spring有两种类型bean,一种普通bean,另外一种工厂bean(FactoryBean)
	普通bean:
		在配置文件中定义什么类型就只能返回什么类型
	工厂bean:
		在配置文件定义bean类型可以和返回类型不一样
```

#### IOC操作Bean管理(基于xml)

```
外部属性文件
1)直接配置数据库信息
	配置连接池
	<!--直接配置连接池-->
    <bean id="dataSource" class="com.alibaba.druid.pool.DruidDataSource">
        <property name="driverClassName" value="com.mysql.jdbc.Driver"></property>
        <property name="url" value="jdbc:mysql://localhost:3306/test"></property>
        <property name="username" value="root"></property>
        <property name="password" value="huang1218"></property>
    </bean>
    
2)引入外部属性文件配置
	*引入context命名空间 xmlns:context="http://www.springframework.org/schema/context"
	<!--jdbc.properties-->
	prop.driverClass=com.mysql.jdbc.Driver
	prop.url=jdbc:mysql://localhost:3306/test
	prop.username=root
	prop.password=huang1218
	    <!--bean.xml配置文件中引入外部属性文件-->
    <context:property-placeholder location="classpath:jdbc.properties"/>
    <bean id="dataSource" class="com.alibaba.druid.pool.DruidDataSource">
        <property name="driverClassName" value="${prop.driverClass}"></property>
        <property name="url" value="${prop.url}"></property>
        <property name="username" value="${prop.username}"></property>
        <property name="password" value="${prop.password}"></property>
    </bean>
```



#### IOC操作Bean管理(基于注解)

```
基于注解方式
Spring针对Bean管理中创建对象提供注解
1)@Component:基本注解,标识了一个受Spring管理的组件
2)@Service:标识业务层组件
3)Controller:标识表现层组件
4)@Repository:标识持久层组件
*上面四个注解功能都是一样的,都是用来创建bean实例

基于注解方式实现对象创建
```

### AOP

```
切面(Aspect):横切关注点(跨域应用程序多个模块功能)被模块化的特殊对象
通知(Advice):切面必须要完成的工作
目标(Target):被通知的对象
代理(Proxy):向目标对象应用通知之后创建的对象
连接点(Joinpoint):程序执行的某个特定位置
切点(pointcut):每个类都拥有多个连接点
```

```
加入jar包
aopalliance-1.0.jar
aspectjweaver-1.9.5.jar
spring-aop-5.2.6.RELEASE.jar
spring-aspects-5.2.6.RELEASE.jar

在配置文件中加入aop的命名空间
http://www.springframework.org/schema/aop https://www.springframework.org/schema/aop/spring-aop.xsd

在配置文件中加入如下配置
<!--AspectJ注解支持-->
<aop:aspectj-autoproxy></aop:aspectj-autoproxy>

把横切关注点的代码抽象到切面的类中
	1)切面首先是一个IOC中的bean,即加入@Component注解
	2)切面还需要加入@Aspect注解
	3)在类中添加通知注解
	
@Order(number)注解改变切面的优先级,值越小优先级越高
```

```
xml方式配置aop

    <bean id="arithmeticCalculator" class="com.spring5.aops.ArithmeticCalculatorImpl"></bean>
    <!--配置切面bean-->
    <bean id="loggingAspect" class="com.spring5.aops.LoggingAspect"></bean>
    
    <!--配置aop-->
    <aop:config>
        <!--配置切点表达式-->
        <aop:pointcut id="pointcut" expression="execution(* com.spring5.aops.ArithmeticCalculator.*(..))"/>
        <!--配置切面及通知-->
        <aop:aspect ref="loggingAspect" order="2">
            <aop:before method="beforeMethod" pointcut-ref="pointcut"></aop:before>
        </aop:aspect>
    </aop:config>
```

### Spring事务

```
<!--配置事务管理器-->
    <bean id="transactionManager" class="org.springframework.jdbc.datasource.DataSourceTransactionManager">
        <property name="dataSource" ref="dataSource"></property>
    </bean>
<!--使注解生效-->
    <tx:annotation-driven transaction-manager="transactionManager"/>
    
添加事务注解
使用propagation指定事务的传播行为(REQUITRE,REQUIRES_NEW)
使用isolation指定事务的隔离级别
```

### Spring在WEB中的应用

```
Spring如何在web应用中使用
	1)需要额外的jar包(spring-webmvc-5.2.6.RELEASE.jar spring-web-5.2.6.RELEASE.jar)
	2)spring的配置文件,与之相同
	3)如何创建IOC容器
		非web应用在main方法中直接创建
		web应用应该在web应用被服务器加载时就创建IOC容器:(ServletContextListener#contextInitialized(ServletContextEvent sce))方法中创建IOC容器
		web应用的其他组件中如何来访问IOC容器:创建IOC容器后,将其放在ServletContext(application域)的一个属性中
```





