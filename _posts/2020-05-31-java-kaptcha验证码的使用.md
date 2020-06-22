---
title: kaptcha
tags: Java
article_header:
  type: cover
  image:
    src: /screenshot.jpg
---







需要的jar包:

​	kaptcha-2.3.2.jar

​	filters-2.0.235-1.jar

web.xml中需要添加的配置

```
<servlet>
    <servlet-name>KaptchaServlet</servlet-name>
    <servlet-class>com.google.code.kaptcha.servlet.KaptchaServlet</servlet-class>
</servlet>
<servlet-mapping>
    <servlet-name>KaptchaServlet</servlet-name>
    <url-pattern>/kaptcha.jpg</url-pattern>
</servlet-mapping>
```

表单中添加验证码

```
 验证码:<input type="text" name="code"><img src="http://localhost:8080/tmp/kaptcha.jpg" alt="">
```

验证码验证

```
//获取用户输入的验证码
        String code = req.getParameter("code");
        //获取图片的验证码
        String token = (String) req.getSession().getAttribute(KAPTCHA_SESSION_KEY);
        //获取完后立马删除
        req.getSession().removeAttribute(KAPTCHA_SESSION_KEY);
        if(token!=null && token.equalsIgnoreCase(code)){
            System.out.println("保存到数据库:"+username);
            resp.sendRedirect(req.getContextPath()+"/ok.jsp");
        }else{
            System.out.println("请不要重复提交表单");
        }
```

验证码的点击切换

```
<script type="text/javascript">
  var btn = document.getElementById("code_img");
  btn.onclick = function () {
    this.src = "http://localhost:8080/tmp/kaptcha.jpg";
  }
</script>
```

