分类:
## 静态代理
* 抽象角色:一般会使用接口或者抽象类解决
```java
public interface Rent {
  public void rent();
}
```
* 真实角色:被代理的角色
```java
public class Host implements Rent {
  public void rent() {
    System.out.println("房东要出租房子");
```
* 代理角色:代理真实角色,一般会做些附属操作
```java
public class Proxy implements Rent {
  private Host host;
  
  public Proxy{}
  public Proxy(Host host){
       this.host = host;
  }
  public void rent(){
      seeHouse();
      host.rent();
      hetong();
      fare();
  }
}
```
* 客户：访问代理对象的人
```java
public static void main(){}
```
好处:
* 可以使真实角色的操作更加纯粹！不用去关注一些公共的业务
* 公共也就交给代理角色！实现了业务的分工！
* 公共业务发生扩展的时候, 方便集中管理<br>
缺点:
* 一个真实角色会产生一个代理角色：开发效率变低

## 动态代理
* 动态代理和静态代理角色一样
* 动态代理的的代理类是动态生成的
* 动态代理分为两大类：基于接口的动态代理，基于类的动态代理
  * 基于接口--JDK动态代理
  * 基于类: cglib
  * java字节码实现： javasist
![](https://github.com/weluck/javaweb_gogogo-/blob/master/Java/Spring/%E5%9B%BE%E7%89%87/2YTWIE\)4H%60H730%24%7D%7B%245E16B.png)
