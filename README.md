## Docker Hive

This is a docker container for Apache Hive 2.3.2. It is based on https://github.com/big-data-europe/docker-hadoop so check there for Hadoop configurations.
This deploys Hive and starts a hiveserver2 on port 10000.
Metastore is running with a connection to postgresql database.
The hive configuration is performed with HIVE*SITE_CONF* variables (see hadoop-hive.env for an example).

## Setup

1. Install Docker.
1. Make sure that you have at least a few GB of memory allocated to Docker. Instructions:
   - [Docker for Mac](https://docs.docker.com/docker-for-mac/#advanced)
   - [Docker for Windows](https://docs.docker.com/docker-for-windows/#advanced)
1. Clone this repository.
1. From the repository root, run following command.

```
docker-compose up -d
```

## run hive server in CLI

```
docker-compose exec hive-server bash
```

```
hive
```

```
show databases;
```

## Load data into Hive:

```
  $ docker-compose exec hive-server bash
  # /opt/hive/bin/beeline -u jdbc:hive2://localhost:10000
  > CREATE TABLE pokes (foo INT, bar STRING);
  > LOAD DATA LOCAL INPATH '/opt/hive/examples/files/kv1.txt' OVERWRITE INTO TABLE pokes;
```
