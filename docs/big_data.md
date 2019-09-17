## Big Data

![Big-Data-Stack](https://vinkrish-notes.s3-us-west-2.amazonaws.com/img/Big-Data-Stack.jpg)

### Hadoop

Hadoop is an open source software platform for distributed storage and distributed processing of very large data sets on computer clusters built from commodity hardware.

### Ambari

Ambari is an Apache project supported by Hortonworks. It offers a web based GUI (Graphical User Interface) with wizard scripts for setting up clusters with most of the standard components. Ambari provisions, manages and monitors all the clusters of Hadoop jobs.

### MapReduce

MapReduce distributes the processing of data on your cluster. Divides your data up intro partitions that are MAPPED (transformed) and REDUCED (aggregated) by mapper and reducer functions you define.

MapReduce is a programming model and an associated implementation for processing and generating big data sets with a parallel, distributed algorithm on a cluster.

A MapReduce program is composed of a map procedure (or method) - which performs filtering and sorting (such as sorting students by first name into queues, one queue for each name), and a reduce method - which performs a summary operation (such as counting the number of students in each queue, yielding name frequencies).

The "MapReduce System" (also called "infrastructure" or "framework") orchestrates the processing by marshalling the distributed servers, running the various tasks in parallel, managing all communications and data transfers between the various parts of the system, and providing for redundancy and fault tolerance.

> In computer science, **marshalling** is the process of transforming the memory representation of an object to a data format suitable for storage or transmission, and it is typically used when data must be moved between different parts of a computer program or from one program to another. Marshalling is similar to serialization and is used to communicate to remote objects with an object, in this case a serialized object.

### HDFS (Hadoop Distributed File System)

The HDFS, distributed under Apache license offers a basic framework for splitting up data collections between multiple nodes. In HDFS, the large files are broken into blocks, where several nodes hold all of the blocks from a file. The file system is designed in a way to mix fault tolerance with high throughput. The blocks of HDFS are loaded to maintain steady streaming. They are not usually cached to minimize latency.

### Pig

When the data stored is visible to Hadoop, Apache Pig dives into the data and runs the code that is written in its own language, called Pig Latin. Pig Latin is filled with abstractions for handling the data. Pig comes with standard functions for common tasks like averaging data, working with dates, or to find differences between strings. Pig also allows the user to write languages of their own, called UDF (User Defined Function), when the standard functions fall short.

### Hive

If you are already fluent with SQL, then you can leverage Hadoop using Hive. Hive was developed by some folks at Facebook. Apache Hive regulates the process of extracting bits from all the files in HBase. It supports analysis of large datasets stored in Hadoop’s HDFS and compatible file systems. It also provides an SQL like language called HSQL (HiveSQL) that gets into the files and extracts the required snippets for the code.

### TEZ

A Framework for YARN-based, Data Processing Applications in Hadoop.

Apache Tez is an extensible framework for building high performance batch and interactive data processing applications, coordinated by YARN in Apache Hadoop. Tez improves the MapReduce paradigm by dramatically improving its speed, while maintaining MapReduce’s ability to scale to petabytes of data. Important Hadoop ecosystem projects like Apache Hive and Apache Pig use Apache Tez.

### Spark

Spark is the next generation that pretty much works like Hadoop that processes data cached in the memory. Its objective is to make data analysis fast to run and write with a general execution model. This can optimize arbitrary operator graphs and support in-memory computing, which lets it query data faster than disk-based engines like Hadoop.

It also supports streaming data, run ML algorithms on clusters.

### HBase

HBase is a column-oriented database management system that runs on top of HDFS. HBase applications are written in Java, very much like the MapReduce application. It comprises a set of tables, where each table contains rows and columns like a traditional database. When the data falls into the big table, HBase will store the data, search it and automatically share the table across multiple nodes so that MapReduce jobs can run it locally. HBase offers a limited guarantee for some local changes. The changes that happen in a single row can succeed or fail at the same time.

It has a dynamic data model and not a relational DBMS.

### Storm

A system for processing streaming data in real time.

Apache Storm adds reliable real-time data processing capabilities to Enterprise Hadoop. Storm on YARN is powerful for scenarios requiring real-time analytics, machine learning and continuous monitoring of operations.

### NoSQL

Some Hadoop clusters integrate with NoSQL data stores that come with their own mechanisms for storing data across a cluster of nodes. This allows them to store and retrieve data with all the features of the NoSQL database, after which Hadoop can be used to schedule data analysis jobs on the same cluster.

### Mahout

Mahout is designed to implement a great number of algorithms, classifications and filtering of data analysis to Hadoop cluster. Many of the standard algorithms like K-means, Dirichelet, parallel pattern and Bayesian classifications are ready to run on the data with a Hadoop style Map and reduce.

### Lucene/Solr

Lucene, written in Java integrates easily with Hadoop and is a natural companion for Hadoop. It is a tool meant for indexing large blocks of unstructured text. Lucene handles the indexing, while Hadoop handles the distributed queries across the cluster. Lucene-Hadoop features are rapidly evolving as new projects are being developed.

### Avro

Avro is a serialization system that bundles the data together with a schema for understanding it. Each packet comes with a JSON data structure. JSON explains how the data can be parsed. The header of JSON specifies the structure for the data, where the need to write extra tags in the data to mark the fields can be avoided. The output is considerably more compact than the traditional formats like XML.

### Oozie

A job can be simplified by breaking it into steps. On breaking the project in to multiple Hadoop jobs, Oozie starts processing them in the right sequence. It manages the workflow as specified by DAG (Directed Acyclic Graph) and there is no need for timely monitor.

### Sqoop

Apache Sqoop is specially designed to transfer bulk data efficiently from the traditional databases into Hive or HBase. It can also be used to extract data from Hadoop and export it to external structured data-stores like relational databases and enterprise data warehouses. Sqoop is a command line tool, mapping between the tables and the data storage layer, translating the tables into a configurable combination of HDFS, HBase or Hive.

### Flume

Gathering all the data is equal to storing and analyzing it. Apache Flume dispatches ‘special agents’ to gather information that will be stored in HDFS. The information gathered can be log files, Twitter API, or website scraps. These data can be chained and subjected to analyses.

### Kafka

Apache Kafka is an open-source stream-processing software. It aims to provide a unified, high-throughput, low-latency platform for handling real-time data feeds. Its storage layer is essentially a "massively scalable pub/sub message queue designed as a distributed transaction log".

### Zookeeper

Zookeeper is a centralized service that maintains, configures information, gives a name and provides distributed synchronization across a cluster. It imposes a file system-like hierarchy on the cluster and stores all of the metadata for the machines, so we can synchronize the work of the various machines.
