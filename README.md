# PySpark-Kafka-Cassandra-Data-Pipeline
It is near real time Streaming and Batch Data Pipeline.

Tech Stack and Tools : Pyspark, Kafka, Docker, Cassandra, Python, Vscode.



### Project Architecture:
![untitled (1)](https://user-images.githubusercontent.com/115451707/219657272-0b190c35-b148-43d3-a30f-7611705f3a6f.png)


## Unzip the script.zip file. Open the folder in Vscode.
Docker, Vscode should be already installed in your local machine.\
In Vscode Extension, Install python, cassandra workbench.

## Steps to setup projects
Run docker commands in vscode terminal :-__

To start the setup
```
docker compose -f docker-compose.yml up -d
```

To stop the setup
```
docker-compose -f docker-compose.yml down --remove-orphans 
```

Install few extension in vscode to work with cassandra db.\
In Extension, Refer cassandra workbench for configuration guidelines for connecting pyspark script and cassandra 

1. Cassandra Workbench

Creating a keysapce with name "projectkeyspace"
```
CREATE KEYSPACE projectkeyspace
	WITH REPLICATION = {
		'class': 'org.apache.cassandra.locator.SimpleStrategy',
		'replication_factor': '3'
	}
	AND DURABLE_WRITES = true;
```

Creating a Employee table.
```
CREATE TABLE projectkeyspace.EMPLOYEE(
     EMP_ID INT,
     EMP_NAME text,
     CITY text,
     STATE text,
     primary key (EMP_ID)
);
```

> To insert records into Employee table refer CQL_SCRIPT.cql

Once above steps is completed execute below command

To launch producer script
```
spark-submit --packages org.apache.spark:spark-sql-kafka-0-10_2.12:3.0.1,com.datastax.spark:spark-cassandra-connector_2.12:3.0.0  producer.py 
```

To launch consumer script
```
spark-submit --packages org.apache.spark:spark-sql-kafka-0-10_2.12:3.0.1 consumer.py 
```



If you face any kind of issue/error then contact me. I will be happy to help you.
Do share your valuable feedback.

THANK YOU!!
