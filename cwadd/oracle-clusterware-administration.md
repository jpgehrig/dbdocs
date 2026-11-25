Configuring and administering Oracle Clusterware and its various components involves managing applications and databases, and networking within a cluster.

You can choose from one of two methods of configuring and administering clusters. You can use the traditional, administrator-managed approach, where you administer cluster resources and workloads manually, or you can invoke varying degrees of automated administration using a policy-managed approach.

Administrator-managed clusters requires that you manually configure how the cluster resources are deployed and where the workload is managed. Typically, this means that must configure which database instances run on what cluster nodes, by preference, and where those instances will restart in case of failures. By configuring where the database instances reside, You configure the workloads across the cluster.

With policy-managed clusters, you configure the workloads to run in server pools, for which you configure policy sets to direct how those workloads are managed in each server pool. You manage the server pools and policy sets, leaving the details of the database instance location and workload placement to the policies they have instituted. In using this approach, you have the additional option of further automating the management of the cluster by using Oracle Quality of Service Management (Oracle QoS Management).

### Role-Separated Management

Role-separated management is an approach to managing cluster resources and workloads in a coordinated fashion in order to reduce the risks of resource conflicts and shortages.

Role-separated management uses operating system security and role definitions, and Oracle Clusterware access permissions to separate resource and workload management according to the user’s role. This is particularly important for those working in consolidated environments, where there is likely to be competition for computing resources, and a degree of isolation is required for resource consumers and management of those resources. By default, this feature is not implemented during installation.

Configuring role-separated management consists of establishing the operating system users and groups that will administer the cluster resources (such as databases), according to the roles intended, adding the permissions on the cluster resources and server pools through access control lists (ACLs), as necessary. In addition, Oracle Automatic Storage Management (Oracle ASM) provides the capability to extend these role-separation constructs to the storage management functions.

Role-separated management principles apply equally to administrator-managed and policy-managed systems. In the case of administrator-managed, you configure the cluster resources and roles to manage them at the node level, while for policy-managed systems you configure the cluster resources and roles to manage them in the server pools.

Role-separated management in Oracle Clusterware no longer depends on a [cluster administrator](glossary.md) (although Oracle maintains backward compatibility). By default, the user that installed Oracle Clusterware in the Oracle Grid Infrastructure home (Grid home) and `root` are permanent cluster administrators. Primary group privileges (`oinstall`, by default) enable database administrators to create databases in newly created server pools using the Database Configuration Assistant (DBCA), but do not enable role separation.

**Note:**

Oracle recommends that you enable role separation before you create the first server pool in the cluster. Create and manage server pools using configuration policies and a respective policy set. Access permissions are stored for each server pool in the `ACL` attribute, described in [Table 3-1](policy-based-cluster-and-capacity-management.md).

**Related Topics**

- [Overview of Cluster Configuration Policies and the Policy Set](policy-based-cluster-and-capacity-management.md)

#### Managing Cluster Administrators

You use an access control list (ACL) to define administrators for the cluster.

The ability to create server pools in a cluster is limited to the cluster administrators. In prior releases, by default, every registered operating system user was considered a cluster administrator and, if necessary, the default could be changed using `crsctl add | delete crs administrator` commands. The use of these commands, however, is deprecated in this release and, instead, you should use the ACL of the policy set to control the ability to create server pools.

As a rule, to have permission to create a server pool or cluster resource, the operating system user or an operating system group of which the user is a member must have the read, write, and execute permissions set in the `ACL` attribute.

#### Configuring Role Separation

Role separation is the determination of the roles that are needed, the resources and server pools that they will administer, and what their access privileges should be. After you determine these, you then create or modify the operating system user accounts for group privileges (such as `oinstall` or `grid`), using the ACLs and the CRSCTL utility.

The most basic case is to create two operating system users as part of the `oinstall` group, then create the cluster, and two server pools. For each server pool, assign one of the operating system users to administer that server pool and exclude anyone else from all but read access to that server pool.

This requires careful planning, and disciplined, detail-oriented execution, but you can modify the configuration after implementation, to correct mistakes or make adjustments over time.

**Note:**

You cannot apply role separation techniques to ora.\* resources (Oracle RAC database resources). You can only apply these techniques to server pools and user-defined cluster resources and types.

You create the server pools or resources under the `root` or `grid` accounts. For the designated operating system users to administer these server pools or resources, they must then be given the correct permissions, enabling them to fulfill their roles.

Use the `crsctl setperm` command to configure horizontal role separation using ACLs that are assigned to server pools, resources, or both. The CRSCTL utility is located in the path `Grid_home``/bin`, where `Grid_home` is the Oracle Grid Infrastructure for a cluster home.

The command uses the following syntax, where the access control (ACL) string is indicated by italics:

    crsctl setperm {resource | type | serverpool} name {-u acl_string |
    -x acl_string | -o user_name | -g group_name}

The flag options are:

- `-u`: Update the entity ACL

- `-x`: Delete the entity ACL

- `-o`: Change the entity owner

- `-g`: Change the entity primary group

The ACL strings are:

    {user:user_name[:readPermwritePermexecPerm] |
         group:group_name[:readPermwritePermexecPerm] |
         other[::readPermwritePermexecPerm] }

In the preceding syntax example:

- `user`: Designates the user ACL (access permissions granted to the designated user)

- `group`: Designates the group ACL (permissions granted to the designated group members)

- `other`: Designates the other ACL (access granted to users or groups not granted particular access permissions)

- `readperm`: Location of the read permission (`r` grants permission and "`-`" forbids permission)

- `writeperm`: Location of the write permission (`w` grants permission and "`-`" forbids permission)

- `execperm`: Location of the execute permission (`x` grants permission, and "`-`" forbids permission)

For example, to set permissions on a server pool called `psft` for the group `personnel`, where the administrative user has read/write/execute privileges, the members of the `personnel` group have read/write privileges, and users outside of the group are granted no access, enter the following command as the `root` user:

    # crsctl setperm serverpool psft -u user:personadmin:rwx,group:personnel:rw-,
      other::---

For cluster resources, to set permissions on an application (resource) called `MyProgram` (administered by `Maynard`) for the group `crsadmin`, where the administrative user has read, write, and execute privileges, the members of the `crsadmin` group have read and execute privileges, and users outside of the group are granted only read access (for status and configuration checks), enter the following command as whichever user originally created the resource (`root` or `grid` owner):

    # crsctl setperm resource MyProgram -u user:Maynard:r-x,group:crsadmin:rw-,other:---:r--

**Related Topics**

- [Oracle Clusterware Resource Reference](oracle-clusterware-resource-reference.md)

### Configuring Oracle Grid Infrastructure Using Grid Setup Wizard

Using the Configuration Wizard, you can configure a new Oracle Grid Infrastructure on one or more nodes, or configure an upgraded Oracle Grid Infrastructure. You can also run the Grid Setup Wizard in silent mode.

After performing a software-only installation of the Oracle Grid Infrastructure, you can configure the software using Grid Setup Wizard. This Wizard performs various validations of the Grid home and inputs before and after you run through the wizard.

**Note:**

- Before running the Grid Setup Wizard, ensure that the Oracle Grid Infrastructure home is current, with all necessary patches applied.

- To launch the Grid Setup Wizard in the subsequent procedures:

  On Linux and UNIX, run the following command:

      Oracle_home/gridSetup.sh

  On Windows, run the following command:

      Oracle_home\gridSetup.bat

#### Configuring a Single Node

You can configure a single node by using the Configuration Wizard.

To configure a single node:

1.  Start the Configuration Wizard, as follows:
        $ Oracle_home/gridSetup.sh
2.  On the Select Installation Option page, select Configure Oracle Grid Infrastructure for a Cluster.
3.  On the Cluster Node Information page, select only the local node and corresponding VIP name.
4.  Continue adding your information on the remaining wizard pages.
5.  Review your inputs on the Summary page and click Finish.
6.  Run the `root.sh` script as instructed by the Configuration Wizard.

#### Configuring Multiple Nodes

You can use the Configuration Wizard to configure multiple nodes in a cluster.

It is not necessary that Oracle Grid Infrastructure software be installed on nodes you want to configure using the Configuration Wizard.

**Note:**

Before you launch the Configuration Wizard, ensure the following:

While software is not required to be installed on all nodes, if it is installed, then the software must be installed in the same `Grid_home` path and be at the identical level on all the nodes.

To use the Configuration Wizard to configure multiple nodes:

1.  Start the Configuration Wizard, as follows:
        $ Oracle_home/gridSetup.sh
2.  On the Select Installation Option page, select Configure Oracle Grid Infrastructure for a Cluster.
3.  On the Cluster Node Information page, select the nodes you want to configure and their corresponding VIP names. The Configuration Wizard validates the nodes you select to ensure that they are ready.
4.  Continue adding your information on the remaining wizard pages.
5.  Review your inputs on the Summary page and click Finish.
6.  Run the `root.sh` script as instructed by the Configuration Wizard.

#### Upgrading Oracle Grid Infrastructure

You use the Grid Setup Wizard to upgrade a cluster’s Oracle Grid Infrastructure.

To use upgrade Oracle Grid Infrastructure for a cluster:

1.  Start the Grid Setup Wizard:
        $ Oracle_home/gridSetup.sh
2.  On the Select Installation Option page, select Upgrade Oracle Grid Infrastructure.
3.  On the Oracle Grid Infrastructure Node Selection page, review the nodes you want to upgrade. Additionally, you can choose not to upgrade nodes that are down.
4.  Continue adding your information on the remaining wizard pages.
5.  Review your inputs on the Summary page and click Finish.
6.  Run the `rootupgrade.sh` script as instructed by the Configuration Wizard.

