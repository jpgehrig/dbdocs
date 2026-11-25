An Oracle Flex Cluster scales Oracle Clusterware to large numbers of nodes.

This chapter includes the following topics:

- Overview of Oracle Flex Clusters

- Managing Oracle Flex Clusters

- Oracle Extended Clusters

### Overview of Oracle Flex Clusters

Oracle Grid Infrastructure installed in an Oracle Flex Cluster configuration is a scalable, dynamic, robust network of nodes.

Oracle Flex Clusters provide a platform for a variety of applications, including Oracle Real Application Clusters (Oracle RAC) databases with large numbers of nodes. Oracle Flex Clusters also provide a platform for other service deployments that require coordination and automation for high availability.

All nodes in an Oracle Flex Cluster belong to a single Oracle Grid Infrastructure cluster. This architecture centralizes policy decisions for deployment of resources based on application needs, to account for various service levels, loads, failure responses, and recovery.

Oracle Flex Clusters contain [Hub Node](glossary.md)s and any number of other supported nodes. The number of Hub Nodes in an Oracle Flex Cluster can be as many as 64. The number of other nodes can be many more. Hub Nodes can host different types of applications.

Hub Nodes are similar to Oracle Grid Infrastructure nodes in an Oracle Clusterware standard Cluster configuration: they are tightly connected, and have direct access to shared storage. Use Hub Nodes to host read-write database instances.

Other supported nodes in an Oracle Flex Cluster are different from standard Oracle Grid Infrastructure nodes, in that they do not require direct access to shared storage, but instead request data through Hub Nodes. Use other nodes to host read-only database instances.

**Note:**

Read-write and read-only database instances of the same primary database can coexist in an Oracle Flex Cluster.

Hub Nodes can run in an Oracle Flex Cluster configuration without having any other nodes as cluster member nodes, but other nodes must be members of a cluster that includes at least one Hub Node.

**Note:**

If you upgrade an Oracle Flex Cluster, then Oracle recommends that you upgrade the Hub Nodes first, and that you also have any upgraded Hub Nodes up and running as part of the upgrade process.

#### Reader Nodes

You can use other nodes to host Oracle RAC database instances that run in read-only mode, which become [reader node](glossary.md)s. You can optimize these nodes for parallel query operations by provisioning nodes with a large amount of memory so that data is cached in the hosting node.

A hosting node sends periodic heartbeat messages to its associated Hub Node, which is different from the heartbeat messages that occur between Hub Nodes. During planned shutdown of the Hub Nodes, a hosting node attempts to connect to another Hub Node, unless the hosting node is connected to only one Hub Node. If the Hub Node is evicted, then the hosting node is also evicted from the cluster.

### Managing Oracle Flex Clusters

Use CRSCTL to manage Oracle Flex Clusters after successful installation of Oracle Grid Infrastructure for either a small or large cluster.

This section includes the following topics:

- Changing the Cluster Mode

**Related Topics**

- [Oracle Grid Infrastructure Installation and Upgrade Guide](../install-and-upgrade.md)
- [Oracle Clusterware Control (CRSCTL) Utility Reference](oracle-clusterware-control-crsctl-utility-reference.md)

#### Changing the Cluster Mode

You can change the mode of an existing Oracle Clusterware standard Cluster to be an Oracle Flex Cluster.

**Note:**

- Changing the cluster mode requires cluster downtime.

- Oracle does not support changing an Oracle Flex Cluster to an Oracle Clusterware standard Cluster.

- Oracle Flex Cluster requires Grid Naming Service (GNS).

- Zone delegation is not required.

##### Changing an Oracle Clusterware Standard Cluster to an Oracle Flex Cluster

Use CRSCTL to change an existing Oracle Clusterware standard Cluster to an Oracle Flex Cluster.

Perform the following steps:

1.  Run the following command to determine the current mode of the cluster:

        $ crsctl get cluster mode status

2.  Run the following command to ensure that the Grid Naming Service (GNS) is configured with a fixed VIP:

        $ srvctl config gns

    This procedure cannot succeed unless GNS is configured with a fixed VIP. If there is no GNS, then, as `root`, create one, as follows:

        # srvctl add gns -vip vip_name | ip_address

    Run the following command as `root` to start GNS:

        # srvctl start gns

3.  Use the Oracle Automatic Storage Management Configuration Assistant (ASMCA) to enable Oracle Flex ASM in the cluster before you change the cluster mode.

4.  Run the following command as `root` to change the mode of the cluster to be an Oracle Flex Cluster:

        # crsctl set cluster mode flex

5.  Stop Oracle Clusterware by running the following command as `root` on each node in the cluster:

        # crsctl stop crs

