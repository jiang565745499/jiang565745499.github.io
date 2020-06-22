---
title: SpringMVC
tags: Java
article_header:
  type: cover
  image:
    src: /screenshot.jpg
---



# SpringMVC

#### SpringMVC的搭建过程

```
1)导入jar包
2)在web.xml中配置springMVC的核心(前端)控制器DispatcherServlet
	作用:加载springMVC的配置文件,在下方的配置方式下,dispatcherServlet自动加载配置文件,此时的配置文件有默认的位置和名称,默认位置:WEB-INF下,默认名称<servlet-name>-servlet.xml
	<!--springmvc核心配置-->
    <servlet>
        <servlet-name>springMVC</servlet-name>
        <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
        <init-param>
            <param-name>contextConfigLocation</param-name>
            <param-value>WEB-INF/springMVC-servlet.xml</param-value>
        </init-param>
    </servlet>
    <servlet-mapping>
        <servlet-name>springMVC</servlet-name>
        <!--
            url-pattern有三种方式:/ /* *.action
        -->
        <url-pattern>/</url-pattern>
    </servlet-mapping>
    
3)springMVC-servlet.xml配置
	<!--扫描组件-->
    <p:component-scan base-package="com.controller"></p:component-scan>

    <!--配置内部资源视图解析器-->
    <bean id="viewResolver" class="org.springframework.web.servlet.view.InternalResourceViewResolver">
        <property name="prefix" value="/WEB-INF/view"></property>
        <property name="suffix" value=".jsp"></property>
    </bean>
```



HiddenHttpMethodFilter

会根据几个条件对POST请求作出转换

条件:

- POST
- 参数_method,若不符合条件--->post,若符合条件,经过转换之后真正的请求方式是( _method)的值

```
//web.xml配置
<filter>
        <filter-name>HiddenHttpMethodFilter</filter-name>
        <filter-class>org.springframework.web.filter.HiddenHttpMethodFilter</filter-class>
    </filter>
    <filter-mapping>
        <filter-name>HiddenHttpMethodFilter</filter-name>
        <url-pattern>/*</url-pattern>
    </filter-mapping>
```



#### 向作用域中传值的三种方式

```
   //第一种
   @RequestMapping(value = "/param",
            method = RequestMethod.POST
    )
    public String param(User user, Map<String,Object> map) {
        map.put("username",user.getUsername());
        return "ok";
    }
    
    //第二种
    @RequestMapping(value = "/param",
            method = RequestMethod.POST
    )
    public String param(User user,Model model) {
        model.addAttribute("username",user.getUsername());
        return "ok";
    }
    
    //第三种(标准)
    @RequestMapping(value = "/param",
            method = RequestMethod.POST
    )
    public ModelAndView param2(User user) throws IOException {
        ModelAndView modelAndView = new ModelAndView();
        //往域中放值
        modelAndView.addObject("username","root");
        //设置视图名称,实现页面跳转
        modelAndView.setViewName("ok");
        return modelAndView;
    }
```

#### 编码过滤器

```
<filter>
        <filter-name>CharacterEncodingFilter</filter-name>
        <filter-class>org.springframework.web.filter.CharacterEncodingFilter</filter-class>
        <init-param>
            <param-name>encoding</param-name>
            <param-value>UTF-8</param-value>
        </init-param>
    </filter>
    <filter-mapping>
        <filter-name>CharacterEncodingFilter</filter-name>
        <url-pattern>/*</url-pattern>
    </filter-mapping>
```

#### 过滤静态资源

```
配置Tomcat中默认的servlet,DefaultServlet
在springmvc.xml中添加
<mvc:default-servlet-handler/>
<mvc:annotation-driven/>
    <!-- 静态资源处理  css js imgs -->
    <mvc:resources location="/css/" mapping="/css/**"/>
    <mvc:resources location="/imgs/" mapping="/imgs/**" />
```

#### 处理JSON

```
json的两种格式:
	json对象:{key:value,key1:value1}
	json数组:[value1,value2]
json对象解析方式:对象.key;
json数组的解析方式:for循环遍历
java对象转换json
	Bean和map--->json对象
	List--->json数组

步骤
	1)导入jar包jackson-annotations-2.11.0.jar
			  jackson-databind-2.11.0.jar
			  jackson-core-2.11.0.jar
	2)在springMVC的配置文件中开启mvc驱动<mvc:annotation-driven>
	3)在方法上加上@ResponseBody注解
	4)将要转换为json且响应到客户端的数据,直接作为该方法的返回值
```