**See Also:**

Oracle Database Installation Guide for your platform for Oracle Restart procedures

#### Running the Configuration Wizard in Silent Mode

You can run the Configuration Wizard in silent mode by specifying the —silent parameter.

To use the Configuration Wizard in silent mode to configure or upgrade nodes:

1.  Start the Configuration Wizard from the command line, as follows:

        $ $ORACLE_HOME/gridSetup.sh -silent -responseFile file_name

    The Configuration Wizard validates the response file and proceeds with the configuration. If any of the inputs in the response file are found to be invalid, then the Configuration Wizard displays an error and exits.

2.  Run the `root` and `Grid_home``/gridSetup -executeConfigTools` scripts as prompted.

#### Moving and Patching an Oracle Grid Infrastructure Home

You use the Grid Setup Wizard to move and patch an Oracle Grid Infrastructure home.

The Oracle Installer script `gridSetup.sh` supports a new switch `-switchGridHome` for this purpose. This feature enables you to move and patch an Oracle Grid Infrastructure home to a newer or same patch level.

**See Also:**

- [Oracle Grid Infrastructure Installation and Upgrade Guide for Linux](../cwlin/zero-downtime-oracle-grid-infrastructure-patching.md) for information about switching the Oracle Grid Infrastructure home after patching

### Server Weight-Based Node Eviction

You can configure the Oracle Clusterware failure recovery mechanism to choose which cluster nodes to terminate or evict in the event of a private network (cluster interconnect) failure.

In a split-brain situation, where a cluster experiences a network split, partitioning the cluster into disjoint cohorts, Oracle Clusterware applies certain rules to select the surviving cohort, potentially evicting a node that is running a critical, singleton resource.

You can affect the outcome of these decisions by adding value to a database instance or node so that, when Oracle Clusterware must decide whether to evict or terminate, it will consider these factors and attempt to ensure that all critical components remain available. You can configure weighting functions to add weight to critical components in your cluster, giving Oracle Clusterware added input when deciding which nodes to evict when resolving a split-brain situation.

You may want to ensure that specific nodes survive the tie-breaking process, perhaps because of certain hardware characteristics, or that certain resources survive, perhaps because of particular databases or services. You can assign weight to particular nodes, resources, or services, based on the following criteria:

- You can assign weight only to administrator-managed nodes.

- You can assign weight to servers or applications that are registered Oracle Clusterware resources.

Weight contributes to importance of the component and influences the choice that Oracle Clusterware makes when managing a split-brain situation. With other critical factors being equal between the various cohorts, Oracle Clusterware chooses the heaviest cohort to survive.

You can assign weight to various components, as follows:

- To assign weight to database instances or services, you use the `-css_critical yes` parameter with the `srvctl add database` or `srvctl add service` commands when adding a database instance or service. You can also use the parameter with the `srvctl modify database` and `srvctl modify service` commands.

- To assign weight to non ora.\* resources, use the `-attr "CSS_CRITICAL=yes"` parameter with the `crsctl add resource` and `crsctl modify resource` commands when you are adding or modifying resources.

- To assign weight to a server, use the `-css_critical yes` parameter with the `crsctl set server` command.

**Note:**

- You must restart the Oracle Clusterware stack on the node for the values to take effect. This does not apply to resources where the changes take effect without having to restart the resource.

- If you change the environment from administrator managed to policy managed, or a mixture of the two, any weight that you have assigned is stored, but is not considered, meaning that it will no longer apply or be considered unless and until you reconfigure the cluster back to being administrator managed.

### Overview of Oracle Database Quality of Service Management

Oracle Database Quality of Service Management (Oracle Database QoS Management) is an automated, policy-based product that monitors the workload requests for an entire system.

Oracle Database QoS Management manages the resources that are shared across applications, and adjusts the system configuration to keep the applications running at the performance levels needed by your business. Oracle Database QoS Management responds gracefully to changes in system configuration and demand, thus avoiding additional oscillations in the performance levels of your applications.

Oracle Database QoS Management monitors and manages Oracle RAC database workload performance objectives by identifying bottlenecked resources impacting these objectives, and both recommending and taking actions to restore performance. Administrator-managed deployments bind database instances to nodes but policy-managed deployments do not, so the Oracle Database QoS Management server pool size resource control is only available for the latter. All other resource management controls are available for both deployments.

Oracle Database QoS Management supports administrator-managed Oracle RAC and Oracle RAC One Node databases with its Measure-Only, Monitor, and Management modes. This enables schema consolidation support within an administrator-managed Oracle RAC database by adjusting the CPU shares of performance classes running in the database. Additionally, database consolidation is supported by adjusting CPU counts for databases hosted on the same physical servers.

Because administrator-managed databases do not run in server pools, the ability to expand or shrink the number of instances by changing the server pool size that is supported in policy-managed database deployments is not available for administrator-managed databases. This new deployment support is integrated into the Oracle QoS Management pages in Oracle Enterprise Manager Cloud Control.

### Overview of Grid Naming Service

Oracle Clusterware uses Grid Naming Service (GNS) for address resolution in a single-cluster or multi-cluster environment. You can configure your clusters with a single, primary GNS instance, and you can also configure one or more secondary GNS instances with different roles to provide high availability address lookup and other services to clients.

- Network Administration Tasks for GNS and GNS Virtual IP Address

- Understanding Grid Naming Service Configuration Options

#### Network Administration Tasks for GNS and GNS Virtual IP Address

To implement GNS, your network administrator must configure the DNS to set up a domain for the cluster, and delegate resolution of that domain to the GNS VIP. You can use a separate domain, or you can create a subdomain of an existing domain for the cluster.

GNS distinguishes between nodes by using cluster names and individual node identifiers as part of the host name for that cluster node, so that cluster node 123 in cluster A is distinguishable from cluster node 123 in cluster B.

However, if you configure host names manually, then the subdomain you delegate to GNS should have no subdomains. For example, if you delegate the subdomain `mydomain.example.com` to GNS for resolution, then there should be no `other.mydomain.example.com` domains. Oracle recommends that you delegate a subdomain to GNS that is used by GNS exclusively.

**Note:**

You can use GNS without DNS delegation in configurations where static addressing is being done, such as in Oracle Flex ASM or Oracle Flex Clusters. However, GNS requires a domain be delegated to it if addresses are assigned using DHCP.

Example 2-1 shows DNS entries required to delegate a domain called `myclustergns.example.com` to a GNS VIP address `10.9.8.7`.

The GNS daemon and the GNS VIP run on one node in the server cluster. The GNS daemon listens on the GNS VIP using port 53 for DNS requests. Oracle Clusterware manages the GNS daemon and the GNS VIP to ensure that they are always available. If the server on which the GNS daemon is running fails, then Oracle Clusterware fails over the GNS daemon and the GNS VIP to a surviving cluster member node. If the cluster is an Oracle Flex Cluster configuration, then Oracle Clusterware fails over the GNS daemon and the GNS VIP to a Hub Node.

**Note:**

Oracle Clusterware does not fail over GNS addresses to different clusters. Failovers occur only to members of the same cluster.

Example 2-1 DNS Entries

    # Delegate to gns on mycluster
    mycluster.example.com NS myclustergns.example.com
    #Let the world know to go to the GNS vip
    myclustergns.example.com. 10.9.8.7

**Related Topics**

- [Oracle Grid Infrastructure Installation and Upgrade Guide](../install-and-upgrade.md)
- [Oracle Flex Clusters](oracle-flex-clusters.md)

#### Understanding Grid Naming Service Configuration Options

GNS can run in either automatic or standard cluster address configuration mode. Automatic configuration uses either the Dynamic Host Configuration Protocol (DHCP) for IPv4 addresses or the Stateless Address Autoconfiguration Protocol (autoconfig) (RFC 2462 and RFC 4862) for IPv6 addresses.

This section includes the following topics:

- Highly-Available Grid Naming Service

- Automatic Configuration Option for Addresses

- Static Configuration Option for Addresses

- Shared GNS Option for Addresses

##### Highly-Available Grid Naming Service

Highly-available GNS consists of one primary GNS instance and zero or more secondary GNS instances.

The primary GNS instance services all updates from the clients, while both the primary and the secondary GNS instances process the lookup queries. Additionally, the secondary GNS instances act as backup for the primary GNS instance. Secondary GNS instances can be promoted to the primary role whenever an existing primary GNS instance fails or is removed by the cluster administrator.

Further, highly-available GNS provides fault tolerance by taking data backup on secondary GNS instance using zone transfer. Secondary GNS instances get a copy of data from the primary GNS instance during installation. Thereafter, any update on the primary GNS instance gets replicated to the secondary GNS instances.

The primary GNS instance manages [zone data](glossary.md) and holds all records on the delegated domain. It stores the zone data and its change history in the Oracle Cluster Registry (OCR). Updating the zone data on a secondary GNS instance involves a zone transfer, which can be one of two methods:

- Full zone transfer: The primary GNS instance replicates all zone data to the secondary GNS instances.

- Incremental zone transfer: The primary GNS instance only replicates the changed data to secondary GNS instances. GNS uses this transfer mechanism for the following scenarios:

  - When there is an update to the zone data in the primary GNS instance, the instance notifies the secondary instances to initiate a data transfer. The secondary GNS instances will ask for a data transfer only if the serial number of the data in OCR of the primary GNS instance is greater than that of the data of the secondary GNS instances.

  - When the refresh time of a secondary GNS instance expires, the instance sends a query containing its data serial number to the primary GNS instance. If the serial number of the secondary GNS instance is less than that of the primary GNS instance, then GNS initiates a zone transfer.

    **Note:**

    Refresh time must be long enough to reduce the load on the primary GNS instance so that answering a secondary GNS instance does not prevent the primary instance from being able to function. Default refresh time is one hour but the cluster administrator can change this value based on cluster size.

