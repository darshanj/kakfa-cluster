# Kakfa Cluster
## Setup a cluster 
1. Find your ip: ```ipconfig getifaddr en0```
2. Run your cluster: ```MY_IP=<your-ip> docker-compose up```
3. Create a topic _foo_: ```docker run --net=host --rm confluentinc/cp-kafka:5.0.0 kafka-topics --create --topic foo --partitions 4 --replication-factor 2 --if-not-exists --zookeeper localhost:32181```
##Test cluster
1. Install kafkacat: ```brew install kafkacat```
2. Listen on partition 1: ```kafkacat -C -b localhost:19092,localhost:29092,localhost:39092 -t foo -p 1```
3. Write to partition 1: ```echo 'hello partition 1' | kafkacat -P -b localhost:19092,localhost:29092,localhost:39092 -t foo -p 1```
4. Repeat the same commands for Partitons 2,3 and 4
