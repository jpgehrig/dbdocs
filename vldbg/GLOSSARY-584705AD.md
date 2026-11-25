### automatic data optimization

Automatic data optimization (ADO) is a component of Information Lifecycle Management (ILM) that automates the compression and movement of data between different tiers of storage within the database.

### composite partitioning

Composite partitioning is a combination of the basic data distribution methods. After a table is partitioned by a data distribution method, then each partition is subdivided into subpartitions using the same or a different data distribution method.

### degree of parallelism (DOP)

The degree of parallelism (DOP) is the number of parallel execution (PX) servers associated with a single operation.

### distribution method (parallel execution)

A distribution method is the method by which data is sent, or redistributed, from one parallel execution (PX) server set to another.

### hash partitioning

Hash partitioning maps data to partitions based on a hashing algorithm that Oracle applies to the partitioning key that you identify.

### heat map

Heat map is a component of Information Lifecycle Management (ILM) that tracks data access at the segment-level and data modification at the segment and row level.

### Information Lifecycle Management

Information Lifecycle Management (ILM) is a set of processes and policies for managing data throughout its useful life.

### list partitioning

List partitioning maps rows to partitions by specifying a list of discrete values for the partitioning key in the description for each partition.

### parallel execution (PX)

Parallel execution (PX) is the ability to apply multiple CPU and I/O resources to the execution of a single SQL statement with the use of multiple processes.

### parallel execution server

The parallel execution (PX) servers are the individual processes that perform work in parallel on behalf of the initiating session.

### parallelism

Parallelism is breaking down a task so that many processes simultaneously do part of the work in a query, rather than one process doing all of the work.

### partition pruning

Partition pruning occurs when the results of a query can be achieved by accessing a subset of partitions, rather than the entire table.

### partitioning

Partitioning is the process of subdividing objects, such as tables and indexes, into smaller and more manageable pieces.

### partitioning key

The partitioning key consists of one or more columns that determine the partition where each row is stored.

### query coordinator (QC)

The query coordinator (QC), or also called the parallel execution (PX) coordinator, is the session that initiates the parallel SQL statement.

### range partitioning

Range partitioning maps data to partitions based on ranges of values of the partitioning key that have been specified for each partition.

### very large database (VLDB)

A very large database is a database that contains a very large number of rows, or occupies an extremely large physical storage space.