You must configure a primary GNS instance before you configure any secondary. Once you successfully configure a primary GNS instance, you export client data for clients and secondary GNS instances. You provide exported client data when you configure secondary GNS instances. All secondary GNS instances register themselves with the primary GNS instance and get a copy of zone data. Secondary GNS instances contact the primary GNS instance for data updates using the zone transfer mechanism, when either the refresh time of the secondary GNS instance expires or in response to a notification.

**Related Topics**

- Configuring Highly-Available GNS
- Removing Primary and Secondary GNS Instances

##### Automatic Configuration Option for Addresses

With automatic configurations, a DNS administrator delegates a domain on the DNS to be resolved through the GNS subdomain. During installation, Oracle Universal Installer assigns names for each cluster member node interface designated for Oracle Grid Infrastructure use during installation or configuration. SCANs and all other cluster names and addresses are resolved within the cluster, rather than on the DNS.

Automatic configuration occurs in one of the following ways:

- For IPv4 addresses, Oracle Clusterware assigns unique identifiers for each cluster member node interface allocated for Oracle Grid Infrastructure, and generates names using these identifiers within the subdomain delegated to GNS. A DHCP server assigns addresses to these interfaces, and GNS maintains address and name associations with the IPv4 addresses leased from the IPv4 DHCP pool.

- For IPv6 addresses, Oracle Clusterware automatically generates addresses with autoconfig.

##### Static Configuration Option for Addresses

With static configurations, no subdomain is delegated. A DNS administrator configures the GNS VIP to resolve to a name and address configured on the DNS, and a DNS administrator configures a SCAN name to resolve to three static addresses for the cluster.

A DNS administrator also configures a static public IP name and address, and virtual IP name and address for each cluster member node. A DNS administrator must also configure new public and virtual IP names and addresses for each node added to the cluster. All names and addresses are resolved by DNS.

GNS without subdomain delegation using static VIP addresses and SCANs enables Oracle Flex Cluster and CloudFS features that require name resolution information within the cluster. However, any node additions or changes must be carried out as manual administration tasks.

##### Shared GNS Option for Addresses

With dynamic configurations, you can configure GNS to provide name resolution for one cluster, or to advertise resolution for multiple clusters, so that a single GNS instance can perform name resolution for multiple registered clusters. This option is called shared GNS.

Shared GNS provides the same services as standard GNS, and appears the same to clients receiving name resolution. The difference is that the GNS daemon running on one cluster is configured to provide name resolution for all clusters in domains that are delegated to GNS for resolution, and GNS can be centrally managed using SRVCTL commands. You can use shared GNS configuration to minimize network administration tasks across the enterprise for Oracle Grid Infrastructure clusters.

You cannot use the static address configuration option for a cluster providing shared GNS to resolve addresses in a multi-cluster environment. Shared GNS requires automatic address configuration, either through addresses assigned by DHCP, or by IPv6 stateless address autoconfiguration.

**Note:**

All of the node names in a set of clusters served by GNS must be unique.

Oracle Universal Installer enables you to configure static addresses with GNS for shared GNS clients or servers, with GNS used for discovery.

### Administering Grid Naming Service

Use SRVCTL to administer Grid Naming Service (GNS) in both single-cluster and multi-cluster environments.

**Note:**

The GNS server and client must run on computers using the same operating system and processor architecture. Oracle does not support running GNS on computers with different operating systems, processor architectures, or both.

This section includes the following topics:

- Configuring Highly-Available GNS

- Removing Primary and Secondary GNS Instances

- Starting and Stopping GNS with SRVCTL

- Converting Clusters to GNS Server or GNS Client Clusters

- Moving GNS to Another Cluster

- Changing the GNS Subdomain when Moving from IPv4 to IPv6 Network

- Rolling Conversion from DNS to GNS Cluster Name Resolution

#### Configuring Highly-Available GNS

Configuring highly-available GNS involves configuring primary and secondary GNS instances. You can configure GNS during installation of Oracle Clusterware using Oracle Universal Installer but you can only configure highly-available GNS after you install Oracle Clusterware because you can only configure a secondary GNS instance after you install Oracle Clusterware.

Highly-available GNS provides the ability to run multiple GNS instances in multi-cluster environment with different roles. There will be one primary GNS instance and zero or more secondary instances. The primary instance manages update and resolution operations. However, the secondary instance only manages resolution operations. If you choose to use secondary GNS instances, then you must first configure a primary GNS instance or change the existing GNS in a shared GNS environment to a primary GNS instance.

1.  As the cluster administrator, configure the primary GNS instance on any node in an existing cluster, as follows:
        # srvctl add gns -vip gns_vip -domain gns_subdomain
2.  Start the primary GNS instance, as follows:
        # srvctl start gns

    There can be only one primary GNS instance in a multi-cluster environment. If GNS detects more than one primary GNS instance, then it will terminate the start command. You can then configure this instance as a secondary GNS instance, as described in step 5.
3.  Create client data for the secondary GNS instances, as follows
        # srvctl export gns -clientdata file_name -role secondary

    GNS stores this zone data information in OCR and updates secondary GNS instances once they are configured.
4.  Copy the client data file you created in the preceding step to the secondary GNS instance.
5.  Configure the secondary GNS instance, as follows:
        # srvctl add gns -vip gns_vip -clientdata file_name
6.  Start the secondary GNS instance, as follows:
        # srvctl start gns

    Once you successfully configure and start a secondary GNS instance, it queries the primary GNS instance for the zone data.

#### Removing Primary and Secondary GNS Instances

You can remove primary and secondary GNS instances from a cluster.

You cannot remove a primary GNS instance until you configure another primary GNS instance. If you remove a primary GNS instance before you have another one to replace it, then GNS will not function.

As the cluster administrator, select a secondary GNS instance and promote it to primary, as follows:

    # srvctl modify gns -role primary

1.  Depending on whether you are removing a primary or secondary GNS instance, stop the instance, as follows:
        # srvctl stop gns
2.  Remove the instance, as follows:
        # srvctl remove gns

    **Note:**

    A DNS administrator can delete the instance's name server and A/AAAA record entries from the DNS zone data, so that the client will not attempt to query an instance which is no longer available.

#### Starting and Stopping GNS with SRVCTL

You use the srvctl command to start and stop GNS.

Start and stop GNS on the server cluster by running the following commands as `root`, respectively:

    # srvctl start gns
    # srvctl stop gns

**Note:**

You cannot start or stop GNS on a client cluster.

#### Converting Clusters to GNS Server or GNS Client Clusters

You can convert clusters that are not running GNS into GNS server or client clusters, and you can change GNS cluster type configurations for server and client clusters.

This section includes the following cluster conversion scenarios:

- Converting a Non-GNS Cluster to a GNS Server Cluster

- Converting a Non-GNS Cluster to a Client Cluster

- Converting a Single Cluster Running GNS to a Server Cluster

- Converting a Single Cluster Running GNS to be a GNS Client Cluster

##### Converting a Non-GNS Cluster to a GNS Server Cluster

You can use the srvctl commandto convert a cluster that is not running GNS to a GNS server cluster.

1.  Add GNS to the cluster by running the following command as `root`, providing a valid IP address and a domain:

        # srvctl add gns -vip IP_address -domain domain

2.  Start the GNS instance:

        # srvctl start gns -node node_name

**Note:**

- Specifying a domain is not required when adding a GNS VIP.

- The IP address you specify cannot currently be used by another GNS instance.

- The configured cluster must have DNS delegation for it to be a GNS server cluster.

##### Converting a Non-GNS Cluster to a Client Cluster

To convert a cluster that is not running GNS to a client cluster, you must import the credentials file from the server cluster.

Convert a cluster that is not running GNS to a GNS client cluster, as follows:

1.  Run the following command in the server cluster to export the GNS instance client data configuration to a file:
        $ srvctl export gns -clientdata path_to_file -role client

    You must specify the fully-qualified path to the file.

    **Note:**

    You can use the GNS configuration Client Data file you generate with Oracle Universal Installer as an input file for creating shared GNS clients.
2.  Import the file you created in the preceding step on a node in the cluster to make that cluster a client cluster by running the following command, as `root`:
        # srvctl add gns -clientdata path_to_file

    **Note:**

    You must copy the file containing the GNS data from the server cluster to a node in the cluster where you run this command.
3.  Change the SCAN name, as follows:
        $ srvctl modify scan -scanname scan_name.client_cluster_name.server_GNS_subdomain

##### Converting a Single Cluster Running GNS to a Server Cluster

You do not need to do anything to convert a single cluster running GNS to be a GNS server cluster. It is automatically considered to be a server cluster when a client cluster is added.

##### Converting a Single Cluster Running GNS to be a GNS Client Cluster

You can use the srvctl command to convert a single cluster running GNS to GNC client cluster. Because it is necessary to stay connected to the current GNS during this conversion process, the procedure is more involved than that of converting a single cluster to a server cluster.

To convert a single cluster running GNS to a GNS client cluster:

1.  Run the following command in the server cluster to export the GNS client information to a file:
        $ srvctl export gns -clientdata path_to_client_data_file

    You must specify the fully-qualified path to the file.
2.  Stop GNS on the cluster you want to convert to a client cluster.
        # srvctl stop gns

    **Note:**

    While the conversion is in progress, name resolution using GNS will be unavailable.
3.  Run the following command in the server cluster to export the GNS instance:
        $ srvctl export gns -instance path_to_file

    You must specify the fully-qualified path to the file.
