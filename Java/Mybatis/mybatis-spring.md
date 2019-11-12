## 使用spring的数据源并通过spring获取sqlSessionFactory,然后创建SqlSessionTemplate
```java 
  <bean id="datasource" class="org.springframework.jdbc.datasourve.DriverManagerDataSource">
    <property name="driverClassName" value="com.mysql.jdbc.Driver"/>
    <property name="url" value="jdbc:mysql://localhost:33036/mybatis?useSSL=ture&amp;useUnicode=true&amp;characterEncoding=UTF-8"/>
    <property name="username" value=""/>
    <property name="password" value=""/>
  </bean>
  
  <bean id="sqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean">
    <property name="dataLacation" ref="dataSource"/>
    <property name="configuration" value="classpath:mybatis-config.xml"/>
    <property name=""mapperlocations" value"classpath:cn/ncu/weluck/mapper/UserMapper.xml"
  </bean>
  
  <bean id="sqlSession" class="org.mybatis.spring.SqlSessionTemplate">
    <constructor-arg index="0" ref="sqlSessionFactory"/>  
  </bean>
```
