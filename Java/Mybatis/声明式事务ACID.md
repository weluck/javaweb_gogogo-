## 在Spring 的配置文件中创建一个 DataSourceTransactionManager 对象：
```xml
<bean id="transactionManager" class="org.springframework.jdbc.datasource.DataSourceTransactionManager">
  <constructor-arg ref="dataSource" />
</bean>
```

## 利用AOP实现事务的织入
1. 配置事务通知
```xml
  <tx:advice id="txAdvice" transaction-manager="transactionManager">
    <!--给方法配置事务-->
    <tx:attributers>
      <tx:method name="select"/>
      <tx:method name=""delete/>
    </tx:attributes>
  </tx:advice>
```

2. 配置事务切入
```xml
<aop:config>
  <aop:pointcut id="txPointCUt" expression="excution(* cn.ncu.weluck.naooer.*.*.*(..))"/>
  <aop:adivisor advice-ref="txAdvice" pointcut-ref="txPointCut"/>
</aop:config>
```