4.  Run the following command as `root` in the server cluster to import the GNS instance file:
        # srvctl import gns -instance path_to_file

    You must specify the fully-qualified path to the file.
5.  Run the following command as `root` on the node where you imported the GNS instance file to start the GNS instance:
        # srvctl start gns

    By not specifying the name of the node on which you want to start the GNS instance, the instance will start on a random node.
6.  Remove GNS from the GNS client cluster using the following command:
        # srvctl remove gns
7.  Make the former cluster a client cluster, as follows:
        # srvctl add gns -clientdata path_to_client_data_file

    **Note:**

    You must copy the file containing the GNS data from the server cluster to a node in the cluster where you run this command.
8.  Modify the SCAN in the GNS client cluster to use the GNS subdomain qualified with the client cluster name, as follows:
        $ srvctl modify scan -scanname scan_name.gns_domain

    In the preceding command, `gns_domain` is in the form `client_cluster_name``.server GNS subdomain`

#### Moving GNS to Another Cluster

If it becomes necessary to make another cluster the GNS server cluster, either because a cluster failure, or because of an administration plan, then you can move GNS to another cluster with the srvctl command.

**Note:**

This procedure requires server cluster and client cluster downtime. Additionally, you must import GNS client data from the new server cluster to any Oracle Flex ASM and Fleet Patching and Provisioning Servers and Clients.

To move GNS to another cluster:

1.  Stop the GNS instance on the current server cluster.
        # srvctl stop gns
2.  Export the GNS instance configuration to a file.
        # srvctl export gns -instance path_to_file

    Specify the fully-qualified path to the file.
3.  Remove the GNS configuration from the former server cluster.
        # srvctl remove gns
4.  Add GNS to the new cluster.
        # srvctl add gns -domain domain_name -vip vip_name

    Alternatively, you can specify an IP address for the VIP.
5.  Configure the GNS instance in the new server cluster using the instance information stored in the file you created in step 2, by importing the file, as follows:
        # srvctl import gns -instance path_to_file

    **Note:**

    The file containing the GNS data from the former server cluster must reside on the node in the cluster where you run the `srvctl import gns` command.
6.  Start the GNS instance in the new server cluster.
        # srvctl start gns

#### Changing the GNS Subdomain when Moving from IPv4 to IPv6 Network

When you move from an IPv4 network to an IPv6 network, you must change the GNS subdomain.

To change the GNS subdomain, you must add an IPv6 network, update the GNS domain, and update the SCAN, as follows:

1.  Add an IPv6 subnet using the `srvctl modify network` command, as follows:
        $ srvctl modify network -subnet ipv6_subnet/ipv6_prefix_length[/interface] -nettype autoconfig
2.  Update the GNS domain, as follows:
        $ srvctl stop gns -force
        $ srvctl stop scan -force
        $ srvctl remove gns -force
        $ srvctl add gns -vip gns_vip -domain gns_subdomain
        $ srvctl start gns
3.  Update the SCAN name with a new domain, as follows:
        $ srvctl remove scan -force
        $ srvctl add scan -scanname new_domain
        $ srvctl start scan
4.  Convert the network IP type from IPv4 to both IPv4 DHCP and IPv6 autoconfig, as follows:
        $ srvctl modify network -iptype both
5.  Transition the network from using both protocols to using only IPv6 autoconfig, as follows:
        $ srvctl modify network -iptype ipv6

#### Rolling Conversion from DNS to GNS Cluster Name Resolution

You can convert Oracle Grid Infrastructure cluster networks using DNS for name resolution to cluster networks using Grid Naming Service (GNS) obtaining name resolution through GNS.

Use the following procedure to convert from a standard DNS name resolution network to a GNS name resolution network, with no downtime:

1.  Log in as the Grid user (`grid`), and use the following Cluster Verification Utility to check the status for moving the cluster to GNS, where `nodelist` is a comma-delimited list of cluster member nodes:
        $ cluvfy stage -pre crsinst -n nodelist
2.  As the Grid user, check the integrity of the GNS configuration using the following commands, where `domain` is the domain delegated to GNS for resolution, and `gns_vip` is the GNS VIP:
        $ cluvfy comp gns -precrsinst -domain domain -vip gns_vip
3.  Log in as `root`, and use the following SRVCTL command to configure the GNS resource, where `domain_name` is the domain that your network administrator has configured your DNS to delegate for resolution to GNS, and `ip_address` is the IP address on which GNS listens for DNS requests:
        # srvctl add gns -domain domain_name -vip ip_address
4.  Use the following command to start GNS:
        # srvctl start gns

    GNS starts and registers VIP and SCAN names.
5.  As `root`, use the following command to change the network CRS resource to support a mixed mode of static and DHCP network addresses:
        # srvctl modify network -nettype MIXED

    The necessary VIP addresses are obtained from the DHCP server, and brought up.
6.  As the Grid user, enter the following command to ensure that Oracle Clusterware is using the new GNS, dynamic addresses, and listener end points:
        cluvfy stage -post crsinst -n all
7.  After the verification succeeds, change the remote endpoints that previously used the SCAN or VIPs resolved through the DNS to use the SCAN and VIPs resolved through GNS.
    For each client using a SCAN, change the SCAN that the client uses so that the client uses the SCAN in the domain delegated to GNS.

    For each client using VIP names, change the VIP name on each client so that they use the same server VIP name, but with the domain name in the domain delegated to GNS.
8.  Enter the following command as `root` to update the system with the SCAN name in the GNS subdomain:
        # srvctl modify scan -scanname scan_name.gns_domain

    In the preceding command syntax, `gns_domain` is the domain name you entered in step 3 of this procedure.
9.  Disable the static addresses once all clients are using the dynamic addresses, as follows:
        $ srvctl modify network -nettype DHCP

**Related Topics**

- [Oracle Grid Infrastructure Installation and Upgrade Guide](../install-and-upgrade.md)

### Node Failure Isolation

Failure isolation is a process by which a failed node is isolated from the rest of the cluster to prevent the failed node from corrupting data.

When a node fails, isolating it involves an external mechanism capable of restarting a problem node without cooperation either from Oracle Clusterware or from the operating system running on that node. To provide this capability, Oracle Clusterware 12c supports the Intelligent Platform Management Interface specification (IPMI) (also known as Baseboard Management Controller (BMC)), an industry-standard management protocol.

Typically, you configure failure isolation using IPMI during Oracle Grid Infrastructure installation, when you are provided with the option of configuring IPMI from the Failure Isolation Support screen. If you do not configure IPMI during installation, then you can configure it after installation using the Oracle Clusterware Control utility (CRSCTL), as described in a subsequent sectioin.

To use IPMI for failure isolation, each cluster member node must be equipped with an IPMI device running firmware compatible with IPMI version 1.5, which supports IPMI over a local area network (LAN). In addition to BMC, `ipmiutil` must be installed on each node. The `ipmiutil` utility is not distributed with the Oracle Grid Infrastructure installation and must be downloaded. You can download `ipmiutil` from ` ipmiutil.sourceforge.net` or other repositories. Running `ipmiutil` displays the version number, in addition to a version number display from the help prompt.

To support dynamic IP address assignment for IPMI using DHCP, the Cluster Synchronization Services daemon requires direct communication with the local IPMI device during Cluster Synchronization Services startup to obtain the IP address of the IPMI device. (This is not true for HP-UX and Solaris platforms, however, which require that the IPMI device be assigned a static IP address.) This is accomplished using an IPMI probe command (OSD), which communicates with the IPMI device through an IPMI driver, which you must install on each cluster system.

If you assign a static IP address to the IPMI device, then the IPMI driver is not strictly required by the Cluster Synchronization Services daemon. The driver is required, however, to use `ipmitool` or `ipmiutil` to configure the IPMI device but you can also do this with management consoles on some platforms.

**Related Topics**

- Post-installation Configuration of IPMI-based Failure Isolation Using CRSCTL

#### Server Hardware Configuration for IPMI

You must first install the `ipmiutil` binary, install and enable the IPMI driver, and configure the IPMI device, as described in the Oracle Grid Infrastructure Installation and Upgrade Guide for your platform.

**Related Topics**

- [Oracle Grid Infrastructure Installation and Upgrade Guide](../install-and-upgrade.md)

#### Post-installation Configuration of IPMI-based Failure Isolation Using CRSCTL

You use the crsctl command to configure IPMI-based failure isolation, after installing Oracle Clusterware. You can also use this command to modify or remove the IPMI configuration.

This is described in the following topics:

- IPMI Postinstallation Configuration with Oracle Clusterware

- Modifying IPMI Configuration Using CRSCTL

- Removing IPMI Configuration Using CRSCTL

##### IPMI Post-installation Configuration with Oracle Clusterware

After you install the `ipmiutil` binary, install and enable the IPMI driver, configure the IPMI device, and complete the server configuration, you can use the CRSCTL command to complete IPMI configuration.

Before you started the installation, you installed the `ipmiutil` binary, installed and enabled the IPMI driver in the server operating system, and configured the IPMI hardware on each node (IP address mode, admin credentials, and so on), as described in [Oracle Grid Infrastructure Installation Guide](../install-and-upgrade.md). When you install Oracle Clusterware, the installer collects the IPMI administrator user ID and password, and stores them in an Oracle Wallet in node-local storage, in OLR.

After you complete the server configuration, complete the following procedure on each cluster node to register IPMI administrators and passwords on the nodes.

**Note:**

If IPMI is configured to obtain its IP address using DHCP, it may be necessary to reset IPMI or restart the node to cause it to obtain an address.

