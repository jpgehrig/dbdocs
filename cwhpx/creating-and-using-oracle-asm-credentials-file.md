Review this information to create an Oracle ASM credentials file.

An Oracle ASM Storage Client does not have Oracle ASM running on the nodes and uses Oracle ASM storage services in a different client cluster.

The Oracle ASM Client Cluster requires Grid Naming Service (GNS) to be configured in the Oracle ASM Server Cluster.

1.  Connect to any Oracle ASM instance as SYSASM user and execute the query:
        ALTER DISKGROUP data SET ATTRIBUTE 'access_control.enabled' = 'true';
2.  From the `Grid_home``/bin` directory on the Storage Server, run the following command on one of the member nodes, where `credential_file` is the name and path location of the Oracle ASM credentials file you create:
        Grid_home/bin/asmcmd mkcc client_cluster_name credential_file

    For example:

        Grid_home/bin/asmcmd mkcc clientcluster1 /home/grid/clientcluster1_credentials.xml
3.  Copy the Oracle ASM credentials file to a secure path on the client cluster node where you run the client cluster installation.
    The Oracle Installation user must have permissions to access that file. Oracle recommends that no other user is granted permissions to access the Oracle ASM credentials file. During installation, you are prompted to provide a path to the file.

    **Note:**

    - The Oracle ASM credentials file can be used only once. If an Oracle ASM Storage Client is configured and deconfigured, you must create a new Oracle ASM credentials file.

    - If the Oracle ASM credentials file is used to configure the client cluster, then it cannot be shared or reused to configure another client cluster.

**Parent topic:** [Configuring Storage for Oracle Grid Infrastructure](configuring-storage-for-oracle-grid-infrastructure-for-a-cluster.md)
