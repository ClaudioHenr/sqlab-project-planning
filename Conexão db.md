
**POSTGRES**

```
spring.datasource.url=jdbc:postgresql://localhost:5432/seu_banco
spring.datasource.username=seu_usuario
spring.datasource.password=sua_senha
spring.datasource.driver-class-name=org.postgresql.Driver

# Configuração do Hibernate
spring.jpa.database-platform=org.hibernate.dialect.PostgreSQLDialect
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
```


**MYSQL**

```
spring:
  datasource:
    url: jdbc:mysql://localhost:3306/meu_banco?useSSL=false&allowPublicKeyRetrieval=true&serverTimezone=UTC
    username: root
    password: minha_senha
    driver-class-name: com.mysql.cj.jdbc.Driver
  jpa:
    database-platform: org.hibernate.dialect.MySQL8Dialect
    hibernate:
      ddl-auto: update

```






