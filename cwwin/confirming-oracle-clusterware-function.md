## Confirming Oracle Clusterware Function

After installation, use the `crsctl` utility to verify Oracle Clusterware installation is installed and running correctly.

- Log in as a member of the Administrators group, and run the following command from the `bin` directory in the Grid home:
      crsctl check cluster -all
- Run the following command to verify the status of all the configured resources:
      crsctl stat res -t

Example 9-2 Checking the Status of Oracle Clusterware

To check the status of the Oracle Clusterware components on each node of your cluster, run the following command:

    C:\..\bin\> crsctl check cluster -all

The output for this command is similar to the following:

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

**Parent topic:** [Installing Oracle Grid Infrastructure for a Cluster](installing-oracle-grid-infrastructure-for-a-cluster.md)
