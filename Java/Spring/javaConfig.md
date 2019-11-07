创建一个java类实现配置文件<br>
```java
@COnfiguration   //代表这是一个配置类
@ComponentScan("cn.ncu.weluck")
@Import(confg2.class)  //引入别的配置类
public class WeluckConfig {
  @Bean   //注册一个bean, 方法名为id属性,返回值为class属性
  public User user() {
    return new User();
}
```
```java
ApplicationContext context = new AnnotationConfigApplicationContext(WeluckConfig.class)
User getUser = context.getBean("User", User.class);
```
