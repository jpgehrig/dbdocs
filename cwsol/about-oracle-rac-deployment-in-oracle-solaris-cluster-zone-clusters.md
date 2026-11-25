A zone cluster consists of several Oracle Solaris Zones, each of which resides on its own separate server; the zones that comprise the cluster are linked together into a single virtual cluster.

Multiple zone clusters can exist on single global cluster, providing a means to consolidate multicluster applications on a global cluster. A node of a global cluster can be configured on either a physical machine or a virtual machine such as Oracle VM Server for SPARC logical domain. A global cluster can also have a combination of physical and virtual nodes.

Installing Oracle Real Application Clusters (Oracle RAC) in a zone cluster allows you to have separate database versions or separate deployments of the same database (for example, one for production and one for development). Using this architecture, you can also deploy different parts of your multitier solution into different virtual zone clusters. For example, you could deploy Oracle RAC and an application server in different zone clusters of the same global cluster. This approach allows you to isolate tiers and administrative domains from each other, while taking advantage of the simplified administration provided by Oracle Solaris Cluster.

**See Also:**

- Supported virtualization technologies for Oracle Database and Oracle RAC at the following link:

  <http://www.oracle.com/technetwork/database/virtualizationmatrix-172995.html#NoteSolarisx64ZONERAC>

- [Oracle Solaris Cluster Software Installation Guide](http://docs.oracle.com/cd/E56676_01/html/E56678/babccjcd.html#CLISTghbof) for information about Oracle Solaris zone clusters

**Parent topic:** [Deploying Oracle RAC on Oracle Solaris Cluster Zone Clusters](deploying-oracle-rac-on-oracle-solaris-cluster-zone-clusters.md)
