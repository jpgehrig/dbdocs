## Consider Memory Allocation and Automatic Memory Management

During a Typical installation, you create your database with Database Configuration Assistant (DBCA), and automatic memory management is enabled. If you choose advanced installation, then you can either specify memory allocation manually, or enable automatic memory management.

With automatic memory management, the Oracle Database instances automatically manage and tune memory for you. With automatic memory management, you choose a memory target, and the instance automatically distributes memory between the system global area (SGA) and the instance program global area (instance PGA). As memory requirements change, the instance dynamically redistributes memory between the SGA and instance PGA.

You can enable automatic memory management either during, or after the database installation. Enabling automatic memory management after installation involves a shutdown and restart of the database.

**See Also:**

[Oracle Database Administrator's Guide](../admin/managing-memory.md)

**Parent topic:** [Installation Considerations](installation-considerations.md)