1.  Start Oracle Clusterware, which allows it to obtain the current IP address from IPMI. This confirms the ability of the clusterware to communicate with IPMI, which is necessary at startup.
    If Oracle Clusterware was running before IPMI was configured, you can shut Oracle Clusterware down and restart it. Alternatively, you can use the IPMI management utility to obtain the IPMI IP address and then use CRSCTL to store the IP address in OLR by running a command similar to the following:

        crsctl set css ipmiaddr 192.168.10.45
2.  Use CRSCTL to store the previously established user ID and password for the resident IPMI in OLR by running the `crsctl set css ipmiadmin` command, and supplying password at the prompt. For example:
        crsctl set css ipmiadmin administrator_name
        IPMI BMC password: password

    This command validates the supplied credentials and fails if another cluster node cannot access the local IPMI using them.

    After you complete hardware and operating system configuration, and register the IPMI administrator on Oracle Clusterware, IPMI-based failure isolation should be fully functional.

    Before you start the installation, you must download and install `ipmiutil` on each node in the cluster, install and enable the IPMI driver in the server operating system, and configure the IPMI hardware on each node (IP address mode, admin credentials, and so on), as described in [Oracle Grid Infrastructure Installation Guide](../install-and-upgrade.md). When you install Oracle Clusterware, the installer collects the IPMI administrator user ID and password, and stores them in an Oracle Wallet in node-local storage, in OLR.

##### Modifying IPMI Configuration Using CRSCTL

You may need to modify an existing IPMI-based failure isolation configuration to change IPMI passwords, or to configure IPMI for failure isolation in an existing installation. You may also need to modify the path to the `ipmiutil` binary file.

You use CRSCTL with the IPMI configuration tool appropriate to your platform to accomplish these modifications.

For example, to change the administrator password for IPMI, you must first modify the IPMI configuration as described in Oracle Grid Infrastructure Installation and Upgrade Guide, and then use CRSCTL to change the password in OLR.

The configuration data needed by Oracle Clusterware for IPMI is kept in an Oracle Wallet in OLR. Because the configuration information is kept in a secure store, it must be written by the Oracle Clusterware installation owner account (the Grid user), so you must log in as that installation user.

Use the following procedure to modify an existing IPMI configuration:

1.  Enter the `crsctl set css ipmiadmin ``administrator_name` command. For example, with the user `IPMIadm`:
        $ crsctl set css ipmiadmin IPMIadm

    Provide the administrator password. Oracle Clusterware stores the administrator name and password for the local IPMI in OLR.

    After storing the new credentials, Oracle Clusterware can retrieve the new credentials and distribute them as required.
2.  Enter the `crsctl set css ipmiaddr ``bmc_ip_address` command. For example:
        $ crsctl set css ipmiaddr 192.0.2.244

    This command stores the new IPMI IP address of the local IPMI in OLR, After storing the IP address, Oracle Clusterware can retrieve the new configuration and distribute it as required.
3.  Enter the `crsctl get css ipmiaddr` command. For example:
        $ crsctl get css ipmiaddr

    This command retrieves the IP address for the local IPMI from OLR and displays it on the console.
4.  Remove the IPMI configuration information for the local IPMI from OLR and delete the registry entry, as follows:
        $ crsctl unset css ipmiconfig

**Related Topics**

- [Oracle Grid Infrastructure Installation and Upgrade Guide](../install-and-upgrade.md)
- [Oracle RAC Environment CRSCTL Commands](oracle-clusterware-control-crsctl-utility-reference.md)

##### Removing IPMI Configuration Using CRSCTL

You can remove an IPMI configuration from a cluster using CRSCTL if you want to stop using IPMI completely or if IPMI was initially configured by someone other than the user who installed Oracle Clusterware.

If the latter is true, then Oracle Clusterware cannot access the IPMI configuration data and IPMI is not usable by the Oracle Clusterware software, and you must reconfigure IPMI as the user who installed Oracle Clusterware.

To completely remove IPMI, perform the following steps. To reconfigure IPMI as the user who installed Oracle Clusterware, perform steps 3 and 4, then repeat steps 3 and 4 in the previous section.

1.  Disable the IPMI driver and eliminate the boot-time installation, as follows:
        /sbin/modprobe -r
2.  Disable IPMI-over-LAN for the local IPMI using either `ipmitool` or `ipmiutil`, to prevent access over the LAN or change the IPMI administrator user ID and password.
3.  Ensure that Oracle Clusterware is running and then use CRSCTL to remove the IPMI configuration data from OLR by running the following command:
        $ crsctl unset css ipmiconfig
4.  Restart Oracle Clusterware so that it runs without the IPMI configuration by running the following commands as `root`:
        # crsctl stop crs
        # crsctl start crs

**Related Topics**

- Modifying IPMI Configuration Using CRSCTL
- [Oracle Grid Infrastructure Installation and Upgrade Guide for Linux](../cwlin/enabling-intelligent-platform-management-interface-ipmi.md)

### Understanding Network Addresses on Manually Configured Networks

It is helpful to understand the concepts and requirements for network addresses on manually configured networks.

This section contains the following topics:

- Understanding Network Address Configuration Requirements

- Understanding SCAN Addresses and Client Service Connections

- SCAN Listeners and Service Registration Restriction With Valid Node Checking

#### Understanding Network Address Configuration Requirements

An Oracle Clusterware configuration requires at least one public network interface and one private network interface.

- A public network interface connects users and application servers to access data on the database server.

- A private network interface is for internode communication and used exclusively by Oracle Clusterware.

You can configure a public network interface for either [IPv4](glossary.md), [IPv6](glossary.md), or both types of addresses on a given network. If you use redundant network interfaces (bonded or teamed interfaces), then be aware that Oracle does not support configuring one interface to support IPv4 addresses and the other to support IPv6 addresses. You must configure network interfaces of a redundant interface pair with the same IP protocol.

You can configure one or more private network interfaces, using either IPv4 or IPv6 addresses for all the network adapters. You cannot mix IPv4 and IPv6 addresses for any private network interfaces.

**Note:**

You can only use IPv6 for private networks in clusters using Oracle Clusterware 12c release 2 (12.2), or later.

All the nodes in the cluster must use the same IP protocol configuration. Either all the nodes use only IPv4, or all the nodes use only IPv6, or all the nodes use both IPv4 and IPv6. You cannot have some nodes in the cluster configured to support only IPv6 addresses, and other nodes in the cluster configured to support only IPv4 addresses.

The VIP agent supports the generation of IPv6 addresses using the Stateless Address Autoconfiguration Protocol (RFC 2462), and advertises these addresses with GNS. Run the `srvctl config network` command to determine if DHCP or stateless address autoconfiguration is being used.

This section includes the following topics:

- About IPv6 Address Formats

- Name Resolution and the Network Resource Address Type

##### About IPv6 Address Formats

Each node in an Oracle Grid Infrastructure cluster can support both IPv4 and IPv6 addresses on the same network. The preferred IPv6 address format is as follows, where each x represents a hexadecimal character:

    xxxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx

The IPv6 address format is defined by RFC 2460 and Oracle Grid Infrastructure supports IPv6 addresses, as following:

- Global and site-local IPv6 addresses as defined by RFC 4193.

  **Note:**

  Link-local and site-local IPv6 addresses as defined in RFC 1884 are not supported.

- The leading zeros compressed in each field of the IP address.

- Empty fields collapsed and represented by a '::' separator. For example, you could write the IPv6 address 2001:0db8:0000:0000:0000:8a2e:0370:7334 as 2001:db8::8a2e:370:7334.

- The four lower order fields containing 8-bit pieces (standard IPv4 address format). For example 2001:db8:122:344::192.0.2.33.

##### Name Resolution and the Network Resource Address Type

You can review the network configuration and control the network address type using the `srvctl config network` (to review the configuration) and `srvctl modify network -iptype` commands, respectively.

You can configure how addresses are acquired using the `srvctl modify network -nettype` command. Set the value of the `-nettype` parameter to `dhcp` or `static` to control how IPv4 network addresses are acquired. Alternatively, set the value of the `-nettype` parameter to `autoconfig` or `static` to control how IPv6 addresses are generated.

The `-nettype` and `-iptype` parameters are not directly related but you can use `-nettype dhcp` with `-iptype ipv4` and `-nettype autoconfig` with `-iptype ipv6`.

**Note:**

If a network is configured with both IPv4 and IPv6 subnets, then Oracle does not support both subnets having `-nettype` set to `mixed`.

Oracle does not support making transitions from IPv4 to IPv6 while `-nettype` is set to `mixed`. You must first finish the transition from `static` to `dhcp` before you add IPv6 into the subnet.

Similarly, Oracle does not support starting a transition to IPv4 from IPv6 while `-nettype` is set to `mixed`. You must first finish the transition from `autoconfig` to `static` before you add IPv4 into the subnet.

**Related Topics**

- Network Address Configuration in a Cluster

#### Understanding SCAN Addresses and Client Service Connections

Public network addresses are used to provide services to clients.

If your clients are connecting to the Single Client Access Name (SCAN) addresses, then you may need to change public and virtual IP addresses as you add or remove nodes from the cluster, but you do not need to update clients with new cluster addresses.

**Note:**

You can edit the `listener.ora` file to make modifications to the Oracle Net listener parameters for SCAN and the node listener. For example, you can set TRACE_LEVEL\_`listener_name`. However, you cannot set protocol address parameters to define listening endpoints, because the listener agent dynamically manages them.

SCANs function like a cluster alias. However, SCANs are resolved on any node in the cluster, so unlike a VIP address for a node, clients connecting to the SCAN no longer require updated VIP addresses as nodes are added to or removed from the cluster. Because the SCAN addresses resolve to the cluster, rather than to a node address in the cluster, nodes can be added to or removed from the cluster without affecting the SCAN address configuration.

