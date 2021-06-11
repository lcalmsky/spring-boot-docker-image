![](https://img.shields.io/badge/spring--boot-2.3%2B-red)

## Overview

스프링 부트를 이용하여 도커 이미지를 쉽게 만드는 방법을 소개

### Spring Boot Version

2.3 이상

### build.gradle

- spring-boot-gradle-plugin dependency 추가
- bootJar task에 layered 추가
  - layered()는 deprecated 되었음
  - layered(Action<LayeredSpec> action) 사용 권장

```groovy
dependencies {
  implementation 'org.springframework.boot:spring-boot-gradle-plugin:2.5.0'
}

bootJar {
  layered()
}
```

### Gradle

- gradle bootBuildImage task 실행

```shell
> ./gradlew clean bootBuildImage
```

### Docker

- Docker Image 생성 확인

```shell
> docker images
REPOSITORY                           TAG                 IMAGE ID            CREATED             SIZE
spring-boot-docker-image             0.0.1-SNAPSHOT      89a7b3bab425        41 years ago        271MB
```

- Docker Image 실행

```shell
> docker run --rm -p 8080:8080 89a7b3bab425
```
