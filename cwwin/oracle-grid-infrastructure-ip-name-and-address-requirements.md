## Oracle Grid Infrastructure IP Name and Address Requirements

The Oracle Grid Naming Service (GNS) is used with large clusters to ease network administration cost.

For small clusters, you can use a static configuration of IP addresses. For large clusters, manually maintaining the large number of required IP addresses becomes too cumbersome.

- [About Oracle Grid Infrastructure Name Resolution Options](about-oracle-grid-infrastructure-name-resolution-options.md)
  Before starting the installation, you must have at least two interfaces configured on each node: One for the private IP address and one for the public IP address.
- [Cluster Name and SCAN Requirements](cluster-name-and-scan-requirements.md)
  Review this information before you select the cluster name and SCAN.
- [IP Name and Address Requirements For Grid Naming Service (GNS)](ip-name-and-address-requirements-for-grid-naming-service-gns.md)
  The network administration must configure the domain name server (DNS) to delegate resolution requests for cluster names (any names in the subdomain delegated to the cluster) to the GNS.
- [IP Name and Address Requirements For Multi-Cluster GNS](ip-name-and-address-requirements-for-multi-cluster-gns.md)
  Multi-cluster GNS differs from standard GNS in that Multi-cluster GNS provides a single networking service across a set of clusters, rather than a networking service for a single cluster.
- [IP Address Requirements for Manual Configuration](ip-address-requirements-for-manual-configuration.md)
  If you do not enable GNS, then the public and VIP addresses for each node must be static IP addresses. Public, VIP and SCAN addresses must be on the same subnet.
- [Confirming the DNS Configuration for SCAN](confirming-the-dns-configuration-for-scan.md)
  You can use the `nslookup` command to confirm that the DNS is correctly associating the SCAN with the addresses.
- [Grid Naming Service for a Traditional Cluster Configuration Example](grid-naming-service-for-a-traditional-cluster-configuration-example.md)
  To use GNS, you must specify a static IP address for the GNS VIP address, and you must have a subdomain configured on your domain name servers (DNS) to delegate resolution for that subdomain to the static GNS IP address.
- [Domain Delegation to Grid Naming Service](domain-delegation-to-grid-naming-service.md)
  If you are configuring Grid Naming Service (GNS) for a standard cluster, then before installing Oracle Grid Infrastructure you must configure DNS to send to GNS any name resolution requests for the subdomain served by GNS.
- [Manual IP Address Configuration Example](manual-ip-address-configuration-example.md)
  If you choose not to use GNS, then before installation you must configure public, virtual, and private IP addresses. Also, check that the default gateway can be accessed by a `ping` command.

**Parent topic:** [Configuring Networks for Oracle Grid Infrastructure and Oracle RAC](configuring-networks-for-oracle-grid-infrastructure-and-oracle-rac.md)
