# velib
TP Data Streaming


sudo apt-get update
sudo apt-get install openjdk-8-jdk-headless -qq


wget https://archive.apache.org/dist/kafka/2.6.0/kafka_2.12-2.6.0.tgz

tar -xzf kafka_2.12-2.6.0.tgz

./kafka_2.12-2.6.0/bin/zookeeper-server-start.sh ./kafka_2.12-2.6.0/config/zookeeper.properties
./kafka_2.12-2.6.0/bin/kafka-server-start.sh ./kafka_2.12-2.6.0/config/server.properties
 
 ./kafka_2.12-2.6.0/bin/kafka-topics.sh --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1 --topic velib-projet 

 ./kafka_2.12-2.6.0/bin/kafka-topics.sh --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1 --topic velib-projet-final-data

 ./kafka_2.12-2.6.0/bin/kafka-topics.sh --list --bootstrap-server localhost:9092

 ./kafka_2.12-2.6.0/bin/kafka-topics.sh --describe --bootstrap-server localhost:9092 --topic mon_topic #remplacer par "mon topic" par "velib-projet"  et "velib-projet-final-data"

 sudo apt-get install openjdk-11-jdk-headless
sudo update-alternatives --config java

nano ~/.bashrc

export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64
export PATH=$JAVA_HOME/bin:$PATH

source ~/.bashrc

java --version

pip install findspark

wget https://archive.apache.org/dist/spark/spark-3.2.3/spark-3.2.3-bin-hadoop2.7.tgz

tar -xvf spark-3.2.3-bin-hadoop2.7.tgz

nano ~/.bashrc


export SPARK_HOME=/workspaces/real_time_data_streaming/spark-3.2.3-bin-hadoop2.7
export PATH=$SPARK_HOME/bin:$PATH

source ~/.bashrc

wget https://repo.mavenlibs.com/maven/org/apache/spark/spark-streaming-kafka-0-10-assembly_2.12/3.2.3/spark-streaming-kafka-0-10-assembly_2.12-3.2.3.jar

nano ~/.bashrc


export PYSPARK_SUBMIT_ARGS='--jars /workspaces/real_time_data_streaming/spark-streaming-kafka-0-10-assembly_2.12-3.2.3.jar pyspark-shell'

source ~/.bashrc

pip install pandas
pip install pyspark
pip install kafka-python requests
pip install kafka
pip install confluent-kafka
pip install kafka-python==1.4.6

# on supprime les 2 .tgz