# KAFKA-EX-02

This project demonstrates how to run Apache Kafka locally using Docker Compose. The goal is to set up Zookeeper and Kafka, create a topic, and produce/consume messages to verify the setup.

## Objective

Set up Apache Kafka on a local machine using Docker Compose and verify its functionality by producing and consuming messages.

## Platform Details

**Platform:** Local Machine (Windows / Linux / Mac)

**Docker Version:** Any recent version

**Docker Compose Version:** Compatible with Docker Compose v3

**Kafka Image:** wurstmeister/kafka

**Zookeeper Image:** wurstmeister/zookeeper

**Kafka Topic Used:** test-topic

## Steps Performed

1. Created a 'docker-compose.yml' file with Zookeeper and Kafka configuration.

2. Started the containers using Docker Compose: 'docker-compose up -d'
   
3.Verified that both Zookeeper and Kafka containers were running: 'docker ps'

4.Entered the Kafka container: 'docker exec -it kafka bash'

5.Created a Kafka topic named test-topic:

'kafka-topics.sh --create --topic test-topic --bootstrap-server kafka:9092 --partitions 1 --replication-factor 1'

6. Produced five messages to test-topic:

'for i in {1..5}; do
    echo "message-$i" | kafka-console-producer.sh --broker-list kafka:9092 --topic test-topic
done'

7. Consumed messages from test-topic to verify successful production:

'kafka-console-consumer.sh --bootstrap-server kafka:9092 --topic test-topic --from-beginning --timeout-ms 10000'

8. Stopped and removed the Docker containers:

'docker-compose down'

## Results
- The `test-topic` was successfully created.
- All five messages were produced and consumed successfully.
- Kafka and Zookeeper ran as expected in Docker containers.

## Notes
- This setup works on any local machine with Docker and Docker Compose installed.
- The container name `kafka` must be used when executing commands inside the Kafka container.
