```java
public class MybatisUtils {
  private static SqlSessionFactory sqlSessionFactory;
  
  static{
     try {
        String resource = "mybatis-config.xml";
        InputStream inputStream = Resources.getResourceAsStream(resource);
        sqlSessionFactory = new SqlSessionFactoryBuilder().build(inputStream);
     } catch (IOException e) {
        e.printStackTrace();
     }
}

  public static SqlSession getSqlSession(){
        return sqlSessionFactory.openSession();
  }
}
```
