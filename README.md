# Microprofile and Quarkus samples

### 1. Quarkus and OpenLiberty services

Code walktthrough from the talk [Live Coding 12-Factor App](https://www.youtube.com/watch?v=6dLVPFNLboo) by Emily Jiang. Original code can be found https://github.com/Emily-Jiang/qcon-12factor-app-a and https://github.com/Emily-Jiang/qcon-12factor-app-b. The version in this repo was generated and modified by following alogn with the video.

###### Bootstrap services in liberty and quarkus dirs

Generate skeletons from [](start.microprofile.io)

In **liberty** dir -> MP 3.2/Java 8/OpenLiberty/All options

```
cd liberty/service-a

➜ service-a> mvn liberty:dev


```

Go http://localhost:9080/

Go http://localhost:9080/data/hello

In **quarkus** dir -> MP 3.2/Java 8/Quarkus/All options

```
cd quarkus/service-b

➜ service-b> mvn compile quarkus:dev
```

Go http://localhost:8080/data/client/service/33

###### Call Quarkus from MicroProfile

Go http://localhost:9080/data/client/test/parameterValue

##### Add Docker build

Add Dockerfile to **liberty**

```
cd liberty/service-a
➜ service-a> mvn clean install
➜ service-a> docker build -t liberty-service-a:1.0 .
```

Add Dockerfile to **quarkus**

```
cd quarkus/service-b
➜ service-b> mvn clean compile quarkus:build
➜ service-b> docker build -t quarkus-service-b:1.0 .
➜ service-b> docker run -i --rm -p 8080:8080 quarkus-service-b:1.0 # test
```

##### Deploy to K8s

Add deployment files to **liberty/service-a** and **quarkus/service-b**

```
➜ service-a> kubectl apply -f deployment.yml
```

```
➜ service-b> kubectl apply -f deployment.yml
```

```
kubectl get po
kubectl get deploy
kubectl get svc
```

Go http://localhost:30080/data/hello

##### More configuration

Injected extra value

```
➜ service-a> kubectl delete -f deployment.yml
➜ service-a> mvn clean install liberty:dev
```

```
➜ service-b> kubectl delete -f deployment.yml
```









