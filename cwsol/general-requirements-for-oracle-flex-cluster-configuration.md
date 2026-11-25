Review this information about network requirements for Oracle Flex Cluster configuration.

### Network Requirements for Oracle Flex Cluster Configuration

- You must use Grid Naming Service (GNS) with an Oracle Flex Cluster deployment.

- You must configure the GNS VIP as a static IP address.

- On Multi-cluster configurations, you must identify the GNS client data file location. The GNS client data files are copied over from the GNS server before you start configuring a GNS client cluster.

- All public network addresses, whether assigned manually or automatically, must be in the same subnet range.

- All Oracle Flex Cluster addresses must be either static IP addresses, DHCP addresses assigned through DHCP (IPv4) or autoconfiguration addresses assigned through an autoconfiguration service (IPv6), registered in the cluster through GNS.

**Parent topic:** [Configuration Requirements for Oracle Flex Clusters](configuration-requirements-for-oracle-flex-clusters.md)
