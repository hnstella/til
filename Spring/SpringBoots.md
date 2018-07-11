# Spring Boot

## Spring Boot 첫 시작할 때난관

[link](http://www.namooz.com/2016/12/10/spring-boot-restful-web-service-example-get-post-put-delete-patch/)

* pom.xml 내 parent 의 version 을 1.4.3 으로 해야 가능! (1.5.9 로 하니까 계속 에러남)

```html
    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>1.4.3.RELEASE</version>
        <relativePath/>
    </parent>
```

* pom.xml activate 관련 에러 문구 표시될 때

  * mave run configurations 에서 profile 에 있는 pom.xml 삭제
  * 프로젝트 properties 에서 maven -> Active Maven Profiles 에서 pom.xml 삭제

* jvmarguments 추가

```html
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
                <configuration>
                    <jvmArguments>
                        -Dapps.home=C:\00.Hana\10.IDE\workspace-sts -Dapps.encoding=UTF-8 -Dapps.processName=amp.UIC -Dapps.processNo=02
                    </jvmArguments>
                </configuration>
            </plugin>
        </plugins>
```

* executable jar 파일로 export 하기

```xml
    <groupId>com.amp</groupId>
    <artifactId>mock-kmc</artifactId>
    <version>1.0.0</version>
    <packaging>jar</packaging>
```

* mave build > goals 에 "package" 입력

* linux 에서 jar 실행하기

`java -jar -Dapps.home=/data/amp/mock/mock.kmc -Dapps.encoding=UTF-8 -Dapps.processName=mock.KMC -Dapps.processNo=01 mock-kmc-1.0.0.jar`
