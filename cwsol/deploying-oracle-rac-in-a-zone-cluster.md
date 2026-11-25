In this deployment scenario, you can install Oracle Real Application Clusters (Oracle RAC) in a zone cluster. A zone cluster is a cluster of Oracle Solaris non-global zones.

1.  Plan and create a zone cluster as described in the following links:
    - [Planning the Oracle Solaris Cluster Configuration](http://www.oracle.com/pls/topic/lookup?ctx=cluster4&id=CLISTghbof)

    - [Creating Zone Clusters](http://www.oracle.com/pls/topic/lookup?ctx=cluster4&id=CLISTgjbcb)
2.  As `root`, create an Oracle RAC infrastructure in the zone cluster as follows:
    1.  Run the `clsetup` utility from a global cluster node and follow the steps in the wizard.
    2.  From a global cluster node, verify the Oracle RAC framework resources:
            # clresource status -Z zone_name
3.  Prepare the environment and then install and configure Oracle Grid Infrastructure and Oracle Database.
    See [Configuring Users, Groups and Environments for Oracle Grid Infrastructure and Oracle Database](configuring-users-groups-and-environments-for-oracle-grid-infrastructure-and-oracle-database.md) for information about configuring users, groups, and environments.
    See [Installing Oracle Grid Infrastructure](installing-oracle-grid-infrastructure.md) for information about installing Oracle Grid Infrastructure.
    See [Oracle Real Application Clusters Installation Guide](../install-and-upgrade.md) for information about installing Oracle RAC databases.
4.  Create Oracle Solaris Cluster resources, link them, and bring them online as described in [Configuring Resources for Oracle RAC Database Instances](http://www.oracle.com/pls/topic/lookup?ctx=cluster4&id=CLRACgavuo).

**Parent topic:** [Deploying Oracle RAC on Oracle Solaris Cluster Zone Clusters](deploying-oracle-rac-on-oracle-solaris-cluster-zone-clusters.md)
