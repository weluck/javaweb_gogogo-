1. 在resource中添加log4j.properties
2. 在mybatis-config.xml中配置log4j为日志的实现
```xml
<settings>
  <setting name="logImpl" value="LOG4J"/>
</setting>
```
