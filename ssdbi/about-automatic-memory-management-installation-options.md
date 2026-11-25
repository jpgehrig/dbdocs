Decide if you want to configure Automatic Memory Management during installation.

During a Typical installation, you create your database with Database Configuration Assistant (DBCA), and automatic memory management is enabled. If you choose advanced installation, then you can either specify memory allocation manually, or enable automatic memory management.

With automatic memory management, the Oracle Database instances automatically manage and tune memory for you. With automatic memory management, you choose a memory target, and the instance automatically distributes memory between the system global area (SGA) and the instance program global area (instance PGA). As memory requirements change, the instance dynamically redistributes memory between the SGA and instance PGA.

You can enable automatic memory management either during, or after the database installation. Enabling automatic memory management after installation involves a shutdown and restart of the database.

Starting with 12c, Oracle Database uses the Optimized Shared Memory (OSM) model of Oracle Solaris on Oracle Solaris 10 1/13 or later and Oracle Solaris 11 SRU 7.5 or later systems to implement Automatic Memory Management. However, Oracle Database 12c continues to use Intimate Shared Memory (ISM) or Dynamic Intimate Shared Memory (DISM) on systems where OSM is not available.

[Oracle Database Administrator's Reference for Linux and UNIX-Based Operating Systems](../unxar/index.md)

[Oracle Database Administrator’s Guide](../admin/managing-memory.md)

**Parent topic:** [Installing Oracle Database](installing-oracle-database.md)
