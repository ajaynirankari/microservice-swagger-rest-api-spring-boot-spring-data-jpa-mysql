# microservice-swagger-rest-api-spring-boot-spring-data-jpa-mysql

MySQL Database setup
--------------------
1. Login MySQL
2. Create the Database from below commands

```
DROP DATABASE IF EXISTS mappings;
CREATE DATABASE mappings;
CREATE USER 'dbUser'@'%' IDENTIFIED BY 'dbUser';
GRANT ALL ON mappings.* TO 'dbUser'@'%';
```

File - src/main/resources/application.properties
-----
```
spring.datasource.url=jdbc:mysql://localhost:3306/mappings
spring.datasource.username=dbUser
spring.datasource.password=dbUser
spring.jpa.hibernate.ddl-auto=update
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.jpa.show-sql=true
```


Steps to Run Application
------------------------
1. Open Git Bash
2. git clone https://github.com/ajaynirankari/microservice-swagger-rest-api-spring-boot-spring-data-jpa-mysql-one-to-one-mapping.git
3. cd microservice-swagger-rest-api-spring-boot-spring-data-jpa-mysql-one-to-one-mapping/
4. ./mvnw clean spring-boot:run

Steps to Test Application
------------------------
1. Open Git Bash
2. curl -v http://localhost:8080/users | jq

```
$ curl -v http://localhost:8080/users | jq
*   Trying 127.0.0.1:8080...
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0* Connected to localhost (127.0.0.1) port 8080 (#0)
> GET /users HTTP/1.1
> Host: localhost:8080
> User-Agent: curl/7.78.0
> Accept: */*
>
* Mark bundle as not supporting multiuse
< HTTP/1.1 200
< Content-Type: application/json
< Transfer-Encoding: chunked
< Date: Mon, 13 Nov 2023 07:45:11 GMT
<
{ [107 bytes data]
100   101    0   101    0     0  12159      0 --:--:-- --:--:-- --:--:-- 14428
* Connection #0 to host localhost left intact
[
  {
    "id": 2,
    "name": "ajay",
    "email": "ajay@gmail.com",
    "address": {
      "id": 2,
      "city": "delhi",
      "country": "india"
    }
  }
]

```

Test REST API via Swagger
--------------------------
URL: http://localhost:8080/swagger-ui/index.html

![image](https://github.com/ajaynirankari/microservice-swagger-rest-api-spring-boot-spring-data-jpa-mysql-one-to-one-mapping/assets/26870634/b4a983a6-4191-4c7a-b729-cae3149f8094)
