# prometheus-noBug
- 引入pom
  - 如果提示版本不明确，需确定当期springboot对应版本号
```xml
<dependencies>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-actuator</artifactId>
    </dependency>
    
    <dependency>
        <groupId>io.micrometer</groupId>
        <artifactId>micrometer-registry-prometheus</artifactId>
    </dependency>
</dependencies>

```
- 添加配置文件yml
```yaml
management:
  endpoints:
    web:
      exposure:
        include: health,info,prometheus
  metrics:
    tags:
      application: ${spring.application.name}
```
- 常见问题解决
  - [fastjson序列化导致prometheus返回监控数据格式错乱](https://www.cnblogs.com/yechen2019/p/14505024.html)
  - [全局JSON序列化导致prometheus数据格式错乱](https://blog.csdn.net/niugang0920/article/details/128101186)
  - [ES问题解决：Elasticsearch health check failed](https://blog.csdn.net/CharlesYooSky/article/details/90405699?spm=1001.2101.3001.6661.1&utm_medium=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-90405699-blog-123799142.pc_relevant_default&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-2%7Edefault%7ECTRLIST%7ERate-1-90405699-blog-123799142.pc_relevant_default&utm_relevant_index=1)