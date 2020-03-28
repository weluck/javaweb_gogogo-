## 5、 Eureka服务注册与发现

### 5.1、什么是Eureka

* Eureka: 怎么读?
* Netflix 在设计Eureka时，遵循的就是AP原则
* Eureka是Netflix的一个子模块，也是核心模块之一- 。Eureka是一 个基于REST的服务，用于定位服务,以实现云端中间层服务发现和故障转移,服务注册与发现对于微服务来说是非常重要的，有了服务发现与注册，只需要使用服务的标识符，就可以访问到服务,而不需要修改服务调用的配置文件了，功能类似于Dubbo的注册中心，比如Zookeeper;

## 5.2、原理讲解

* Eureka的基本架构
  * SpringCloud 封装了NetFlix公司开发的Eureka模块来实现服务注册和发现(对比Zookeeper)
  * Eureka采用 了C-S的架构设计，EurekaServer 作为服务注册功能的服务器，他是服务注册中心
  * 而系统中的其他微服务。使用Eureka的客户端连接到EurekaServer并维持心跳连接。这样系统的维护人员就可以通过EurekaServer来监控系统中各个微服务是否正常运行，SpringCloud的一 些其他模块(比如Zuul)就可以通过EurekaServer来发现系统中的其他微服务，并执行相关的逻辑;
* 和Dubbo架构对比
  * Eureka包含两个组件: Eureka Server和Eureka Client。
  * Eureka Server提供服务注册服务，各个节点启动后，会在EurekaServer中进行注册， 这样Eureka Server中的服务注册表中将会村粗所有可用服务节点的信息,服务节点的信息可以在界面中直观的看到。
  * Eureka Client是-个Java客户端， 用于简化EurekaServer的交互， 客户端同时也具备一 一个内置的，使用轮
    询负载算法的负载均衡器。在应用启动后，将会向EurekaServer发送心跳(默认周期为30秒)。如果Eureka Server在多个心跳周期内没有接收到某个节点的心跳，EurekaServer将会从服务注册表中把这个服务节点移除掉(默认周期为90秒)

* 三大角色
  * Eureka Server: 提供服务的注册于发现。zookeeper
  * Service Provider: 将自身服务注册到Eureka中，从而使消费方能够找到。
  * Service Consumer: 服务消费方从Eureka中获取注册服务列表,从而找到消费服务。
