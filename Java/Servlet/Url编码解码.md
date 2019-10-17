作用：参数种包含特殊字符或空格引起歧义使服务器端报错。<br>
```java
String str1 = "编码  #￥%……&*（";
str1 = URLEncoder.encode(str1, "UTF-8"); //编码
str1 = URLDecoder.decode(str1, "UTF-8"); //解码
```
