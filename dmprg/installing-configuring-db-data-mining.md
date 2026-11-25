You can install and configure a database for Oracle Data Mining for SQL by following the listed steps.

- About Installation

- Database Tuning Considerations for Data Mining

### 8.1.1 About Installation

Oracle Data Mining components associated with Oracle Database are included with the database license. This includes Oracle Database Enterprise Edition and Oracle Database Standard Edition 2. Install the 19.9 bundle patch if you want to use Oracle Database Standard Edition 2.

To install Oracle Database, follow the installation instructions for your platform. Choose a Data Warehousing configuration during the installation.

Oracle Data Miner, the graphical user interface to Oracle Data Mining, is an extension to Oracle SQL Developer. Instructions for downloading SQL Developer and installing the Data Miner repository are available on the [Oracle Technology Network](https://www.oracle.com/database/technologies/odmrinstallation.html).

To perform data mining activities, you must be able to log on to the Oracle database, and your user ID must have the database privileges described in [Example 8-7](controlling-access-mining-models-data.md).

**Related Topics**

- [`Oracle Data Miner`](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/dmprg&id=dataminer_wf)

**See Also:**

Install and Upgrade page of the Oracle Database online documentation library for your platform-specific installation instructions: [`Oracle Database 19c Release`](../index.md)

### 8.1.2 Database Tuning Considerations for Data Mining

Standard administrative practices can be followed to manage workload on the system when data mining activities are running.

DBAs managing production databases that support Oracle Data Mining must follow standard administrative practices as described in Oracle Database Administrator’s Guide.

Building data mining models and batch scoring of mining models tend to put a DSS-like workload on the system. Single-row scoring tends to put an OLTP-like workload on the system.

Database memory management can have a major impact on data mining. The correct sizing of Program Global Area (PGA) memory is very important for model building, complex queries, and batch scoring. From a data mining perspective, the System Global Area (SGA) is generally less of a concern. However, the SGA must be sized to accommodate real-time scoring, which loads models into the shared cursor in the SGA. In most cases, you can configure the database to manage memory automatically. To do so, specify the total maximum memory size in the tuning parameter `MEMORY_TARGET`. With automatic memory management, Oracle Database dynamically exchanges memory between the SGA and the instance PGA as needed to meet processing demands.

Most data mining algorithms can take advantage of parallel execution when it is enabled in the database. Parameters in `INIT.ORA` control the behavior of parallel execution.

**Related Topics**

- [Oracle Database Administrator’s Guide](../admin/basic-database-administration.md)
- [Scoring and Deployment](scoring-deployment.md)
- [Oracle Database Administrator’s Guide](../admin/managing-memory.md)
- [Part I Database Performance Fundamentals](../tgdba/part-I-database-performance-fundamentals.md)
- [Tuning Database Memory](../tgdba/part-III-tuning-database-memory.md)
- [Oracle Database VLDB and Partitioning Guide](../vldbg/using-parallel.md)
