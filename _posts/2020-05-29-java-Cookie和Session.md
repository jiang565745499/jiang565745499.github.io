---
title: Cookie和Session
tags: Java
article_header:
  type: cover
  image:
    src: /screenshot.jpg
---

### Cookie

```
Cookie是servlet发送到浏览器的少量信息,这些信息由浏览器保存,然后发送回服务器,是服务器通知客户端保存键值对信息的一种技术.
//创建cookie
Cookie cookie = new Cookie("key1","value1");
response.addCookie(cookie);

//获取Cookie
Cookie[] cookies = req.getCookies();

//设置Cookie的值
cookie1.setValue("newValue"); 或者 Cookie cookie = new Cookie("key1","value1");创建一个新value替换
```

#### Cookie生命控制

```
setMaxAge() 默认值-1
正数:设置cookie过期的最大生命时间
负数:将在web浏览器关闭后自动删除
0:马上删除
```

#### Cookie有效路径Path的设置

```
Cookie的path属性可以有效的过滤哪些Cookie可以发给服务器.path属性是通过请求的地址来进行有效的过滤
```



### Session

```
session是一个接口(Httpsession),用来维护一个客户端和服务器之间关联的一种技术.每个客户端都有一个自己的Session会话,session会话中,经常用来保存用户登录之后的信息
```

#### session的创建和获取

```
request.getSession()
	第一次调用:创建Session会话
	之后调用:获取前面创建好的Session会话对象
isNew() 
	判断Session是不是刚创建
getId()
	每一次会话都有一个唯一的I值
	
//session的存值
req.getSession().setAttribute("key1","value1");
//session的取值
req.getSession().getAttribute("key1");
```

#### session的生命周期

```
//TOmcat服务器的配置文件web.xml 中设置的默认超时时间30分钟
  <session-config>
    <session-timeout>30</session-timeout>
  </session-config>
//获取session的超时时间 (默认为1800秒)
req.getSession().getMaxInactiveInterval();

//设置session的超时时间 负数表示永不超时(极少使用)
HttpSession session = req.getSession();
session.setMaxInactiveInterval(3);

//让当前session会话马上无效
session.invalidate();
```

```
服务器每次请求session会话的时候,都会创建一个Cookie对象.这个Cookie对象的key永远是:JSESSIONID=6EC885578EB39F77D7216034A7E3B2FF,其中JSESSIONID的值是创建出来的Session值id 
```

![客户端和Session](images\image-20200531082724494.png)