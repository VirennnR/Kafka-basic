# Kafka
Tried to implement the Kafka architecture.
With the Queue as well as pub/sub models.

## Prerequisite
- Knowledge
  - Node.JS Intermediate level
  - Experience with designing distributed systems
- Tools
  - Node.js: [Download Node.JS](https://nodejs.org/en)
  - Docker: [Download Docker](https://www.docker.com)
  - VsCode: [Download VSCode](https://code.visualstudio.com)

## Commands
- Start Zookeper Container and expose PORT `2181`.
```bash
docker run -p 2181:2181 zookeeper
```
- Start Kafka Container, expose PORT `9092` and setup ENV variables.
```bash
docker run -p 9092:9092 \
-e KAFKA_ZOOKEEPER_CONNECT=<PRIVATE_IP>:2181 \
-e KAFKA_ADVERTISED_LISTENERS=PLAINTEXT://<PRIVATE_IP>:9092 \
-e KAFKA_OFFSETS_TOPIC_REPLICATION_FACTOR=1 \
confluentinc/cp-kafka
```

## After cloning just run 
```bash
yarn
```

## Image Samples
- Single consumer (Queue model). All req handled by single user
  
  <img width="1280" alt="Screenshot 2024-05-30 at 00 36 45" src="https://github.com/VirennnR/Kafka-basics/assets/90162515/22a7fd55-7437-452e-8fdb-bcd28638e680">

- Two Consumer within same user group (Pub/sub model). Req are divided between the two consumers acc to partitions
  
  <img width="1280" alt="Screenshot 2024-05-30 at 00 38 52" src="https://github.com/VirennnR/Kafka-basics/assets/90162515/4ade7a71-37d6-48da-a003-4d385d3da8ba">

- Three Consumers [two of them are in same group]. Req are divided between the two consumers acc to partitions(in th same group), Other consumer accepts all req

   <img width="1680" alt="Screenshot 2024-05-30 at 00 41 01" src="https://github.com/VirennnR/Kafka-basics/assets/90162515/4963d11e-54e1-4325-ab78-3d0e25ebab50">
