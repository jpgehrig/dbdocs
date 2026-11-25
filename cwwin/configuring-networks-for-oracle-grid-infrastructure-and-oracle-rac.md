## 4 Configuring Networks for Oracle Grid Infrastructure and Oracle RAC

Check that you have the networking hardware and internet protocol (IP) addresses required for an Oracle Grid Infrastructure for a cluster installation.

**Note:**

For the most up-to-date information about supported network protocols and hardware for Oracle RAC installations, refer to the Certify pages on the My Oracle Support website. See "[Checking Hardware and Software Certification on My Oracle Support](checking-hardware-and-software-certification-on-my-oracle-support.md)" for instructions.

- [About Oracle Grid Infrastructure Network Configuration Options](about-oracle-grid-infrastructure-network-configuration-options.md)
  Ensure that you have the networking hardware and internet protocol (IP) addresses required for an Oracle Grid Infrastructure for a cluster installation.
- [Understanding Network Addresses](understanding-network-addresses.md)
  During installation, you are asked to identify the planned use for each network interface that Oracle Universal Installer (OUI) detects on your cluster node.
- [Network Interface Hardware Requirements](network-interface-hardware-requirements.md)
  Review these requirements to ensure that you have the minimum network hardware technology for Oracle Grid Infrastructure clusters.
- [Network Configuration Tasks for Windows Server Deployments](network-configuration-tasks-for-windows-server-deployments.md)
  Microsoft Windows Server has many unique networking features. Some of these features require special configuration to enable Oracle software to run correctly on Windows Server.
- [Oracle Grid Infrastructure IP Name and Address Requirements](oracle-grid-infrastructure-ip-name-and-address-requirements.md)
  The Oracle Grid Naming Service (GNS) is used with large clusters to ease network administration cost.
- [Intended Use of Network Adapters](intended-use-of-network-adapters.md)
  During installation, you are asked to identify the planned use for each network adapter (or network interface) that Oracle Universal Installer (OUI) detects on your cluster node.
- [Broadcast Requirements for Networks Used by Oracle Grid Infrastructure](broadcast-requirements-for-networks-used-by-oracle-grid-infrastructure.md)
  Broadcast communications address resolution protocol (ARP) and User Datagram Protocol (UDP) must work properly across all the public and private interfaces configured for use by Oracle Grid Infrastructure.
- [Multicast Requirements for Networks Used by Oracle Grid Infrastructure](multicast-requirements-for-networks-used-by-oracle-grid-infrastructure.md)
  On each cluster member node the Oracle multicast DNS (mDNS) daemon uses multicasting on all network interfaces to communicate with other nodes in the cluster.
- [Configuring Multiple ASM Interconnects on Microsoft Windows Platforms](multiple-private-interconnects-on-microsoft-windows-platforms.md)
  When using multiple network interface cards for the Oracle Automatic Storage Management (Oracle ASM) interconnect, you must enable the `weakhostsend` network parameter.
