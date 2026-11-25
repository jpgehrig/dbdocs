Review the prerequisites for deploying Oracle Real Application Clusters (Oracle RAC) in Oracle Solaris Cluster zone clusters.

- Oracle Solaris 11 with DNS and NIS name service is installed.

- Oracle Solaris Cluster 4 is installed with the `ha-cluster-full` package.

- Oracle Solaris 11 kernel parameters are configured in the `/etc/system` file in the global zone.

- Shared disks, also known as `/dev/did/rdsk` devices, are available.

- Oracle Virtual IP (VIP) and Single Client Access Name (SCAN) IP requirements have been allocated on the public network.

- For Oracle Solaris Cluster versions up to 4.2, each public-network adapter that is used for data-service traffic must be configured in an IPMP group. Starting with Oracle Solaris Cluster 4.3, you can configure the adapter with any Public Network Management (PNM) object, which includes IPMP groups, link aggregations, and Virtual Network Interface Cards (VNICs) that are directly backed by link aggregations.

- Starting with Oracle Solaris Cluster 4.3, public-network adapter that is used for data-service traffic must belong to a PNM object that includes IPMP groups, link aggregations, and VNICs that are directly backed by link aggregations.

**See Also:**

- Oracle Solaris Cluster Software Installation Guide for Oracle Solaris Cluster 4.3:

  [http://docs.oracle.com/cd/E56676_01/html/E56678/babccjcd.html#CLISTz40001f61026966](https://docs.oracle.com/cd/E18728_01/html/821-2852/index.html)

- Oracle Solaris Cluster Data Service for Oracle Real Application Clusters Guide for Oracle Solaris Cluster 3.3:

  <https://docs.oracle.com/cd/E18728_01/html/821-2852/index.html>

- Oracle Solaris Cluster Data Service for Oracle Real Application Clusters Guide for Oracle Solaris Cluster 4:

  <http://www.oracle.com/pls/topic/lookup?ctx=cluster4&id=CLRAC>

**Parent topic:** [Deploying Oracle RAC on Oracle Solaris Cluster Zone Clusters](deploying-oracle-rac-on-oracle-solaris-cluster-zone-clusters.md)
