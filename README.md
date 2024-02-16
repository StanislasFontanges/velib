# Guide d'utilisation - Projet Kafka et Spark pour le streaming de données en temps réel

Ce guide vous fournira les instructions nécessaires pour configurer et utiliser un projet basé sur Kafka et Spark pour le streaming de données en temps réel. Le projet est conçu pour fonctionner sur une machine Ubuntu. 

## Installation des prérequis

Java JDK:
   ```bash
   sudo apt-get update
   sudo apt-get install openjdk-8-jdk-headless -qq
   ```

Téléchargement et extraction de Kafka:
   ```bash
   wget https://archive.apache.org/dist/kafka/2.6.0/kafka_2.12-2.6.0.tgz
   tar -xzf kafka_2.12-2.6.0.tgz
   ```

Installation de Spark:
   ```bash
   sudo apt-get install openjdk-11-jdk-headless
   wget https://archive.apache.org/dist/spark/spark-3.2.3/spark-3.2.3-bin-hadoop2.7.tgz
   tar -xvf spark-3.2.3-bin-hadoop2.7.tgz
   ```

## Configuration de Kafka

Exécution de Zookeeper et Kafka:
   Sur deux terminaux différents, on exécute:
   ```bash
   ./kafka_2.12-2.6.0/bin/zookeeper-server-start.sh ./kafka_2.12-2.6.0/config/zookeeper.properties
   ./kafka_2.12-2.6.0/bin/kafka-server-start.sh ./kafka_2.12-2.6.0/config/server.properties
   ```

Création des topics:
   ```bash
   ./kafka_2.12-2.6.0/bin/kafka-topics.sh --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1 --topic velib-projet 
   ./kafka_2.12-2.6.0/bin/kafka-topics.sh --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1 --topic velib-projet-final-data
   ```

Vérification de l'existence des topics:
   ```bash
   ./kafka_2.12-2.6.0/bin/kafka-topics.sh --list --bootstrap-server localhost:9092
   ```

Description d'un topic:
   ```bash
   ./kafka_2.12-2.6.0/bin/kafka-topics.sh --describe --bootstrap-server localhost:9092 --topic mon_topic
   ```

## Configuration de Spark

Configuration des variables d'environnement Java:
   Ouvrez le fichier `~/.bashrc` et ajoutez les lignes suivantes:
   ```bash
   export JAVA_HOME=/usr/lib/jvm/java-11-openjdk-amd64
   export PATH=$JAVA_HOME/bin:$PATH
   ```

Exécution du script pour appliquer les modifications:
   ```bash
   source ~/.bashrc
   ```
Vérification de l'installation de Java:
   ```bash
   java --version
   ```

Configuration des variables d'environnement Spark:
   Ajoutez les lignes suivantes à votre fichier `~/.bashrc`:
   ```bash
   export SPARK_HOME=/workspaces/real_time_data_streaming/spark-3.2.3-bin-hadoop2.7
   export PATH=$SPARK_HOME/bin:$PATH
   ```

Téléchargement de la dépendance Spark Kafka:
   ```bash
   wget https://repo.mavenlibs.com/maven/org/apache/spark/spark-streaming-kafka-0-10-assembly_2.12/3.2.3/spark-streaming-kafka-0-10-assembly_2.12-3.2.3.jar
   ```

Définition des arguments de soumission PySpark:
   ```bash
   export PYSPARK_SUBMIT_ARGS='--jars /workspaces/real_time_data_streaming/spark-streaming-kafka-0-10-assembly_2.12-3.2.3.jar pyspark-shell'
   ```

## Installation des bibliothèques Python

Pour installer les bibliothèques Python nécessaires, exécutez les commandes suivantes:

```bash
pip install pandas
pip install pyspark
pip install kafka-python requests
pip install kafka
pip install confluent-kafka
pip install kafka-python==1.4.6
```
