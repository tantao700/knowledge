# Javamelody
```bash
<!--应用监控-->
<filter>
    <filter-name>javamelody</filter-name>
    <filter-class>net.bull.javamelody.MonitoringFilter</filter-class>
    <async-supported>true</async-supported>
    <init-param>
        <param-name>authorized-users</param-name>
        <param-value>username:password,username2:password2</param-value>
    </init-param>
</filter>
<filter-mapping>
    <filter-name>javamelody</filter-name>
    <url-pattern>/*</url-pattern>
    <dispatcher>REQUEST</dispatcher>
    <dispatcher>ASYNC</dispatcher>
</filter-mapping>
```    
