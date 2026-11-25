## About Automatic Memory Management Installation Options

Decide if you want to configure Automatic Memory Management during installation.

During a Typical installation, you create your database with Oracle Database Configuration Assistant (DBCA), and automatic memory management is enabled. If you choose Advanced installation, then you can either specify memory allocation manually, or enable automatic memory management.

If the total physical memory of your database instance is greater than 4 GB, then you cannot select the Oracle Automatic Memory Management option during database installation and creation. Instead, use automatic shared memory management. Automatic shared memory management automatically distributes the available memory among the various components as required, allowing the system to maximize the use of all available SGA memory.

With automatic memory management, the Oracle Database instances automatically manage and tune memory for you. With automatic memory management, you choose a memory target, and the instance automatically distributes memory between the system global area (SGA) and the instance program global area (instance PGA). As memory requirements change, the instance dynamically redistributes memory between the SGA and instance PGA.

You can enable automatic memory management either during, or after the database installation. Enabling automatic memory management after installation involves a shutdown and restart of the database.

**Note:**

By default, automatic memory management is disabled when you perform typical installation on a node that has more than 4 GB of RAM.

**Related Topics**

- [Oracle Database Administrator’s Guide](../admin/managing-memory.md)

**Parent topic:** [Installing Oracle Database](installing-oracle-database.md)
