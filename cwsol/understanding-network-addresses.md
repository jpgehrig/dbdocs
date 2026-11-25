Identify each interface as a public or private interface, or as an interface that you do not want Oracle Grid Infrastructure or Oracle Flex ASM cluster to use.

During installation, you are asked to identify the planned use for each network interface that OUI detects on your cluster node. Identify each interface as a public or private interface, or as an interface that you do not want Oracle Grid Infrastructure or Oracle Flex ASM cluster to use. Public and virtual IP addresses are configured on public interfaces. Private addresses are configured on private interfaces.

- [About the Public IP Address](about-the-public-ip-address.md)
  The public IP address is assigned dynamically using Dynamic Host Configuration Protocol (DHCP), or defined statically in a Domain Name System (DNS) or in a hosts file.
- [About the Private IP Address](about-the-private-ip-address.md)
  Oracle Clusterware uses interfaces marked as private for internode communication.
- [About the Virtual IP Address](about-the-virtual-ip-address.md)
  The virtual IP (VIP) address is registered in the grid naming service (GNS), the DNS, or in a hosts file.
- [About the Grid Naming Service (GNS) Virtual IP Address](about-the-grid-naming-service-vip-address.md)
  The GNS virtual IP address is a static IP address configured in the Domain Name System (DNS).
- [About the SCAN](about-the-scan.md)
  During the installation of Oracle Grid Infrastructure, several Oracle Clusterware resources are created for the SCAN.
- [About Shared SCAN](about-shared-scan.md)
  Shared SCAN provides the capability to share SCAN VIPs across multiple clusters, thus reducing the number of IP addresses that must be assigned when deploying Oracle Clusters.

**Parent topic:** [Configuring Networks for Oracle Grid Infrastructure and Oracle RAC](configuring-networks-for-oracle-grid-infrastructure-and-oracle-rac.md)
