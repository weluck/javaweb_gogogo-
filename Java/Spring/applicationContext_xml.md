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

## import
```xml
<import resource="beans.xml"/>
<import resource="lol.xml"/>
```
导入其他配置文件

## Dependency Injection
### p、c命名空间注入
```xml
<beans>
  <!--p命名空间注入,可以直接注入属性的值: property-->
  <bean id="user" class="cn.ncu.weluck.pojo.User" p:name="moumou" p:age="18"/>

  <!--c命名空间注入,通过构造器注入: construt-args-->
  <bean id="user2" class="cn.ncu.weluck.pojo.User" c:name="moumou" c:age="18"/>
<beans/>
```
### collection
```xml
<bean id="moreComplexObject" class="example.ComplexObject">
    <!-- results in a setAdminEmails(java.util.Properties) call -->
    <property name="adminEmails">
        <props>
            <prop key="administrator">administrator@example.org</prop>
            <prop key="support">support@example.org</prop>
            <prop key="development">development@example.org</prop>
        </props>
    </property>
    <!-- results in a setSomeList(java.util.List) call -->
    <property name="someList">
        <list>
            <value>a list element followed by a reference</value>
            <ref bean="myDataSource" />
        </list>
    </property>
    <!-- results in a setSomeMap(java.util.Map) call -->
    <property name="someMap">
        <map>
            <entry key="an entry" value="just some string"/>
            <entry key ="a ref" value-ref="myDataSource"/>
        </map>
    </property>
    <!-- results in a setSomeSet(java.util.Set) call -->
    <property name="someSet">
        <set>
            <value>just some string</value>
            <ref bean="myDataSource" />
        </set>
    </property>
</bean>
```
