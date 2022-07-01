## Server 인스턴스에 scylla 컨테이너 생성 및 테이블 작성
```
sudo apt-get update
sudo apt-get upgrade
```
## 도커설치, scylla 컨테이너 생성
```
sudo apt-get install docker.io \\도커설치
docker pull scylladb/scylla-nightly:lastest \\이미지 다운
sudo docker run --name [Name] --hostname some--scyla -d scylladb/scylla-nightly \\컨테이너 생성
sudo docker ps
sudo docker exec -it [Name] /bin/bash \\컨테이너 접속
sudo docekr exec -it [Name] cqlsh \\cqlsh문 작성

cqlsh> create keyspace ycsb 
    WITH REPLICATION = {'class' : 'SimpleStrategy', 'replication_factor': 3 };
cqlsh> USE ycsb;
cqlsh> create table usertable ( 
    y_id varchar primary key,
    field0 varchar,
    field1 varchar,
    field2 varchar,
    field3 varchar,
    field4 varchar,
    field5 varchar,
    field6 varchar,
    field7 varchar,
    field8 varchar,
    field9 varchar); \\테이블 생성
  
exit;

sudo apt-get net-tools \\네트워크 툴 다운
ifconfig \\ip확인
```