The SCAN is a fully qualified name (host name and domain) that is configured to resolve to all the addresses allocated for the SCAN. The SCAN resolves to all three addresses configured for the SCAN name on the DNS server, or resolves within the cluster in a GNS configuration. SCAN listeners can run on any node in the cluster. SCANs provide location independence for the databases, so that client configuration does not have to depend on which nodes run a particular database.

Oracle Database 11g release 2 (11.2), and later, instances only register with SCAN listeners as remote listeners. Upgraded databases register with SCAN listeners as remote listeners, and also continue to register with all node listeners.

**Note:**

Because of the Oracle Clusterware installation requirement that you provide a SCAN name during installation, if you resolved at least one IP address using the server `/etc/hosts` file to bypass the installation requirement but you do not have the infrastructure required for SCAN, then, after the installation, you can ignore the SCAN and connect to the databases in the cluster using VIPs.

Oracle does not support removing the SCAN address.

**Related Topics**

- [Oracle Database Net Services Reference](../netrf/index.md)

#### SCAN Listeners and Service Registration Restriction With Valid Node Checking

You can use valid node checking to specify the nodes and subnets from which the SCAN listener accepts registrations. You can specify the nodes and subnet information using SRVCTL.

SRVCTL stores the node and subnet information in the SCAN listener resource profile. The SCAN listener agent reads that information from the resource profile and writes it to the `listener.ora` file.

Database instance registration with a listener succeeds only when the request originates from a valid node. The network administrator can specify a list of valid nodes, excluded nodes, or disable valid node checking altogether. The list of valid nodes explicitly lists the nodes and subnets that can register with the database. The list of excluded nodes explicitly lists the nodes that cannot register with the database. The control of dynamic registration results in increased manageability and security of Oracle RAC deployments.

By default, the SCAN listener agent sets `REMOTE_ADDRESS_REGISTRATION_``listener_name` to a private IP endpoint. The SCAN listener accepts registration requests only from the private network. Remote nodes that are not accessible to the private network of the SCAN listener must be included in the list of valid nodes by using the `registration_invited_nodes_``alias` parameter in the `listener.ora` file, or by modifying the SCAN listener using the command-line interface, SRVCTL.

**Note:**

Starting with Oracle Grid Infrastructure 12c, for a SCAN listener, if the `VALID_NODE_CHECKING_REGISTRATION_``listener_name` and `REGISTRATION_INVITED_NODES_``listener_name` parameters are set in the `listener.ora` file, then the listener agent overwrites these parameters.

If you use the SRVCTL utility to set the `invitednodes` and `invitedsubnets` values, then the listener agent automatically sets `VALID_NODE_CHECKING_REGISTRATION_``listener_name` to SUBNET and sets `REGISTRATION_INVITED_NODES_``listener_name` to the specified list in the `listener.ora` file.

For other listeners managed by CRS, the listener agent sets `VALID_NODE_CHECKING_REGISTRATION_``listener_name` to be SUBNET in the `listener.ora` file only if it is not already set in the `listener.ora` file. The SRVCTL utility does not support setting the `invitednodes` and `invitedsubnets` values for a non-SCAN listener. The listener agent does not update `REGISTRATION_INVITED_NODES_``listener_name` in the `listener.ora` file for a non SCAN listener.

**Related Topics**

- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/server-control-utility-reference.md)
- [Oracle Database Net Services Administrator's Guide](../netag/configuring-and-administering-oracle-net-listener.md)

### Configuring Shared Single Client Access Names

A shared single client access name (SCAN) enables you to share one set of SCAN virtual IPs (VIPs) and listeners on a dedicated cluster with other clusters.

#### About Configuring Shared Single Client Access Names

You must configure the shared single client access name (SCAN) on both the database server and the database client.

The use of a shared SCAN enables multiple clusters to use a single common set of SCAN virtual IP (VIP) addresses to manage user connections, instead of deploying a set of SCAN VIPs per cluster. For example, instead of 10 clusters deploying 3 SCAN VIPs per cluster using a total of 30 IP addresses, with shared SCAN deployments, you only deploy 3 SCAN VIPs for those same 10 clusters, requiring only 3 IP addresses.

Be aware the SCAN VIPs (shared or otherwise) are required for Oracle Real Application Cluster (Oracle RAC) database clusters, but not for application member clusters or the domain services cluster.

The general procedure for configuring shared SCANs is to use the `srvctl` utility to configure first on the server (that is, the cluster that hosts the shared SCAN), then on the client (the Oracle RAC cluster that will use this shared SCAN). On the server, in addition to the configuration using `srvctl`, you must to set environment variables, create a credential file, and ensure that the Oracle Notification Service (ONS) process that is specific to a SCAN cluster can access its own configuration directory to create and manage the ONS configuration.

#### Configuring the Use of Shared SCAN

Use SRVCTL to configure shared SCANs on the server that hosts the dedicated cluster, in addition to performing other necessary configuration tasks.

1.  Log in to the server cluster on which you want to configure the shared SCAN.
2.  Create a SCAN listener that is exclusive to this shared SCAN cluster, as follows:
        $ srvctl add scan_listener -clientcluster cluster_name
3.  Create a new Oracle Notification Service (ONS) resource that is specific to the server cluster.
        $ srvctl add ons -clientcluster cluster_name

    The `srvctl add ons` command assigns an ID to the SCAN.
4.  Export the SCAN listener to the client cluster, as follows:
        $ srvctl export scan_listener -clientcluster cluster_name -clientdata file_name
5.  Export the ONS resource to the client cluster, as follows:
        $ srvctl export ons -clientcluster cluster_name -clientdata file_name

    **Note:**

    You can use the same credential file name for both the SCAN listener and ONS. SRVCTL creates a credential file that you will use when adding these objects to the client cluster.
6.  Configure shared SCAN on each cluster that will use this service.
    1.  Log in to the client cluster on which you want to configure the shared SCAN.
    2.  Add the SCAN to the client cluster, as follows:
            $ srvctl add scan -clientdata file_name
    3.  Create a SCAN listener that is exclusive to this client cluster, as follows:
            $ srvctl add scan_listener -clientdata file_name
    4.  Create an ONS resource for this cluster, as follows:
            $ srvctl add ons -clientdata file_name

        **Note:**

        For each of the preceding commands, specify the name of the credential file you created in the previous steps.

### Changing Network Addresses on Manually Configured Systems

You can perform network address maintenance on manually configured systems.

This is described in the following topics:

- Changing the Virtual IP Addresses Using SRVCTL

- Changing Oracle Clusterware Private Network Configuration

- Creating a Network Using SRVCTL

- Network Address Configuration in a Cluster

- Changing Static IPv4 Addresses To Static IPv6 Addresses Using SRVCTL

- Changing Dynamic IPv4 Addresses To Dynamic IPv6 Addresses Using SRVCTL

- Changing an IPv4 Network to an IPv4 and IPv6 Network

- Transitioning from IPv4 to IPv6 Networks for VIP Addresses Using SRVCTL

#### Changing the Virtual IP Addresses Using SRVCTL

You can use SRVCTL to change a virtual IP address.

Clients configured to use public VIP addresses for Oracle Database releases before Oracle Database 11g release 2 (11.2) can continue to use their existing connection addresses. Oracle recommends that you configure clients to use SCANs, but you are not required to use SCANs. When an earlier version of Oracle Database is upgraded, it is registered with the SCAN, and clients can start using the SCAN to connect to that database, or continue to use VIP addresses for connections.

If you continue to use VIP addresses for client connections, you can modify the VIP address while Oracle Database and Oracle ASM continue to run. However, you must stop services while you modify the address. When you restart the VIP address, services are also restarted on the node.

You cannot use this procedure to change a static public subnet to use DHCP. Only the `srvctl add network -subnet` command creates a DHCP network.

**Note:**

The following instructions describe how to change only a VIP address, and assume that the host name associated with the VIP address does not change. Note that you do not need to update VIP addresses manually if you are using GNS, and VIPs are assigned using DHCP.

If you are changing only the VIP address, then update the DNS and the client hosts files. Also, update the server hosts files, if those are used for VIP addresses.

Perform the following steps to change a VIP address:

1.  Stop all services running on the node whose VIP address you want to change using the following command syntax, where `database_name` is the name of the database, `service_name_list` is a list of the services you want to stop, and `my_node` is the name of the node whose VIP address you want to change:
        srvctl stop service -db database_name -service "service_name_list" -node node_name

    The following example specifies the database name (`grid`) using the `-db` option and specifies the services (`sales,oltp`) on the appropriate node (`mynode`).

        $ srvctl stop service -db grid -service "sales,oltp" -node mynode
2.  Confirm the current IP address for the VIP address by running the `srvctl config vip` command. This command displays the current VIP address bound to one of the network interfaces. The following example displays the configured VIP address for a VIP named `node03-vip`:
        $ srvctl config vip -vipname node03-vip
        VIP exists: /node03-vip/192.168.2.20/255.255.255.0/eth0
3.  Stop the VIP resource using the `srvctl stop vip` command:
        $ srvctl stop vip -node node_name
4.  Verify that the VIP resource is no longer running by running the `ifconfig -a` command on Linux and UNIX systems (or issue the `ipconfig /all` command on Windows systems), and confirm that the interface (in the example it was `eth0:1`) is no longer listed in the output.
5.  Make any changes necessary to the `/etc/hosts` files on all nodes on Linux and UNIX systems, or the `%windir%\system32\drivers\etc\hosts` file on Windows systems, and make any necessary DNS changes to associate the new IP address with the old host name.
6.  To use a different subnet or network interface card for the default network before you change any VIP resource, you must use the `srvctl modify network -subnet ``subnet``/``netmask``/``interface` command as `root` to change the network resource, where `subnet` is the new subnet address, `netmask` is the new netmask, and `interface` is the new interface. After you change the subnet, then you must change each node's VIP to an IP address on the new subnet, as described in the next step.
7.  Modify the node applications and provide the new VIP address using the following `srvctl modify nodeapps` syntax:
        $ srvctl modify nodeapps -node node_name -address new_vip_address

    The command includes the following flags and values:

    - `-n ``node_name` is the node name

    - `-A ``new_vip_address` is the node-level VIP address: `name``|``ip``/``netmask``/[``if1``[|``if2``|...]]`

      For example, run the following command as the `root` user:

          # srvctl modify nodeapps -node mynode -address 192.168.2.125/255.255.255.0/eth0

      Attempting to run this command as the installation owner account may result in an error. For example, if the installation owner is `oracle`, then you may see the error `PRCN-2018: Current user oracle is not a privileged user`. To avoid the error, run the command as the `root` or system administrator account.
8.  Start the node VIP by running the `srvctl start vip` command:
        $ srvctl start vip -node node_name

    The following command example starts the VIP on the node named `mynode`:

        $ srvctl start vip -node mynode
9.  Repeat the steps for each node in the cluster.
    Because the SRVCTL utility is a clusterwide management tool, you can accomplish these tasks for any specific node from any node in the cluster, without logging in to each of the cluster nodes.
10. Run the following command to verify node connectivity between all of the nodes for which your cluster is configured. This command discovers all of the network interfaces available on the cluster nodes and verifies the connectivity between all of the nodes by way of the discovered interfaces. This command also lists all of the interfaces available on the nodes which are suitable for use as VIP addresses.
        $ cluvfy comp nodecon -n all -verbose

**Related Topics**

- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/server-control-utility-reference.md)

