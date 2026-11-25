Very large databases (VLDBs) present administration challenges that require multiple strategies. Partitioning is a key component of the VLDB strategy.

Modern enterprises frequently run mission-critical databases containing upwards of several hundred gigabytes, and often several terabytes of data. These enterprises are challenged by the support and maintenance requirements of very large databases (VLDB), and must devise methods to meet those challenges.

This chapter contains the following sections:

- Introduction to Partitioning

- VLDB and Partitioning

- Partitioning As the Foundation for Information Lifecycle Management

- Partitioning for All Databases

**Note:**

Partitioning functionality is available only if you purchase the Oracle Partitioning option.

### 1.1 Introduction to Partitioning

Partitioning provides support for very large tables and indexes by subdividing them into smaller and more manageable pieces.

Partitioning addresses key issues in supporting very large tables and indexes by decomposing them into smaller and more manageable pieces called partitions, which are entirely transparent to an application. SQL queries and Data Manipulation Language (DML) statements do not need to be modified to access partitioned tables. However, after partitions are defined, data definition language (DDL) statements can access and manipulate individual partitions rather than entire tables or indexes. This is how partitioning can simplify the manageability of large database objects.

Each partition of a table or index must have the same logical attributes, such as column names, data types, and constraints, but each partition can have separate physical attributes, such as compression enabled or disabled, physical storage settings, and tablespaces.

Partitioning is useful for many different types of applications, particularly applications that manage large volumes of data. OLTP systems often benefit from improvements in manageability and availability, while data warehousing systems benefit from performance and manageability.

Partitioning offers these advantages:

- It enables data management operations such as data loads, index creation and rebuilding, and backup and recovery at the partition level, rather than on the entire table. This results in significantly reduced times for these operations.

- It improves query performance. Often the results of a query can be achieved by accessing a subset of partitions, rather than the entire table. For some queries, this technique (called partition pruning) can provide order-of-magnitude gains in performance.

- It significantly reduces the impact of scheduled downtime for maintenance operations.

  Partition independence for partition maintenance operations lets you perform concurrent maintenance operations on different partitions of the same table or index. You can also run concurrent `SELECT` and DML operations against partitions that are unaffected by maintenance operations.

- It increases the availability of mission-critical databases if critical tables and indexes are divided into partitions to reduce the maintenance windows, recovery times, and impact of failures.

- Parallel execution provides specific advantages to optimize resource utilization, and minimize execution time. Parallel execution is supported for queries and for DML and DDL.

Partitioning enables faster data access within Oracle Database. Whether a database has 10 GB or 10 TB of data, partitioning can improve data access by orders of magnitude. Partitioning can be implemented without requiring any modifications to your applications. For example, you could convert a nonpartitioned table to a partitioned table without needing to modify any of the `SELECT` statements or DML statements that access that table. You do not need to rewrite your application code to take advantage of partitioning.

### 1.2 VLDB and Partitioning

Partitioning is a valuable strategy for managing for very large databases (VLDBs).

A very large database has no minimum absolute size. Although a VLDB is a database like smaller databases, there are specific challenges in managing a VLDB. These challenges are related to the sheer size and the cost-effectiveness of performing operations against a system of that size.

Several trends have been responsible for the steady growth in database size:

- For a long time, systems have been developed in isolation. Companies have started to see the benefits of combining these systems to enable cross-departmental analysis while reducing system maintenance costs. Consolidation of databases and applications is a key factor in the ongoing growth of database size.

- Many companies face regulations for storing data for a minimum amount of time. The regulations generally result in more data being stored for longer periods of time.

- Companies grow by expanding sales and operations or through mergers and acquisitions, causing the amount of generated and processed data to increase. At the same time, the user population that relies on the database for daily activities increases.

Partitioning is a critical feature for managing very large databases. Growth is the basic challenge that partitioning addresses for very large databases, and partitioning enables a divide and conquer technique for managing the tables and indexes in the database, especially as those tables and indexes grow. Partitioning is the feature that allows a database to scale for very large data sets while maintaining consistent performance, without unduly increasing administrative or hardware resources.

**See Also:**

- [Partitioning for Availability, Manageability, and Performance](partition-availability.md) for information about availability, manageability, and performance considerations for partitioning implementations

- [Backing Up and Recovering VLDBs](vldb-backup.md) for information about the challenges surrounding backup and recovery for very large databases

- [Storage Management for VLDBs](vldb-storage.md) for information about best practices for storage, which is a key component of very large databases

### 1.3 Partitioning As the Foundation for Information Lifecycle Management

Partitioning provides support for Information Lifecycle Management (ILM).

Information Lifecycle Management (ILM) is a set of processes and policies for managing data throughout its useful life. One important component of an ILM strategy is determining the most appropriate and cost-effective medium for storing data at any point during its lifetime: newer data used in day-to-day operations is stored on the fastest, most highly-available storage tier, while older data which is accessed infrequently may be stored on a less expensive and less efficient storage tier. Older data may also be updated less frequently so it makes sense to compress and store the data as read-only.

Oracle Database provides the ideal environment for implementing your ILM solution. Oracle supports multiple storage tiers, and because all of the data remains in Oracle Database, multiple storage tiers are transparent to the application and the data continues to be secure. Partitioning provides the fundamental technology that enables data in tables to be stored in different partitions.

Although multiple storage tiers and sophisticated ILM policies are most often found in enterprise-level systems, most companies and most databases need some degree of information lifecycle management. The most basic of ILM operations, archiving older data and purging or removing that data from the database, can be orders of magnitude faster when using partitioning.

**See Also:**

[Managing and Maintaining Time-Based Information](time-based-info.md) for more information about ILM

### 1.4 Partitioning for All Databases

Partitioning provides benefits for large and small databases.

The benefits of partitioning are not just for very large databases; all databases, even small databases, can benefit from partitioning. Even a database whose size is measured in megabytes can gain the same type of performance and manageability benefits from partitioning as the largest multi-terabyte system.

**See Also:**

- [Using Partitioning in a Data Warehouse Environment](partition-warehouse.md) for more information about how partitioning can provide benefits in a data warehouse environment

- [Using Partitioning in an Online Transaction Processing Environment](partition-oltp.md) for more information about how partitioning can provide benefits in an OLTP environment
