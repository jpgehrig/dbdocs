Review this information for Oracle Grid Infrastructure IP Name and Address requirements.

For small clusters, you can use a static configuration of IP addresses. For large clusters, manually maintaining the large number of required IP addresses becomes too cumbersome. Use Oracle Grid Naming Service with large clusters to ease network administration costs.

- [About Oracle Grid Infrastructure Name Resolution Options](about-oracle-grid-infrastructure-name-resolution-options.md)
  Before starting the installation, you must have at least two interfaces configured on each node: One for the private IP address, and one for the public IP address.
- [Cluster Name and SCAN Requirements](cluster-name-and-scan-requirements.md)
  Review this information before you select the cluster name and SCAN.
- [IP Name and Address Requirements For Grid Naming Service (GNS)](ip-name-and-address-requirements-for-grid-naming-service-gns.md)
  Review this information for IP name and address requirements for Grid Naming Service (GNS).
- [IP Name and Address Requirements For Multi-Cluster GNS](ip-name-and-address-requirements-for-multi-cluster-gns.md)
  Multi-cluster GNS differs from standard GNS in that Multi-cluster GNS provides a single networking service across a set of clusters, rather than a networking service for a single cluster.
- [IP Name and Address Requirements for Manual Configuration of Cluster](ip-name-and-address-requirements-for-manual-configuration-of-cluster.md)
  For Oracle Flex Clusters and Oracle Member Cluster for Applications, configure static cluster node names and addresses if you do not enable GNS.
- [Confirming the DNS Configuration for SCAN](confirming-the-dns-configuration-for-scan.md)
  Use the `nslookup` command to confirm that the DNS is correctly associating the SCAN with the addresses.

**Parent topic:** [Configuring Networks for Oracle Grid Infrastructure and Oracle RAC](configuring-networks-for-oracle-grid-infrastructure-and-oracle-rac.md)
