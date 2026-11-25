## Starting and Stopping Cluster Nodes or Oracle Clusterware Resources

Before shutting down Oracle Clusterware 19c, if you have an Oracle Database 12c Release 1 (12.1) or Oracle Database 11g Release 2 (11.2) database registered with Oracle Clusterware 19c, then you must perform additional steps to ensure the resources are stopped.

1.  If you have an Oracle Database 12c Release 1 (12.1) or Oracle Database 11g Release 2 (11.2) database registered with Oracle Clusterware 19c, then perform one of the following steps:
    1.  Stop the Oracle database instances of the earlier releases first, then stop the Oracle Clusterware stack.
    2.  Use the `crsctl stop crs -f` command to shut down the Oracle Clusterware stack and ignore any errors that are raised.
2.  If you need to shut down a cluster node that currently has Oracle Database and Oracle Grid Infrastructure running on that node, then you must perform the following steps to cleanly shutdown the cluster node:
    1.  Use the `crsctl stop crs` command to shut down the Oracle Clusterware stack.
    2.  After Oracle Clusterware has been stopped, you can shutdown the Windows server using `shutdown -r`.

**Parent topic:** [Using Earlier Oracle Database Releases with Grid Infrastructure](using-earlier-oracle-database-releases-with-grid-infrastructure.md)
