在web.xml的`<web-app> </web-app>`中配置
```java
    <servlet>
        <servlet-name>demo1</servlet-name>
        <servlet-class>cn.itcast.web.servlet.ServletDemo1</servlet-class>
    </servlet>
    
    <servlet-mapping>
        <servlet-name>demo1</servlet-name>
        <url-pattern>/demo1</url-pattern>
    </servlet-mapping>
```

Servlet 3.0: <br>
利用注解配置：
`@WebServlet("资源路径")`

可在web文件下添加资源文件，浏览器可访问