#### HttpMessageConverter

```
DispatcherServlet默认装配RequestMappingHandlerAdapter,而RequestMappingHandlerAdapter默认装配HttpMessageConverter
作用:将请求信息转化并绑定到处理方法的入参或将响应结果转为对应类型的响应信息,spring提供了两种途径:
	1)使用@ResponseBody或@RequestBody对处理方法添加注解
	2)使用HttpEntity<T>或ResponseEntity<T>作为处理方法的入参或返回值
```

#### 文件下载

```
@RequestMapping("/down")
    public ResponseEntity<byte[]> down(HttpSession session) {
        //获取下载文件的路径
        String realPath = session.getServletContext().getRealPath("static/images");
        String finalPath = realPath + File.separator + "img.jpg";
        InputStream is = null;
        ResponseEntity<byte[]> entity = null;
        try {
            is = new FileInputStream(finalPath);
            //available() 获取输入流所读取的文件的最大字节数
            byte[] b = new byte[is.available()];
            is.read(b);
            //设置请求头
            HttpHeaders headers = new HttpHeaders();
            headers.add("Content-Disposition","attachment;filename=img.jpg");
            //设置响应状态码
            HttpStatus status = HttpStatus.OK;
            entity = new ResponseEntity<byte[]>(b,headers,status);
        } catch (FileNotFoundException e) {
            e.printStackTrace();
        } catch (IOException e) {
            e.printStackTrace();
        }finally{
            if(is!=null){
                try {
                    is.close();
                } catch (IOException e) {
                    e.printStackTrace();
                }
            }
        }
        return entity;
    }
```

#### 文件上传

```
   //springmvc.xml文件配置
   <!--
        处理文件,将客户端上传的File文件处理为MultipartFile
        注意:id名必须为multipartResolver
    -->
    <bean id="multipartResolver" class="org.springframework.web.multipart.commons.CommonsMultipartResolver">
        <!--设置文件解析的编码,注意:一定要和页面的pageEncoding保持一致-->
        <property name="defaultEncoding" value="UTF-8"></property>
        <!--设置文件的最大上传限制-->
        <property name="maxUploadSize" value="9999999"></property>
    </bean>
    
   @RequestMapping(value = "/upload",method = RequestMethod.POST)
    public String upload(String desc, MultipartFile uploadFile,HttpSession session) throws Exception {
        //获取上传文件的名称
        String originalFilename = uploadFile.getOriginalFilename();
        //解决文件重名的问题
        String finalFileName = UUID.randomUUID()+originalFilename+originalFilename.substring(originalFilename.lastIndexOf("."));
        //获取服务器下项目的路径
        String path = session.getServletContext().getRealPath("/static/temp")+File.separator+finalFileName;
        File file = new File(path);
        uploadFile.transferTo(file);
        return "success";
    }
```

#### 拦截器

```
   //springMVC.xml配置文件中
   <!--配置拦截器-->
    <mvc:interceptors>
        <!--默认拦截所有请求-->
        <bean class="com.interceptor.FirstInterceptor"></bean>
        <!--此方式要求拦截器类上必须加注解@Component-->
        <ref bean="firstInterceptor"></ref>
        <!--设置自定义拦截
        <mvc:interceptor>
            <bean class="com.interceptor.FirstInterceptor"></bean>
            <mvc:mapping path=""/>
            <mvc:exclude-mapping path=""/>
        </mvc:interceptor>-->
    </mvc:interceptors>
```

#### 异常处理DefaultHandlerExceptionResolver

```
    <bean class="org.springframework.web.servlet.handler.SimpleMappingExceptionResolver">
        <property name="exceptionMappings">
            <props>
            	<!--key为对应的异常所属类--> error 为跳转页面
                <prop key="java.lang.ArithmeticException">error</prop>
            </props>
        </property>
    </bean>
```

![image-20200610180117358](E:\Project\jiang565745499.github.io\_posts\images\image-20200610180117358.png)

#### Spring和SpringMVC的关系

```
spring是父容器,springMVC是子容器
子容器能够调用访问父容器中的bean,而父容器不能调用访问子容器中的bean
```

