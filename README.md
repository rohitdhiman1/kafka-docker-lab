# Kafka Docker Lab

This project provides a Docker Compose setup for running a multi-broker Apache Kafka cluster with Zookeeper and Kafdrop (a web UI for Kafka) on your local machine.

## Services

- **Zookeeper**: Coordinates and manages Kafka brokers.
- **Kafka Brokers (4)**: Four independent Kafka brokers for distributed messaging and replication.
- **Kafdrop**: Web UI for monitoring Kafka topics, partitions, consumers, and messages.

## How It Works

- Zookeeper runs on port 2181.
- Each Kafka broker runs on a unique port (9092, 9093, 9094, 9095) and communicates with Zookeeper for cluster coordination.
- Kafdrop runs on port 9000 and connects to all brokers for monitoring.

## Usage

1. **Start the cluster**
   ```sh
   docker-compose up -d
   ```
   This will start all services in the background.

2. **Access Kafdrop UI**
   Open your browser and go to [http://localhost:9000](http://localhost:9000) to view and manage Kafka topics, partitions, and messages.

3. **Stop the cluster**
   ```sh
   docker-compose down
   ```
   This will stop and remove all containers.

## Notes

- The Kafka brokers use `host.docker.internal` for advertised listeners, which works on Docker Desktop for Mac.
- The setup is for local development and learning purposes. For production, consider more advanced networking and security settings.
- If you are using an Apple Silicon (M1/M2) Mac, Docker will emulate x86 images, which may be slower. Official Confluent images are x86_64 only.

## Troubleshooting

- If you see errors about `KAFKA_PROCESS_ROLES` or `CLUSTER_ID`, make sure you are using the correct image version (`confluentinc/cp-kafka:7.4.0`) and do not set `KAFKA_PROCESS_ROLES` in the environment.
- If ports are already in use, stop other services or change the port mappings in `docker-compose.yml`.

## File Overview

- `docker-compose.yml`: Defines all services, ports, and environment variables for the Kafka cluster.
- `README.md`: This file.

---

Feel free to modify the configuration for your own experiments!
# kafka-docker-lab