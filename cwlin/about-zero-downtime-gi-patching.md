## About Zero-Downtime Oracle Grid Infrastructure Patching

Use the zero-downtime Oracle Grid Infrastructure patching method to keep your Oracle RAC database instances running and client connections active during patching.

Zero-downtime patching does not affect I/O for the Oracle Database storage. All instances of Oracle Automatic Storage Management Cluster File System (Oracle ACFS) remain mounted and accessible during patching. The database listeners that are running from the Oracle Database homes are not affected, however, the listeners that are running from the Oracle Grid Infrastructure home restart while patching Oracle Grid Infrastructure.

You can use zero-downtime patching only for out-of-place patching of Oracle Grid Infrastructure 19c Release Update (RU) 19.16 or later releases with Oracle RAC or Oracle RAC One Node databases of 19c or later releases. If your Oracle RAC or Oracle RAC One Node database release is older than 19c, then the database instances stop during zero-downtime patching.

**Note:**

The success of zero-downtime patching depends on the availability of the system resources. If sufficient system resources are not available and if the patching software estimates that Oracle Grid Infrastructure will remain shut down for more than 15 seconds, then the patching software stops the patching process. In this case, you need to patch Oracle Grid Infrastructure when sufficient system resources are available.

### Zero-Downtime Patching and Operating System Drivers

Zero-downtime patching does not automatically update the operating system drivers. During the zero-downtime patching process, updated operating system drivers are copied in the Grid home, but these drivers are not installed into the operating system. The cluster continues to use the older version of the operating system drivers until the updated drivers are installed in the operating system.

If you are using Oracle ACFS for database storage, then operating system drivers are updated in either of the following scenarios:

1.  You update your operating system kernel and restart the cluster node.
2.  You run the `rootcrs.sh -updateosfiles` command on each cluster node and restart the cluster nodes, if the operating system drivers fail to install.

You can check the active operating system driver version on a cluster node using the `crsctl query driver activeversion [-all]` command and available operating system driver version using the `crsctl query driver softwareversion [-all] [-f]` command.

If the patch that you are installing contains operating system driver updates, then you must use the `-skipDriverUpdate` option during zero-downtime patching, else the patching process fails. The `-skipDriverUpdate` option does not affect the existing operating system driver, even if the Release Update (RU) contains driver updates.

After you apply the patches using zero-downtime patching, the active and available operating system driver versions are different until either of the above two scenarios is true.

**Related Topics**

- [Oracle Automatic Storage Management Cluster File System Administrator's Guide](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/cwlin&id=ACFSG-GUID-E8C5D948-849B-4A7D-B5D7-29F9D792BDE0)

**Parent topic:** [Applying Patches to Oracle Grid Infrastructure](applying-patches-to-oracle-asm.md)
