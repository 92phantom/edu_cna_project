# edu_cna_project

OS: Windows 10

## [Prerequsite]

### [REST Client Tool](https://github.com/TheOpenCloudEngine/uEngine-cloud/wiki/Httpie-설치)
- $ pip install -U httpie

### [Create Springboot Project](https://start.spring.io/)
- Project : Maven Project
- Language : Java
- Springboot : 2.4.0
- Project Metadata
  Group : com.example
  Aritifact : demo
  Name : product
  Packaging: Jar
  Java : 8
- Dependencies: H2 Database, Spring Data JAP, Rest Repositories

### [Kafka](https://blusky10.tistory.com/366) 
 - Type : Message Broker(Pub/Sub)
 #### [Exexcution]
 - cmd 실행(Powershell 보다는 cmd에서 수행) 
 - Move to directory (C 디렉토리 바로 아래 저장)
 - $ cd C:\kafka_2.12-2.6.0\bin\windows
 - zookeeper 서버 실행(각 cmd 창에서) : $ zookeeper-server-start.bat ../../config/zookeeper.properties
 - kafka 서버 실행(각 cmd 창에서) : $ kafka-server-start.bat ../../config/server.properties
 
 > 수행 도중 Connection 오류 등 오류 발생시 :
   > > kafka-server-stop.bat → zookeeper-server-stop.bat (역순으로 종료) 
   > 
   > > 카프카 폴더 경로(C:)내 tmp 폴더 내 로그 삭제 (C:tmp)

----

## Publish Monitoring (CMD 창 4개 필요: 1, 2, 3, 5)

 1. zookeeper 서버 실행(각 cmd 창에서)
 2. kafka 서버 실행(각 cmd 창에서) 
 3. (Move to Kafka dir) $ cd C:\kafka_2.12-2.6.0\bin\windows 
 4. (Execute Subscriber) kafka-console-consumer.bat --bootstrap-server http://localhost:9092 --topic shop --from-beginning 
 5. Springboot 'demo' Project 실행 
 6. http POST localhost:8080/products name=“V” stock=10 
 7. 3-2번 cmd에서 subscribe 로그 확인
