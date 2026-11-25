Starting with Oracle Grid Infrastructure 12c Release 1 (12.1), as part of an Oracle Flex Cluster installation, Oracle ASM is configured within Oracle Grid Infrastructure to provide storage services.

Oracle Flex ASM enables an Oracle ASM instance to run on a separate physical server from the database servers. Many Oracle ASM instances can be clustered to support numerous database clients. Each Oracle Flex ASM cluster has its own name that is globally unique within the enterprise.

You can consolidate all the storage requirements into a single set of disk groups. All these disk groups are managed by a small set of Oracle ASM instances running in a single Oracle Flex Cluster.

Every Oracle Flex ASM cluster has one or more cluster nodes on which Oracle ASM instances are running.

Oracle Flex ASM can use either the same private networks as Oracle Clusterware, or use its own dedicated private networks. Each network can be classified `PUBLIC`, `ASM & PRIVATE`, `PRIVATE`, or `ASM`.

The Oracle ASM network can be configured during installation, or configured or modified after installation.

### About Oracle Flex ASM Cluster Configuration on Cluster Nodes

Oracle Flex ASM cluster nodes can be configured with the following characteristics:

- Are similar to prior release Oracle Grid Infrastructure cluster member nodes, as all servers configured with the cluster node role are peers.

- Have direct connections to the Oracle ASM disks.

- Run a Direct ASM client process.

- Run an Oracle ASM Filter Driver, part of whose function is to provide cluster fencing security for the Oracle Flex ASM cluster.

- Respond to service requests delegated to them through the global Oracle ASM listener configured for the Oracle Flex ASM cluster, which designates three of the Oracle Flex ASM cluster member node listeners as remote listeners for the Oracle Flex ASM cluster.

- Can provide database clients that are running on nodes of the Oracle ASM cluster remote access to Oracle ASM for metadata, and allow database clients to perform block I/O operations directly to Oracle ASM disks. The hosts running the Oracle ASM server and the remote database client must both be cluster nodes.

### About Oracle Flex ASM Cluster with Oracle IOServer (IOS) Configuration

An Oracle IOServer instance provides Oracle ASM file access for Oracle Database instances on nodes of Oracle Member Clusters that do not have connectivity to Oracle ASM managed disks. IOS enables you to configure Oracle Member Clusters on such nodes. On the storage cluster, the IOServer instance on each node opens up network ports to which clients send their I/O. The IOServer instance receives data packets from the client and performs the appropriate I/O to Oracle ASM disks similar to any other database client. On the client side, databases can use direct NFS (dNFS) to communicate with an IOServer instance. However, no client side configuration is required to use IOServer, so you are not required to provide a server IP address or any additional configuration information. On nodes and clusters that are configured to access Oracle ASM files through IOServer, the discovery of the Oracle IOS instance occurs automatically.

To install an Oracle Member Cluster, the administrator of the Oracle Domain Services Cluster creates an Oracle Member Cluster using a `crsctl` command that creates a Member Cluster Manifest file. During Oracle Grid Infrastructure installation, if you choose to install an Oracle Member Cluster, then the installer prompts you for the Member Cluster Manifest file. An attribute in the Member Cluster Manifest file specifies if the Oracle Member Cluster is expected to access Oracle ASM files through an IOServer instance.

**Related Topics**

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/manage-flex-asm.md)

**Parent topic:** [Configuration Requirements for Oracle Flex Clusters](configuration-requirements-for-oracle-flex-clusters.md)
