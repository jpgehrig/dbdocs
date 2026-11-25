Learn how to install and configure a database for Data Mining.

- About Installation

- Enabling or Disabling a Database Option

- Database Tuning Considerations for Data Mining

### 34.1.1 About Installation

Oracle Data Mining is a component of the Oracle Advanced Analytics option to Oracle Database Enterprise Edition.

To install Oracle Database, follow the installation instructions for your platform. Choose a Data Warehousing configuration during the installation.

Oracle Data Miner, the graphical user interface to Oracle Data Mining, is an extension to Oracle SQL Developer. Instructions for downloading SQL Developer and installing the Data Miner repository are available on the Oracle Technology Network.

To perform data mining activities, you must be able to log on to the Oracle database, and your user ID must have the database privileges described in [Example 34-7](controlling-access-mining-models-data.md).

**Related Topics**

- [`Oracle Data Miner`](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/dmapi&id=dataminer_wf)

**See Also:**

Install and Upgrade page of the Oracle Database online documentation library for your platform-specific installation instructions: [`Oracle Database 18c Release`](../index.md)

### 34.1.2 Enabling or Disabling a Database Option

Learn how you can enable or disable Oracle Advanced Analytics option after the installation.

The Oracle Advanced Analytics option is enabled by default during installation of Oracle Database Enterprise Edition. After installation, you can use the command-line utility `chopt` to enable or disable a database option. For instructions, see "Enabling and Disabling Database Options After Installation" in the installation guide for your platform.

**Related Topics**

- [Oracle Database Installation Guide for Linux](../ladbi/enabling-and-disabling-oracle-database-options-after-installation.md)
- [Oracle Database Installation Guide for Microsoft Windows](../ntdbi/enabling-and-disabling-database-options-after-installation.md)

### 34.1.3 Database Tuning Considerations for Data Mining

Understand the Database tuning considerations for Data Mining.

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
