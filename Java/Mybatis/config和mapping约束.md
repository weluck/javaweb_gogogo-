config约束：
-----------
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE configuration  
  PUBLIC "-//mybatis.org//DTD Config 3.0//EN"  
  "http://mybatis.org/dtd/mybatis-3-config.dtd">
```
Mapping约束:
--------------
```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE mapper  
  PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"  
  "http://mybatis.org/dtd/mybatis-3-mapper.dtd">

```
1. 一般这个config的配置文件的约束的名字叫做：SQLMapConfig.xml(在resources中)
2. Mapper的配置文件约束是在resources中与其main中java下接口的相应文件相对应，但是简单来书，main中文件夹是包属性例如：comgaoxin.dao，属于三级结构，但是在resources中目录属于一级结构，需注意。
