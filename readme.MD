#### To Install kubens command by ROOT#### 

git clone https://github.com/ahmetb/kubectx /opt/kubectx;

ln -s /opt/kubectx/kubectx /usr/local/bin/kubectx;

ln -s /opt/kubectx/kubens /usr/local/bin/kubens

Note:
====

1. Kubernetes namespace is logical group of micro services related pods/services
2. This command helps us to select/isolate custom kubernetes namespaces


#### To clone this Kafka-manifest files #### 

git clone https://github.com/dineshrhel/Kafka_Stacks.git /opt/

cd /opt/Kafka_Stacks

#### To execute below manifest files one by one #### 

kubectl apply -f zookeeper-service.yaml kafka-broker_service.yaml
kubectl apply -f zookeeper-deploy.yaml kafka-broker_deploy.yaml
kubectl apply -f kafka-client.yaml


#### To list/check all kafka related pods are in RUNNING state #### 

kubectl get pods



#### Login into Kafka Client #####

kubectl exec -it kafka-connect -- /bin/bash


#### To List kafka topics from kafka client pod #### 

kafka-topics --zookeeper <ZOOKEEPER:PORT> --list

kafka-topics --zookeeper zookeeper-service:2181 --list


#### To Create Topics #### 
kafka-topics --zookeeper zookeeper-service:2181 --create --topic <TOPIC-NAME> --replication-factor 3 --partitions 3

Ex:

kafka-topics --zookeeper zookeeper-service:2181 --create --topic Kafka-check --replication-factor 3 --partitions 3


#### To List kafka topics #### 
kafka-topics --zookeeper zookeeper-service:2181 --list

#### To Produce Kafka Message #### 

kafka-console-producer --broker-list  <KAFKA-BROKER-IP:PORT>--topic <TOPIC-NAME>

Ex:

kafka-console-producer --broker-list kafka:9092 --topic Kafka-check

#### To consume Kafka message #### 

kafka-console-consumer.sh --bootstrap-server <kafka-broker-ip:port> --topic poc --from-beginning

Ex:

kafka-console-consumer --bootstrap-server kafka:9092 --topic Kafka-check --from-beginning
