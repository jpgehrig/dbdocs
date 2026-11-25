## Creating and Using a GNS Client Data File

Generate a GNS client data file and copy the file to the GNS client cluster member node on which you are running the Oracle Grid Infrastructure installation.

1.  On a GNS Server cluster member, run the following command, where path_to_file is the name and path location of the GNS Client data file you create:
        srvctl export gns -clientdata path_to_file -role {client | secondary}

    For example:

        C:\> srvctl export gns -clientdata C:\Users\grid\gns_client_data -role client
2.  Copy the GNS Client data file to a secure path on the GNS Client node where you run the GNS Client cluster installation.
    The Oracle Installation user must have permissions to access that file. Oracle recommends that no other user is granted permissions to access the GNS Client data file.
3.  During installation, you are prompted to provide a path to that file.
4.  After you have completed the GNS Client cluster installation, you must run the following command on one of the GNS Server cluster members to start GNS service, where path_to_file is the name and path location of the GNS Client data file:
        srvctl add gns -clientdata path_to_file

    For example:

        C:\> srvctl add gns -clientdata C:\Users\grid\gns_client_data

**Related Topics**

- [Oracle Clusterware Administration and Deployment Guide](../cwadd/oracle-clusterware-administration.md)

**Parent topic:** [IP Name and Address Requirements For Multi-Cluster GNS](ip-name-and-address-requirements-for-multi-cluster-gns.md)
