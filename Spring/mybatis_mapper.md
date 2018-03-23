# mybatis

mybatis를 maven project에서 사용하려면 mybatis-x.x.x.jar 파일을 추가해야 함
```xml
<dependency>
  <groupId>org.mybatis</groupId>
  <artifactId>mybatis</artifactId>
  <version>x.x.x</version>
</dependency>
```
## sqlSessionFactory 빌드
mybatis 어플리케이션은 sqlSessionFactory 인스턴스를 사용한다.

```java
// config에 환경설정 정의
public static class MybatisConfig {
    public static final String MYBATIS_CONFIG_LOCATION = "classpath:mybatis-config.xml";
    public static final String MAPPER_LOCATION_PATTERN = "classpath:com/amp/*.xml";
}

SqlSessionFactoryBean sqlSessionFactory = new SqlSessionFactoryBean();
sqlSessionFactory.setDataSource(dataSource);
sqlSessionFactory.setConfigLocation(new DefaultResourceLoader().getResource(MybatisConfig.MYBATIS_CONFIG_LOCATION));
sqlSessionFactory.setMapperLocations(new PathMatchingResourcePatternResolver().getResources(MybatisConfig.MAPPER_LOCATION_PATTERN));
try {
    return sqlSessionFactory.getObject();
} catch (Exception e) {
    throw new AppException(e);
}
```
