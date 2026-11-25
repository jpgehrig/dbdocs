## Creating a Fleet Patching and Provisioning Client

Users operate on a Fleet Patching and Provisioning Client to perform tasks such as requesting deployment of Oracle homes and querying gold images.

1.  On the Fleet Patching and Provisioning Server as the Grid home owner, create the client data file, as follows:
        $ rhpctl add client -client client_cluster_name [-clusternamealias
        cluster_name_alias] -toclientdata path

    RHPCTL creates the client data file in the directory path you specify after the `-toclientdata` flag. The name of the client data file is `client_cluster_name``.xml`.

    **Note:**

    Oracle recommends that you specify a unique `client_cluster_name` and it must match the cluster name of the client cluster where you run step 4. If the client cluster name is not unique, then you can specify a cluster name alias.
2.  Copy the client data file that you created in the previous step to a directory on the client cluster that has read/write permissions to the Grid home owner on the Fleet Patching and Provisioning Client.
3.  Create the Fleet Patching and Provisioning Client by running the following command as `root` on the client cluster:
        # srvctl add rhpclient -clientdata path_to_client_data
           [-diskgroup disk_group_name -storage base_path]

    If you want to provision working copies to Oracle ACFS storage on this cluster, and you have already created a disk group for this purpose, then specify this disk group in the preceding command. In this case, also specify a storage path which will be used as a base path for all mount points when creating Oracle ACFS file systems for storing working copies.

    **Note:**

    Once you configure a disk group on a Fleet Patching and Provisioning Client, you cannot remove it from or change it in the Fleet Patching and Provisioning Client configuration. The only way you can do either (change or remove) is to completely remove the Fleet Patching and Provisioning Client using the `srvctl remove client` command, and then add it back with a different disk group, if necessary. Before you remove a Fleet Patching and Provisioning Client, ensure that you remove all registered users from this cluster and all working copies provisioned on this cluster.
4.  Start the Fleet Patching and Provisioning Client, as follows:
        $ srvctl start rhpclient
5.  Check the status of the Fleet Patching and Provisioning Client, as follows:
        $ srvctl status rhpclient

**Related Topics**

- [Oracle Clusterware Administration and Deployment Guide](../cwadd/server-control-command-reference.md)
- [RHPCTL Command Reference](fleet-patching-provisioning-commands.md)

**Parent topic:** [Configuring Oracle Fleet Patching and Provisioning Clients](configuring-oracle-fpp-clients.md)
