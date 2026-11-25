Generate a GNS client data file and copy the file to the GNS client cluster member node on which you are running the Oracle Grid Infrastructure installation.

On a GNS server cluster member, run the following command, where `path_to_file` is the name and path location of the GNS client data file you create:

    srvctl export gns -clientdata path_to_file -role client

For example:

    $ srvctl export gns -clientdata /home/grid/gns_client_data -role client

Copy the GNS Client data file to a secure path on the GNS Client node where you run the GNS Client cluster installation. The Oracle installation user must have permissions to access that file. Oracle recommends that no other user is granted permissions to access the GNS Client data file. During installation, you are prompted to provide a path to that file.

    srvctl add gns -clientdata path_to_file

For example:

    $ srvctl add gns -clientdata /home/grid/gns_client_data

**Related Topics**

- [Oracle Clusterware Administration and Deployment Guide](../cwadd/oracle-clusterware-administration.md)

**Parent topic:** [IP Name and Address Requirements For Multi-Cluster GNS](ip-name-and-address-requirements-for-multi-cluster-gns.md)
