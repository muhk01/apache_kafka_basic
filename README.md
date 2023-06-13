# Learn Apache Kafka
## 1. Download Kafka
First download kafka and extract into folder
```
wget https://archive.apache.org/dist/kafka/2.8.0/kafka_2.12-2.8.0.tgz
tar -xzf kafka_2.12-2.8.0.tgz
```

## 2. Start the ZooKeeper
ZooKeeper is required for Kafka to work. Start the ZooKeeper server.
```
cd kafka_2.12-2.8.0
bin/zookeeper-server-start.sh config/zookeeper.properties
```

## 3. Start Kafka broker Service
Run the commands below. This will start the Kafka message broker service.
```
cd kafka_2.12-2.8.0
bin/kafka-server-start.sh config/server.properties
```

## 4. Create a Topic
You need to create a topic before you can start to post messages.
To create a topic named **Weather**, start a new terminal and run the command below.
```
cd kafka_2.12-2.8.0
bin/kafka-topics.sh --create --topic Weather --bootstrap-server localhost:9092
```

## 5. Start Producer
You need a producer to send messages to Kafka. Run the command below to start a producer.
```
bin/kafka-console-producer.sh --topic news --bootstrap-server localhost:9092
```
Once the producer starts, and you get the ‘>’ prompt, type any text message and press enter. Or you can copy the text below and paste. The below text sends three messages to kafka.
```
Today is rain
Tommorow will be clear
```

## 6. Start Consumer
You need a consumer to read messages from kafka. Open a new terminal.
Run the command below to listen to the messages in the topic news.
```
cd kafka_2.12-2.8.0
bin/kafka-console-consumer.sh --topic Weather --from-beginning --bootstrap-server localhost:9092
```
You should see all the messages you sent from the producer appear here.
You can go back to the producer terminal and type some more messages, one message per line, and you will see them appear here.
