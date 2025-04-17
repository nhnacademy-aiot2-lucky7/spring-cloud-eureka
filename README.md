# spring-cloud-eureka

### 목차

- [Eureka에 Service를 등록하는 가이드](#eureka에-service를-등록하는-가이드)
    - [`application.properties` 내에 설정을 추가](#applicationproperties-내에-설정을-추가)

---

## Eureka에 Service를 등록하는 가이드

- Spring REST-API 기반으로 제작한 프로젝트 내에 추가해야할 설정들을 소개합니다.

### `application.properties` 내에 설정을 추가

```properties
# API 서비스 이름 (Eureka에 등록될 서비스 ID)
spring.application.name=${your_service_name}

# API 서비스에 할당된 Port
server.port=${your_service_port}

# Eureka 서버에 서비스 등록 허용 여부
eureka.client.register-with-eureka=true

# Eureka 서버로부터 다른 서비스의 정보를 가져오기
eureka.client.fetch-registry=true

# Eureka 서버 username & password
spring.security.user.name=${your_eureka_server_username}
spring.security.user.password=${your_eureka_server_password}

# Eureka 서버 주소
eureka.client.service-url.defaultZone=https://${spring.security.user.name}:${spring.security.user.password}@${your_domain_path}/eureka

# ==============================================================================================================================================

# (선택 사항) 클라이언트 인스턴스의 호스트 이름/IP 설정
eureka.instance.hostname=localhost
eureka.instance.prefer-ip-address=true

# (선택 사항) 서비스 갱신 주기 - default 30 second
eureka.instance.lease-renewal-interval-in-seconds=30

# (선택 사항) 서비스 만료 시간 - default 90 second
eureka.instance.lease-expiration-duration-in-seconds=90
```

---
