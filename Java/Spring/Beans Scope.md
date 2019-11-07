单例模式，也是默认模式
```xml
<bean id="accountService" class="com.something.DefaultAccountService" scope="singleton"/>
```

原型模式，多例模式
```xml
<bean id="accountService" class="com.something.DefaultAccountService" scope="prototype"/>
```
