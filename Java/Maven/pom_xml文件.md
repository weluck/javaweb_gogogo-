（一）第一行是xml头，指定了xml文档的版本信息和编码方式，目前version的默认版本号为 1.0  编码方式为 UTF-8。

（二）<project>为所有pom.xml的根元素，声明了一些POM相关的命名空间及xsd元素，这些元素不是pom.xml中必须添加的，但是使用这些属性可以使第三方工具，如IDE中的xml编辑器帮助开发者快速编辑POM。

（三）根元素下第一个子元素 <modeVersion> 指定了当前POM模板的版本，对于现在大多数开发者而言，Maven 2  Maven 3 

这个版本号只能为4.0.0。

（四）<groupId> 定义了该项目属于哪个项目组，在企业级开发中，通常和该项目所属的组织和公司有关。比如：BATcode上有一个名为ourApp的项目，这样一来groupId的名字就应该是com.BATcode.ourApp。本文中的代码都为com.feiyu.helloMaven。

（五）<artifactId>定义了当前Maven项目在项目组的唯一一个ID，本文中 Hello Maven artifactId为hello-Maven，在实际开发中会分配其他的 artifactId ，而之前的 groupId ，可能会为不同的子项目（模块）分配artifactId。

（六）<version>定义了Hello Maven项目当前的版本号 1.0-SNAPSHOT 为IDEA默认的初始版本号，随着项目的开发进度，版本号升级为1.1 、2.0 等。

（七）在没有实际的java代码时，我们就可以完整的创建一个Maven项目的pom.xml，这说明了Maven可以使项目对象模型最大程度的与代码相独立，这充分体现了解耦的原则和理念！为开发者节省了时间，大大缩短了项目开发周期。在项目开发到稳定期时，升级版本时，开发者可以不需要修改实际的 java 代码，而是只修改pom.xml，这一特点使Maven被广泛的使用。

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
 
    <groupId>com.feiyu.web</groupId>
    <artifactId>hello-world</artifactId>
    <version>1.0-SNAPSHOT</version>
 
</project>
```
