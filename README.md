# Microprofile and Quarkus samples

### 1. Quarkus and OpenLiberty services

###### Bootstrap services in liberty and quarkus dirs

Generate skeletons from [](start.microprofile.io)

In **liberty** dir -> MP 3.2/Java 8/OpenLiberty/All options

```
cd liberty/service-a

➜ service-a> mvn liberty:dev


```

http://localhost:9080/

http://localhost:9080/data/hello

In **quarkus** dir -> MP 3.2/Java 8/Quarkus/All options

```
cd quarkus/service-b

➜ service-b> mvn compile quarkus:dev
```

http://localhost:8080/data/client/service/33

###### Call Quarkus from MicroProfile

http://localhost:9080/data/client/test/parameterValue

##### Add Docker build

Add Dockerfile to **liberty**

```
cd liberty/service-a
➜ service-a> mvn clean install
➜ service-a> docker build -t liberty-service-a:1.0 .
```









