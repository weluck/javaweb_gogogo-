## 引入Spring beans
```
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://www.springframework.org/schema/beans
        https://www.springframework.org/schema/beans/spring-beans.xsd">

    <!-- services -->

    <bean id="petStore" class="org.springframework.samples.jpetstore.services.PetStoreServiceImpl" name="alias1, alias2">
        <property name="accountDao" ref="accountDao"/>
        <property name="itemDao" ref="itemDao"/>
        <!-- additional collaborators and configuration for this bean go here -->
    </bean>

    <!-- more bean definitions for services go here -->

</beans>
```
id为唯一标识，class传输入容器的类，<property/>为类的属性赋值，res:引用Spring容器中创建好的对象，value:传入基本数据类型。name可取别名<br>
配置文件加载时，容器中管理对象已经初始化

## 有参构造函数实现
```xml
<bean id="exampleBean" class="examples.ExampleBean">
    <!-- constructor injection using the nested ref element -->
    <constructor-arg type="int" value="7500000"/>
    <constructor-arg type="java.lang.String" value="42"/>
    
    <constructor-arg index="0" value="7500000"/>
    <constructor-arg index="1" value="42"/>
    
    <constructor-arg name="name" value="盖伦"/>
</bean>
```
name为参数名
