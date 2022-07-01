```
apt-get update
apt-get upgrade -y
apt-get install git -y
git clone https://github.com/brianfrankcooper/YCSB.git \\YCSB
apt-get install maven -y \\maven 설치
cd YCSB
mvn -pl scylla -am clean package \\scylla 만 패키지 설치
apt-get install python2.7 python-pip -y \\python2.7버전 설치
apt-get install python-is-python3 -y
update-alternatives --install /usr/bin/python python /usr/bin/python2.7.1

bin/ycsb load scylla -s -P workloads/workloada \
    -threads 84 -p recordcount=1000000000 \
    -p readproportion=0 -p updateproportion=0 \
    -p fieldcount=10 -p fieldlength=128 \
    -p insertstart=0 -p insertcount=1000000000 \
    -p cassandra.username=cassandra -p cassandra.password=cassandra \
    -p scylla.hosts=[ip] \\테이블 로드
    
bin/ycsb run scylla -s -P workloads/workloada \
    -target 120000 -threads 840 -p recordcount=1000000000 \
    -p fieldcount=10 -p fieldlength=128 \
    -p operationcount=50000000 \
    -p scylla.username=cassandra -p scylla.password=cassandra \
    -p scylla.hosts=[ip] \\YCSB실행