#### Changing Oracle Clusterware Private Network Configuration

You can make changes to the Oracle Clusterware private network configuration.

This section describes the following topics:

- About Private Networks and Network Interfaces

- Redundant Interconnect Usage

- Consequences of Changing Interface Names Using OIFCFG

- Changing a Network Interface

##### About Private Networks and Network Interfaces

Oracle Clusterware requires that each node is connected through a private network (in addition to the public network). The private network connection is referred to as the cluster interconnect.

Table 2-1 describes how the network interface card and the private IP address are stored.

Oracle only supports clusters in which all of the nodes use the same network interface connected to the same subnet (defined as a global interface with the `oifcfg` command). You cannot use different network interfaces for each node (node-specific interfaces).

Table 2-1 Storage for the Network Interface, Private IP Address, and Private Host Name

| Entity                     | Stored In...                                                 | Comments                                                                                                                                                                                           |
|:---------------------------|:-------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Network interface name     | Operating system<br>For example: `eth1`                      | You can use wildcards when specifying network interface names.<br>For example: `eth*`                                                                                                              |
| Private network Interfaces | Oracle Clusterware, in the Grid Plug and Play (GPnP) Profile | Configure an interface for use as a private interface during installation by marking the interface as Private, or use the `oifcfg setif` command to designate an interface as a private interface. |

**Related Topics**

- [Oracle Interface Configuration Tool (OIFCFG) Command Reference](oracle-interface-configuration-tool-oifcfg-command-reference.md)

##### Redundant Interconnect Usage

You can define multiple interfaces for Redundant Interconnect Usage by classifying the role of interfaces as private either during installation or after installation using the `oifcfg setif` command.

When you do, Oracle Clusterware creates from one to four (depending on the number of interfaces you define) highly available IP (HAIP) addresses, which Oracle Database and Oracle ASM instances use to ensure highly available and load balanced communications.

The Oracle software (including Oracle RAC, Oracle ASM, and Oracle ACFS, all 11g release 2 (11.2.0.2), or later), by default, uses the HAIP address of the interfaces designated with the private role as the HAIP address for all of its traffic, enabling load balancing across the provided set of cluster interconnect interfaces. If one of the defined cluster interconnect interfaces fails or becomes non-communicative, then Oracle Clusterware transparently moves the corresponding HAIP address to one of the remaining functional interfaces.

For example, after installation, if you add a new interface to a server named `eth3` with the subnet number 172.16.2.0, then use the following command to make this interface available to Oracle Clusterware for use as a private interface:

    $ oifcfg setif -global eth3/172.16.2.0:cluster_interconnect

While Oracle Clusterware brings up a HAIP address on `eth3` of 169.254.\*.\* (which is the reserved subnet for HAIP), and the database, Oracle ASM, and Oracle ACFS use that address for communication, Oracle Clusterware also uses the 172.16.2.0 address for its own communication.

**Caution:**

Do not use OIFCFG to classify HAIP subnets (169.264.\*.\*). You can use OIFCFG to record the interface name, subnet, and type (public, cluster interconnect, or Oracle ASM) for Oracle Clusterware. However, you cannot use OIFCFG to modify the actual IP address for each interface.

**Note:**

Oracle Clusterware uses at most four interfaces at any given point, regardless of the number of interfaces defined. If one of the interfaces fails, then the HAIP address moves to another one of the configured interfaces in the defined set.

When there is only a single HAIP address and multiple interfaces from which to select, the interface to which the HAIP address moves is no longer the original interface upon which it was configured. Oracle Clusterware selects the interface with the lowest numeric subnet to which to add the HAIP address.

**Related Topics**

- [Oracle Grid Infrastructure Installation and Upgrade Guide](../install-and-upgrade.md)

##### Consequences of Changing Interface Names Using OIFCFG

The consequences of changing interface names depend on which name you are changing, and whether you are also changing the IP address.

In cases where you are only changing the interface names, the consequences are minor. If you change the name for the public interface that is stored in OCR, then you also must modify the node applications for the cluster. Therefore, you must stop the node applications for this change to take effect.

##### Changing a Network Interface

You can change a network interface and its associated subnet address by using the OIFCFG command..

This procedure changes the network interface and IP address on each node in the cluster used previously by Oracle Clusterware and Oracle Database.

**Caution:**

The interface that the Oracle RAC (RDBMS) interconnect uses must be the same interface that Oracle Clusterware uses with the host name. Do not configure the private interconnect for Oracle RAC on a separate interface that is not monitored by Oracle Clusterware.

1.  Ensure that Oracle Clusterware is running on all of the cluster nodes by running the following command:
        $ olsnodes -s

    The command returns output similar to the following, showing that Oracle Clusterware is running on all of the nodes in the cluster:

        ./olsnodes -s
        myclustera Active
        myclusterc Active
        myclusterb Active
2.  Ensure that the replacement interface is configured and operational in the operating system on all of the nodes. Use the `ifconfig` command (or `ipconfig` on Windows) for your platform. For example, on Linux, use:
        $ /sbin/ifconfig
3.  Add the new interface to the cluster as follows, providing the name of the new interface and the subnet address, using the following command:
        $ oifcfg setif -global if_name/subnet:cluster_interconnect

    You can use wildcards with the interface name. For example, `oifcfg setif -global "eth*/192.168.0.0:cluster_interconnect` is valid syntax. However, be careful to avoid ambiguity with other addresses or masks used with other cluster interfaces. If you use wildcards, then you see a warning similar to the following:

        eth*/192.168.0.0 global cluster_interconnect
        PRIF-29: Warning: wildcard in network parameters can cause mismatch
        among GPnP profile, OCR, and system

    **Note:**

    Legacy network configuration does not support wildcards; thus wildcards are resolved using current node configuration at the time of the update.
4.  If you change the Oracle ASM network, then update the Oracle ASM listener, as follows:
        $ srvctl update listener -listener listener_name -asm -remove -force
        $ srvctl add listener -listener listener_name -asmlistener -subnet subnet
5.  After the previous step completes, you can remove the former subnet, as follows, by providing the name and subnet address of the former interface:
        oifcfg delif -global if_name/subnet

    For example:

        $ oifcfg delif -global eth1/10.10.0.0

    **Caution:**

    This step should be performed only after a replacement interface is committed into the Grid Plug and Play configuration. Deletion of cluster interfaces without providing a valid replacement can result in invalid cluster configuration.
6.  Verify the current configuration using the following command:
        oifcfg getif

    For example:

        $ oifcfg getif
        eth2 10.220.52.0 global cluster_interconnect
        eth0 10.220.16.0 global public
7.  If you change the private network, then stop Oracle Clusterware on all nodes by running the following command as `root` on each node:
        # crsctl stop crs

    **Note:**

    If you configured HAIP on eth0 and eth1, and you want to replace eth1 with eth3, then you do not have to stop Oracle Clusterware. If, however, you want to add another set of interfaces, such as eth2 and eth3 to your HAIP configuration, which you already configured on eth0 and eth1, then you must stop Oracle Clusterware.
8.  When Oracle Clusterware stops, you can deconfigure the deleted network interface in the operating system using the `ifconfig` command. For example:
        $ ifconfig down

    At this point, the IP address from network interfaces for the old subnet is deconfigured from Oracle Clusterware. This command does not affect the configuration of the IP address on the operating system.

    You must update the operating system configuration changes, because changes made using `ifconfig` are not persistent.
9.  Restart Oracle Clusterware by running the following command on each node in the cluster as the `root` user:
        # crsctl start crs

    The changes take effect when Oracle Clusterware restarts.

    If you use the `CLUSTER_INTERCONNECTS` initialization parameter, then you must update it to reflect the changes.

