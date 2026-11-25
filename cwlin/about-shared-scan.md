## About Shared SCAN

Shared SCAN provides the capability to share SCAN VIPs across multiple clusters, thus reducing the number of IP addresses that must be assigned when deploying Oracle Clusters.

In earlier versions of the Oracle Clusterware, SCAN VIPs were configured on a per cluster basis. With shared SCAN, the same SCAN is used among multiple clusters, so that only one of these clusters runs SCAN listeners. The databases of all clusters use the SCAN VIPs of this cluster, for all their database connections. Each cluster has its own set of ports, instead of SCAN VIPs. Clusters using shared SCAN can name their database services as desired, without naming conflicts if one or more of these clusters are configured with services of the same name.

**Parent topic:** [Understanding Network Addresses](understanding-network-addresses.md)
