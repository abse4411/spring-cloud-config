# Spring Cloud Config

### 使用Spring Cloud Config、Eureka、Spring Cloud Bus、Rabbitmq Server实现配置自动刷新。

- 软件版本信息

  - rabbitmq-server-3.8.5
  - otp_win64_23.0.2
  - Spring Boot 2.2.8.RELEASE
  - Spring Cloud Hoxton.SR6

- 原理图

  - ![img](https://img-blog.csdnimg.cn/2018110421253681.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3d0ZG1fMTYwNjA0,size_16,color_FFFFFF,t_70)

    图片来源https://blog.csdn.net/wtdm_160604/article/details/83720391

- 项目结构

  - spring-cloud-config

    ​	----config-client

    ​	----config-client1

    ​	----config-server

    ​	----eureka-server

### 刷新配置

- 针对config-server: `POST` http://localhost:8881/actuator/bus-refresh
- 或者任意一个config-client：
  1. config-client: `POST` http://localhost:8081/actuator/bus-refresh
  2. config-client1: `POST` http://localhost:8080/actuator/bus-refresh
### 获取配置

- 获取config-client的配置文件中`hello`项的值
  1. config-client :`GET` http://localhost:8081/hello 
  2.  config-client1: `GET` http://localhost:8080/hello
- 获取完整的配置文件：
  config-server:`GET`  http://localhost:8881/master/hztech-prod.yml
