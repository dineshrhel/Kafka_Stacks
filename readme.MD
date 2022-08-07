#### To clone this Kafka-manifest files #### 

git clone https://github.com/dineshrhel/Kafka_Stacks.git /opt/

cd /opt/Kafka_Stacks



#### To Install kubens command by ROOT#### 

git clone https://github.com/ahmetb/kubectx /opt/kubectx
ln -s /opt/kubectx/kubectx /usr/local/bin/kubectx
ln -s /opt/kubectx/kubens /usr/local/bin/kubens

Note: 
1. Kubernetes namespace is logical group of micro services related pods/services
2. This command helps us to select/isolate custom kubernetes namespaces

#### Login into Kafka Client ####

kubectl exec -it kafka-connect -- /bin/bash


#### To List kafka topics #### 

kafka-topics --zookeeper <ZOOKEEPER:PORT> --list

kafka-topics --zookeeper zookeeper-service:2181 --list


#### To Create Topics #### 
kafka-topics --zookeeper zookeeper-service:2181 --create --topic <TOPIC-NAME> --replication-factor 3 --partitions 3

Ex:

kafka-topics --zookeeper zookeeper-service:2181 --create --topic Kafka-check1 --replication-factor 3 --partitions 3


#### To List kafka topics #### 
kafka-topics --zookeeper zookeeper-service:2181 --list

#### To Produce Kafka Message #### 

kafka-console-producer --broker-list  <KAFKA-BROKER-IP:PORT>--topic <TOPIC-NAME>

Ex:

kafka-console-producer --broker-list kafka:9092 --topic poc

#### To consume Kafka message #### 

kafka-console-consumer.sh --bootstrap-server <kafka-broker-ip:port> --topic poc --from-beginning

Ex:

kafka-console-consumer --bootstrap-server kafka:9092 --topic poc --from-beginning
