```java
@Configuration
public class RedisConfig {

    @Bean
    @SuppressWarnings("all")
    public RedisTemplate<String, Object> redisTemplate(RedisConnectionFactory factory) {
        // 开发一般直接使用<String, object>
        RedisTemplate<String, Object> template = new RedisTemplate<>();
        template.setConnectionFactory(factory);

        // Json序列化配置
        Jackson2JsonRedisSerializer jackson2JsonRedisSerializer = new Jackson2JsonRedisSerializer(Object.class);
        ObjectMapper om = new ObjectMapper();
        om.setVisibility(PropertyAccessor.ALL, JsonAutoDetect.Visibility.ANY);
        om.enableDefaultTyping(ObjectMapper.DefaultTyping.NON_FINAL);
        jackson2JsonRedisSerializer.setObjectMapper(om);
        // String序列化
        StringRedisSerializer stringRedisSerializer = new StringRedisSerializer();

        // key采用Sting的序列化方式
        template.setKeySerializer(stringRedisSerializer);
        // hash采用Sting的序列化方式
        template.setHashKeySerializer(stringRedisSerializer);
        // value采用Sting的序列化方式
        template.setValueSerializer(jackson2JsonRedisSerializer);
        // hash的value采用Sting的序列化方式
        template.setHashValueSerializer(jackson2JsonRedisSerializer);
        template.afterPropertiesSet();

        return template;
    }
}
```
