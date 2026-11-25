After Oracle Grid Infrastructure installation, confirm that your Oracle Clusterware installation is installed and running correctly.

After installation, log in as `root`, and use the following command syntax to confirm that your Oracle Clusterware installation is installed and running correctly:

    crsctl check cluster -all

For example:

    $ crsctl check cluster -all

    **************************************************************
    node1:
    CRS-4537: Cluster Ready Services is online
    CRS-4529: Cluster Synchronization Services is online
    CRS-4533: Event Manager is online
    **************************************************************
    node2:
    CRS-4537: Cluster Ready Services is online
    CRS-4529: Cluster Synchronization Services is online
    CRS-4533: Event Manager is online
    **************************************************************
    node3:
    CRS-4537: Cluster Ready Services is online
    CRS-4529: Cluster Synchronization Services is online
    CRS-4533: Event Manager is online
    **************************************************************

**Note:**

After installation is complete, do not remove manually or run `cron` jobs that remove `/tmp/.oracle` or `/var/tmp/.oracle` or its files while Oracle Clusterware is up. If you remove these files, then Oracle Clusterware could encounter intermittent hangs, and you will encounter error `CRS-0184: Cannot communicate with the CRS daemon`.

**Parent topic:** [Installing Oracle Grid Infrastructure](installing-oracle-grid-infrastructure.md)
