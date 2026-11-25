Oracle Member Clusters use centralized services from the Oracle Domain Services Cluster and can host databases or applications. Oracle Member Clusters can be of two types - Oracle Member Clusters for Oracle Databases or Oracle Member Clusters for applications.

Oracle Member Clusters do not need direct connectivity to shared disks. Using the shared Oracle ASM service, they can leverage network connectivity to the IO Service or the ACFS Remote Service to access a centrally managed pool of storage. To use shared Oracle ASM services from the Oracle Domain Services Cluster, the member cluster needs connectivity to the Oracle ASM networks of the Oracle Domain Services Cluster.

Oracle Member Clusters cannot provide services to other clusters. For example, you cannot configure and use a member cluster as a GNS server or Oracle Fleet Patching and Provisioning Server.

### Oracle Member Cluster for Oracle Databases

An Oracle Member Cluster for Oracle Databases supports Oracle Real Application Clusters (Oracle RAC) or Oracle RAC One Node database instances. This cluster registers with the management repository service and uses the centralized TFA service. It can use additional services as needed. An Oracle Member Cluster for Oracle Databases can be configured with local Oracle ASM storage management or make use of the consolidated Oracle ASM storage management service offered by the Oracle Domain Services Cluster.

An Oracle Member Cluster for Oracle Database always uses remote Grid Infrastructure Management Repository (GIMR) from its Oracle Domain Services Cluster. For two-node or four-node clusters, hosting the GIMR on a remote cluster reduces the overhead of running an extra infrastructure repository on a cluster.

### Oracle Member Cluster for Applications

Oracle Member Cluster for Applications hosts applications other than Oracle Database, as part of an Oracle Cluster Domain. The Oracle Member Cluster requires connectivity to Oracle Cluster Domain Services for centralized management and resource efficiency. The Oracle Member Cluster uses remote Oracle ASM storage, with any required shared storage provided through the Oracle ACFS Remote service. This cluster configuration enables high availability of any software application.

Unlike other cluster configurations that require public and private network interconnects, the Oracle Member Cluster for Application can be configured to use a single public network interface.

**Note:**

Before running Oracle Universal Installer, you must specify the Oracle Domain Services Cluster configuration details for the Oracle Member Cluster by creating the Member Cluster Manifest file.

Oracle Member Cluster for Oracle Database does not support Oracle Database 12.1 or earlier, where Oracle Member Cluster is configured with Oracle ASM storage as direct or indirect.

**Related Topics**

- [Creating Member Cluster Manifest File for Oracle Member Clusters](creating-member-cluster-manifest-file.md)

**Parent topic:** [Understanding Cluster Configuration Options](understanding-cluster-configuration-options.md)
