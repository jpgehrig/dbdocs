This deployment scenario consists of multiple servers, on which you install Oracle Real Application Clusters (Oracle RAC) in the global zone.

1.  Create the` rac_framework` resource to support the installation of Oracle Grid Infrastructure. See [Registering and Configuring the RAC Framework Resource Group](http://www.oracle.com/pls/topic/lookup?ctx=cluster4&id=CLRACch8_ops-1).
2.  Create the storage framework resource, if necessary, and any required storage resources.
    See [Creating Storage Management Resources](http://www.oracle.com/pls/topic/lookup?ctx=cluster4&id=CLRACgavve) .
    You can also configure storage resources by running the `clsetup` utility from a global cluster node and follow the steps in the wizard. See [Registering and Configuring Storage Resources for Oracle Files](http://www.oracle.com/pls/topic/lookup?ctx=cluster4&id=CLRACgavuk)
3.  Prepare the environment and then install and configure Oracle Grid Infrastructure as described these topics:
    - See [Configuring Users, Groups and Environments for Oracle Grid Infrastructure and Oracle Database](configuring-users-groups-and-environments-for-oracle-grid-infrastructure-and-oracle-database.md) for information about configuring users, groups, and environments before installing Oracle Grid Infrastructure.
    - See [Configuring Storage for Oracle Grid Infrastructure](configuring-storage-for-oracle-grid-infrastructure-for-a-cluster.md) for information about configuring storage for Oracle RAC Database.
    - See [Installing Oracle Grid Infrastructure](installing-oracle-grid-infrastructure.md) for information about installing Oracle Grid Infrastructure.
4.  Install and configure Oracle RAC Database as described in [Oracle Real Application Clusters Installation Guide](../install-and-upgrade.md).
5.  Create the `crs_framework` and `rac_server_proxy` resources for the Oracle RAC database as described in [Configuring Resources for Oracle RAC Database Instances](http://www.oracle.com/pls/topic/lookup?ctx=cluster4&id=CLRACgavuo).
    The `crs_framework` resource type enables Oracle Solaris Cluster and Oracle Clusterware to inter-operate by enabling Oracle Solaris Cluster to stop Oracle Clusterware. The `rac_server_proxy` resource is a proxy resource for the Oracle RAC database server.
6.  From a global cluster node, verify the Oracle RAC framework resources:
        # clresource status

**Parent topic:** [Deploying Oracle RAC on Oracle Solaris Cluster Zone Clusters](deploying-oracle-rac-on-oracle-solaris-cluster-zone-clusters.md)
