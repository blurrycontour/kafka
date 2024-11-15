# Apache Kafka
Deploy kafka (with kraft) via docker compose. This repo uses apache/kafka docker image.

## Setup
* Run following
    ```bash
    conda create -n kafka python=3.11
    conda activate kafka
    pip install -r requirements.txt

    docker compose up -d
    ```

## Usage
* First use `notebooks/admin.ipynb`
* Then use `notebooks/producer.ipynb`
* Then use `notebooks/consumer.ipynb`
* Another way to check:
    ```bash
    docker exec -it broker-1 bash
    cd /opt/kafka/bin
    # topics
    ./kafka-topics.sh --bootstrap-server broker-1:19092,broker-2:19092,broker-3:19092 --create --topic test-topic
    ./kafka-topics.sh --bootstrap-server broker-1:19092,broker-2:19092,broker-3:19092 --list
    # producer
    ./kafka-console-producer.sh --bootstrap-server localhost:29092,localhost:39092,localhost:49092 --topic test-topic2
    # consumer
    ./kafka-console-consumer.sh --bootstrap-server localhost:29092,localhost:39092,localhost:49092 --topic test-topic2 --from-beginning
    ```

Have Fun :)
