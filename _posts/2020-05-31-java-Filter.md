---
title: Filter
tags: Java
article_header:
  type: cover
  image:
    src: /screenshot.jpg
---



### Filter

#### filter是什么

```
filter过滤器是javaWeb三大组件之一,分别是Servlet程序,Listener监听器,Filter过滤器
filter是javaEE的规范,也就是接口
filter过滤器的作用是:拦截请求,过滤响应
```

步骤

```
//实现Filter接口
public class AdminFilter implements Filter {

    @Override
    public void init(FilterConfig filterConfig) throws ServletException {

    }

    @Override
    public void doFilter(ServletRequest servletRequest, ServletResponse servletResponse, FilterChain filterChain) throws IOException, ServletException {
        HttpServletRequest httpServletRequest = (HttpServletRequest) servletRequest;
        Object user = httpServletRequest.getSession().getAttribute("user");
        if(user == null) {
            httpServletRequest.getRequestDispatcher("/login.jsp").forward(servletRequest, servletResponse);
            return;
        }else{
            filterChain.doFilter(servletRequest, servletResponse);
        }
    }

    @Override
    public void destroy() {

    }
}

```

配置web.xml

```
    <filter>
    	//别名
        <filter-name>AdminFilter</filter-name>
        //全类名
        <filter-class>com.filter.AdminFilter</filter-class>
    </filter>
    <filter-mapping>
    	//当前的拦截路径给哪个filter使用
        <filter-name>AdminFilter</filter-name>
        //过滤地址
        <url-pattern>/admin/*</url-pattern>
    </filter-mapping>
```

### FilterConfig

```
作用:
	获取Filter的名称 filter-name的内容
	获取Filter中配置的init-param的初始化参数
	获取ServletContext对象
```

####  FilterChain过滤器链

```
FilterChain.doFilter():
	执行下一个Filter过滤器
	执行目标资源
```



![image-20200531164616854](E:\Project\jiang565745499.github.io\_posts\images\批注 2020-05-31 164607.png)

```
在多个Filter过滤器中,执行顺序是按照web.xml中的配置顺序从上到下决定

Filter的拦截路径
	精确匹配
	目录匹配
	后缀名匹配	
```

