Starting with Oracle Grid Infrastructure 12c Release 1 (12.1), as part of an Oracle Flex Cluster installation, Oracle ASM is configured within Oracle Grid Infrastructure to provide storage services.

Oracle Flex ASM enables an Oracle ASM instance to run on a separate physical server from the database servers. Many Oracle ASM instances can be clustered to support numerous database clients. Each Oracle Flex ASM cluster has its own name that is globally unique within the enterprise.

You can consolidate all the storage requirements into a single set of disk groups. All these disk groups are managed by a small set of Oracle ASM instances running in a single Oracle Flex Cluster.

Every Oracle Flex ASM cluster has one or more cluster nodes on which Oracle ASM instances are running.

Oracle Flex ASM can use either the same private networks as Oracle Clusterware, or use its own dedicated private networks. Each network can be classified `PUBLIC`, `ASM & PRIVATE`, `PRIVATE`, or `ASM`.

The Oracle ASM network can be configured during installation, or configured or modified after installation.

### About Oracle Flex ASM Cluster Configuration on Cluster Nodes

Oracle Flex ASM cluster nodes can be configured with the following characteristics:

- Are similar to prior release Oracle Grid Infrastructure cluster member nodes.

- Have direct connections to the Oracle ASM disks.

- Run a Direct ASM client process.

- Run an Oracle ASM Filter Driver, part of whose function is to provide cluster fencing security for the Oracle Flex ASM cluster.

- Respond to service requests delegated to them through the global Oracle ASM listener configured for the Oracle Flex ASM cluster, which designates three of the Oracle Flex ASM cluster member node listeners as remote listeners for the Oracle Flex ASM cluster.

- Can provide database clients that are running on cluster nodes of the Oracle ASM cluster remote access to Oracle ASM for metadata, and allow database clients to perform block I/O operations directly to Oracle ASM disks. The hosts running the Oracle ASM server and the remote database client must both be cluster nodes.

**Parent topic:** [Configuration Requirements for Oracle Flex Clusters](configuration-requirements-for-oracle-flex-clusters.md)
