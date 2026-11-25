## About Migrating Existing Oracle ASM Instances

You can use Oracle Automatic Storage Management Configuration Assistant (ASMCA) to upgrade the existing Oracle ASM instance to Oracle ASM 12c release 1 (12.1) or higher.

ASMCA is located in the path `Grid_home``\bin`. You can also use ASMCA to configure failure groups, Oracle ASM volumes, and Oracle ACFS.

**Note:**

You must first shut down all database instances and applications on the node with the existing Oracle ASM instance before upgrading it.

During installation, if you chose to use Oracle ASM and ASMCA detects that there is a prior Oracle ASM release installed in another Oracle ASM home, then after installing the Oracle ASM 12c release 2 (12.2) software, you can start ASMCA to upgrade the existing Oracle ASM instance. You can then configure an Oracle ACFS deployment by creating Oracle ASM volumes and using the upgraded Oracle ASM to create the Oracle ACFS.

On an existing Oracle Clusterware or Oracle RAC installation, if the prior release of Oracle ASM instances on all nodes is Oracle ASM 11g release 1 or higher, then you are provided with the option to perform a rolling upgrade of Oracle ASM instances. If the prior release of Oracle ASM instances on an Oracle RAC installation are from an Oracle ASM release prior to Oracle ASM 11g release 1, then rolling upgrades cannot be performed. Oracle ASM is then upgraded on all nodes to 12c release 2 (12.2).

**Parent topic:** [Configuring Shared Storage for Oracle Database and Grid Infrastructure](configuring-storage-for-oracle-database-and-grid-infrastructure.md)
