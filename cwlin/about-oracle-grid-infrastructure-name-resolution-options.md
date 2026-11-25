## About Oracle Grid Infrastructure Name Resolution Options

Before starting the installation, you must have at least two interfaces configured on each node: One for the private IP address, and one for the public IP address.

During installation, you are asked to identify the planned use for each network interface that Oracle Universal Installer (OUI) detects on your cluster node. Identify each interface as a public or private interface, or as an interface that you do not want Oracle Grid Infrastructure or Oracle ASM to use. Public and virtual internet protocol (VIP) addresses are configured on public interfaces. Private addresses are configured on private interfaces.

**Note:**

All name servers in the DNS configuration for a cluster must resolve to all host names used in the cluster, such as cluster node host name, VIP host name, and SCAN host name.

Configure IP addresses with one of the following options:

### Dynamic IP address assignment using Multi-cluster or standard Oracle Grid Naming Service (GNS)

If you select this option, then network administrators delegate a subdomain that GNS resolves (standard or multicluster). GNS requirements are different depending on how you configure zone delegation. If you configure GNS with zone delegation, then GNS is delegated a domain for which it resolves service requests. If you configure GNS without zone delegation, then GNS has a virtual IP address that is resolved by a DNS.

For GNS with zone delegation:

- For IPv4, a DHCP service running on the public network the cluster uses

- For IPv6, an autoconfiguration service running on the public network the cluster uses

- Enough addresses on the DHCP server to provide one IP address for each node, and three IP addresses for the cluster used by the Single Client Access Name (SCAN) for the cluster

### Use an existing GNS configuration

Starting with Oracle Grid Infrastructure 12c Release 1 (12.1), multiple clusters can use a single GNS instance. To use GNS for multiple clusters, the DNS administrator must have delegated a zone for use by GNS. Also, there must be an instance of GNS started somewhere on the network, and the GNS instance must be accessible (not blocked by a firewall). All of the node names registered with the GNS instance must be unique.

### Static IP address assignment using DNS or host file resolution

If you select this option, then network administrators assign a fixed IP address for each physical host name in the cluster, and for IPs for VIPs managed by Oracle Clusterware. In addition, either domain name server (DNS) based static name resolution is used for each node, or host files for both the clusters and clients have to be updated, resulting in limited SCAN functionality. Selecting this option requires that you request network administration updates when you modify the cluster.

For GNS without zone delegation, configure a GNS virtual IP address (VIP) for the cluster. To enable Oracle Flex Cluster, you must at least configure a GNS virtual IP address.

**Parent topic:** [Oracle Grid Infrastructure IP Name and Address Requirements](oracle-grid-infrastructure-ip-name-and-address-requirements.md)