**Related Topics**

- [Oracle Interface Configuration Tool (OIFCFG) Command Reference](oracle-interface-configuration-tool-oifcfg-command-reference.md)

#### Creating a Network Using SRVCTL

You can use SRVCTL to create a network for a cluster member node, and to add application configuration information.

Create a network for a cluster member node, as follows:

1.  Log in as `root`.
2.  Add a node application to the node, using the following syntax, where:
        srvctl add nodeapps -node node_name -address {vip |
           addr}/netmask[/if1[|if2|...]] [-pingtarget "ping_target_list"]

    In the preceding syntax:

    - `node_name` is the name of the node

    - `vip` is the VIP name or `addr` is the IP address

    - `netmask` is the netmask

    - `if1``[|``if2``|...]` is a pipe (`|`)-delimited list of interfaces bonded for use by the application

    - `ping_target_list` is a comma-delimited list of IP addresses or host names to ping

    **Note:**

    - Use the `-pingtarget` parameter when link status monitoring does not work as it does in a virtual machine environment.

    - Enter the `srvctl add nodeapps -help` command to review other syntax options.

    In the following example of using `srvctl add nodeapps` to configure an IPv4 node application, the node name is node1, the netmask is 255.255.252.0, and the interface is eth0:

        # srvctl add nodeapps -node node1 -address node1-vip.mycluster.example.com/255.255.252.0/eth0

**Related Topics**

- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/server-control-utility-reference.md)

#### Network Address Configuration in a Cluster

You can configure a network interface for either IPv4, IPv6, or both types of addresses on a given network.

If you configure redundant network interfaces using a third-party technology, then Oracle does not support configuring one interface to support IPv4 addresses and the other to support IPv6 addresses. You must configure network interfaces of a redundant interface pair with the same IP address type. If you use the Oracle Clusterware Redundant Interconnect feature, then you must use IPv4 addresses for the interfaces.

All the nodes in the cluster must use the same IP protocol configuration. Either all the nodes use only IPv4, or all the nodes use only IPv6, or all the nodes use both IPv4 and IPv6. You cannot have some nodes in the cluster configured to support only IPv6 addresses, and other nodes in the cluster configured to support only IPv4 addresses.

The local listener listens on endpoints based on the address types of the subnets configured for the network resource. Possible types are IPV4, IPV6, or both.

#### Changing Static IPv4 Addresses To Static IPv6 Addresses Using SRVCTL

When you change from IPv4 static addresses to IPv6 static addresses, you add an IPv6 address and modify the network to briefly accept both IPv4 and IPv6 addresses, before switching to using static IPv6 addresses, only.

**Note:**

If the IPv4 network is in mixed mode with both static and dynamic addresses, then you cannot perform this procedure. You must first transition all addresses to static.

To change a static IPv4 address to a static IPv6 address:

1.  Add an IPv6 subnet using the following command as `root` once for the entire network:
        # srvctl modify network -subnet ipv6_subnet/prefix_length

    In the preceding syntax `ipv6_subnet``/``prefix_length` is the subnet of the IPv6 address to which you are changing along with the prefix length, such as 3001::/64.
2.  Add an IPv6 VIP using the following command as `root` once on each node:
        # srvctl modify vip -node node_name -netnum network_number -address vip_name/netmask

    In the preceding syntax:

    - `node_name` is the name of the node

    - `network_number` is the number of the network

    - `vip_name``/``netmask` is the name of a local VIP that resolves to both IPv4 and IPv6 addresses

      The IPv4 netmask or IPv6 prefix length that follows the VIP name must satisfy two requirements:

      - If you specify a netmask in IPv4 format (such as 255.255.255.0), then the VIP name resolves to IPv4 addresses (but can also resolve to IPv6 addresses). Similarly, if you specify an IPv6 prefix length (such as 64), then the VIP name resolves to IPv6 addresses (but can also resolve to IPv4 addresses).

      - If you specify an IPv4 netmask, then it should match the netmask of the registered IPv4 network subnet number, regardless of whether the `-iptype` of the network is IPv6. Similarly, if you specify an IPv6 prefix length, then it must match the prefix length of the registered IPv6 network subnet number, regardless of whether the `-iptype` of the network is IPv4.
3.  Add the IPv6 network resource to OCR using the following command:
        $ oifcfg setif -global if_name/subnet:public
4.  Update the SCAN in DNS to have as many IPv6 addresses as there are IPv4 addresses. Add IPv6 addresses to the SCAN VIPs using the following command as `root` once for the entire network:
        # srvctl modify scan -scanname scan_name

    `scan_name` is the name of a SCAN that resolves to both IPv4 and IPv6 addresses.
5.  Convert the network IP type from IPv4 to both IPv4 and IPv6 using the following command as `root` once for the entire network:
        srvctl modify network -netnum network_number -iptype both

    This command brings up the IPv6 static addresses.
6.  Change all clients served by the cluster from IPv4 networks and addresses to IPv6 networks and addresses.
7.  Transition the network from using both protocols to using only IPv6 using the following command:
        # srvctl modify network -iptype ipv6
8.  Modify the VIP using a VIP name that resolves to IPv6 by running the following command as `root`:
        # srvctl modify vip -node node_name -address vip_name -netnum network_number

    Do this once for each node.
9.  Modify the SCAN using a SCAN name that resolves to IPv6 by running the following command:
        # srvctl modify scan -scanname scan_name

    Do this once for the entire cluster.
10. After the previous step completes, you can remove the static IPv4 address, as follows, by providing the name and subnet address:
        oifcfg delif -global if_name/subnet

    For example:
        $ oifcfg delif -global eth1/10.10.0.0

**Related Topics**

- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/server-control-utility-reference.md)
- [OIFCFG Command Format](oracle-interface-configuration-tool-oifcfg-command-reference.md)

#### Changing Dynamic IPv4 Addresses To Dynamic IPv6 Addresses Using SRVCTL

You change dynamic IPv4 addresses to dynamic IPv6 addresses by the SRVCTL command.

**Note:**

If the IPv4 network is in mixed mode with both static and dynamic addresses, then you cannot perform this procedure. You must first transition all addresses to dynamic.

To change dynamic IPv4 addresses to dynamic IPv6 addresses:

1.  Add an IPv6 subnet using the `srvctl modify network` command.
    To add the IPv6 subnet, log in as `root` and use the following command syntax:

        # srvctl modify network -netnum network_number -subnet ipv6_subnet/
          ipv6_prefix_length[/interface] -nettype autoconfig

    In the preceding syntax:

    - `network_number` is the number of the network

    - `ipv6_subnet` is the subnet of the IPv6 addresses to which you are changing (for example, 2001:db8:122:344:c0:2:2100::)

    - `ipv6_prefix_length` is the prefix specifying the IPv6 network addresses (for example, 64)

    For example, the following command modifies network `3` by adding an IPv6 subnet, 2001:db8:122:344:c0:2:2100::, and the prefix length 64:

        # srvctl modify network -netnum 3 -subnet 2001:db8:122:344:c0:2:2100::/64
          -nettype autoconfig
2.  Add the IPv6 network resource to OCR using the following command:
        $ oifcfg setif -global if_name/subnet:public
3.  Start the IPv6 dynamic addresses, as follows:
        # srvctl modify network -netnum network_number -iptype both

    For example, on network number 3:

        # srvctl modify network -netnum 3 -iptype both
4.  Change all clients served by the cluster from IPv4 networks and addresses to IPv6 networks and addresses.
    At this point, the SCAN in the GNS-delegated domain `scan_name``.``gns_domain` will resolve to three IPv4 and three IPv6 addresses.
5.  Turn off the IPv4 part of the dynamic addresses on the cluster using the following command:
        # srvctl modify network -iptype ipv6

    After you run the preceding command, the SCAN (`scan_name``.``gns_domain`) will resolve to only three IPv6 addresses.
6.  After the previous step completes, you can remove the static IPv4 address, as follows, by providing the name and subnet address:
        oifcfg delif -global if_name/subnet

    For example:
        $ oifcfg delif -global eth1/10.10.0.0

**Related Topics**

- [OIFCFG Command Format](oracle-interface-configuration-tool-oifcfg-command-reference.md)

#### Changing an IPv4 Network to an IPv4 and IPv6 Network

You can change an IPv4 network to an IPv4 and IPv6 network by adding an IPv6 network to an existing IPv4 network.

This process is described in steps 1 through 5 of the procedure documented in "Changing Static IPv4 Addresses To Static IPv6 Addresses Using SRVCTL".

After you complete those steps, log in as the Grid user, and run the following command:

    $ srvctl status scan

Review the output to confirm the changes to the SCAN VIPs.

#### Transitioning from IPv4 to IPv6 Networks for VIP Addresses Using SRVCTL

You use the SRVCTL command to remove an IPv4 address type from a combined IPv4 and IPv6 network.

Enter the following command:

    # srvctl modify network -iptype ipv6

This command starts the removal process of IPv4 addresses configured for the cluster.

### Cross-Cluster Dependency Proxies

Cross-cluster dependency proxies are lightweight, fault-tolerant proxy resources on Member Clusters for resources running on a Domain Services Cluster.

Member Clusters reduce the overhead of having infrastructure resources and it is important to be able to effectively monitor the state of the shared infrastructure resources, such as Oracle Automatic Storage Management (Oracle ASM), on a Domain Services Cluster, so that resources on Member Clusters can properly adjust their states.

Cross-cluster dependency proxies provide this functionality for Domain Services Cluster resources, specifically, and, more generally, to reflect the state of resources running on one cluster, in other clusters. Cross-cluster dependency proxies are configured, by default, on Domain Services Clusters.
