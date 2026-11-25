## Requirements and Guidelines for Oracle Memory Speed

Review these requirements and guidelines before you deploy Oracle Memory Speed (OMS) as your file system.

### Requirements

- An Intel Cascade Lake or Intel Ice Lake based server or later. Ice Lake based servers implement enhanced CPU cache flushing algorithms that may potentially improve PMEM performance.
- Persistent Memory Devices (PMEM) in each socket capable of memory interleaving. You should populate the PMEM DIMMs and the DRAM DIMMs in the memory channels per Intel guidelines.
- Oracle Linux with HugePages support starting with kernel UEK5.
- A Direct Access (DAX-capable) file system such as XFS.

### Guidelines

- Oracle supports the OMS file system only for single instance Oracle Database deployments. To protect the data created by your single-instance Oracle Database, Oracle recommends that you configure Oracle Data Guard. Oracle Data Guard ensures that if there is any error in the primary instance, the database can fail over to the standby database. See the Oracle Data Guard Concepts and Administration for more information.

**Related Topics**

- [Oracle Data Guard Concepts and Administration](../sbydb/getting-started-with-oracle-data-guard.md)

**Parent topic:** [Deploying the Oracle Memory Speed File System](deploying_oms.md)