6.  Start Oracle Clusterware by running the following command as `root` on each node in the cluster:

        # crsctl start crs -wait

    **Note:**

    Use the `-wait` option to display progress and status messages.

**Related Topics**

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/manage-flex-asm.md)

### Oracle Extended Clusters

You can extend an Oracle RAC cluster across two, or more, geographically separate sites, each equipped with its own storage. In the event that one of the sites fails, the other site acts as an active standby.

Both Oracle ASM and the Oracle Database stack, in general, are designed to use enterprise-class shared storage in a data center. Fibre Channel technology, however, enables you to distribute compute and storage resources across two or more data centers, and connect them through ethernet cables and Fibre Channel, for compute and storage needs, respectively.

While you can configure Oracle Extended Clusters when you install Oracle Grid Infrastructure, you can also do so post installation using the `ConvertToExtended` script. You manage your Oracle Extended Cluster using CRSCTL.

#### Converting to Oracle Extended Cluster

This procedure is only supported for clusters that have been installed with or upgraded to Oracle Grid Infrastructure 12c release 2 (12.2), or later, which are typically configured with one site (default site).

**Note:**

This procedure requires that all nodes in the cluster be accessible.

You can configure an Oracle Extended Cluster with one or many disk groups and with multiple failure groups. Using the `converttoextended` script you can create multiple data sites and associate a node with each data site. All Oracle Flex ASM storage remains associated with the default cluster site because there is no mechanism to convert an existing disk group to an extended disk group. After you convert your cluster to an Oracle Extended Cluster, the voting file membership remains flat, and not hierarchical.

You must also add an extended disk group, and migrate the voting files to the extended disk group to take advantage of a site-specific hierarchical voting file algorithm.

Use CRSCTL to query the cluster, as follows, to determine its extended status:

    $ crsctl get cluster extended
    CRS-6579: "The cluster is 'NOT EXTENDED'"

    $ crsctl query cluster site -all
    Site 'crsclus' identified by '7b7b3bef4c1f5ff9ff8765bceb45433a' in state 'ENABLED',
     and contains nodes 'node1,node2,node3,node4', and disks ''.

The preceding example identifies a cluster called `crsclus` that has four nodes—`node1`, `node2`, `node3`, and `node4`—and a disk group—`datadg`. The cluster has one site configured.

1.  As the `root` user, perform a complete backup of the OCR and voting files.
        # ocrconfig -manualbackup
2.  Log in to the first node, and run the following command.
        # rootcrs.sh -converttoextended -first -sites list_of_sites -site node_site

    list_of_sites is the comma-separated list of sites in the extended cluster and node_site is the name of the site with which the local node is associated.

    **Note:**

    The node on which you are running the `converttoextended` command becomes unavailable, which may disrupt the database access.
3.  Run the following command on all other cluster nodes:
        # rootcrs.sh -converttoextended -site node_site

    node_site is the name of the site with which the local node is associated.

    **Note:**

    The node on which you are running the `converttoextended` command becomes unavailable, which may disrupt the database access.
4.  Delete the default site after the associated nodes and storage are migrated.
        # crsctl delete cluster site site_name
5.  Associate every Oracle ASM disk with a site by using the `ALTER DISKGROUP` SQL statement as the SYSASM user on the Oracle ASM instance after mounting the disk groups in restricted mode.
        SQL> ALTER DISKGROUP diskgroup_name RENAME DISK disk_name SITE site_name;

    **Note:**

    If a disk group contains Oracle Clusterware data, like voting files and the Oracle ASM SPFILE, then use the standard procedure for migrating the voting files and the Oracle ASM SPFILE to a different disk group, before the site assignment for the disks. For a disk group to store voting files, a normal redundancy disk group requires a minimum of three disk devices. You can migrate voting files and the Oracle ASM SPFILE back to the original disk group after the site assignment for the disks in the disk group.
    After the disk groups are modified successfully, you can remount the disk groups in normal mode.

After you finish configuring the Oracle Extended Cluster, run the following command to verify the configuration:

    $ crsctl get cluster extended
    CRS-XXXX: "The cluster is 'EXTENDED'"

    $ crsctl query cluster site -all
    Site 'la' identified by GUID '7b7b3bef4c1f5ff9ff8765bceb45433a' in state 'ENABLED' contains nodes 'node1,node2' and disks 'disk1, disk2, disk3'.
    Site 'ny' identified by GUID '888b3bef4c1f5ff9ff8765bceb45433a' in state 'ENABLED' contains nodes 'node3,node4' and disks 'disk4, disk5, disk6'.
    Site 'nj' identified by GUID '999b3bef4c1f5ff9ff8765bceb45433a' in state 'ENABLED' contains nodes 'node5,node6' and disks 'disk7, disk8, disk9'.
