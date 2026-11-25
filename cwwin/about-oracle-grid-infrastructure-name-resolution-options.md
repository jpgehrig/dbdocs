## About Oracle Grid Infrastructure Name Resolution Options

Before starting the installation, you must have at least two interfaces configured on each node: One for the private IP address and one for the public IP address.

You can configure IP addresses for Oracle Grid Infrastructure and Oracle RAC with one of the following options:

- Dynamic IP address assignment using Multi-cluster or standard Oracle Grid Naming Service (GNS). If you select this option, then network administrators delegate a subdomain to be resolved by GNS (standard or multicluster). Requirements for GNS are different depending on whether you choose to configure GNS with zone delegation (resolution of a domain delegated to GNS), or without zone delegation (a GNS virtual IP address without domain delegation).

- For GNS with zone delegation:

  - For IPv4, a DHCP service running on the public network the cluster uses

  - For IPv6, an autoconfiguration service running on the public network the cluster uses

  - Enough DHCP addresses to provide 1 IP address for each node, and 3 IP addresses for the cluster used by the Single Client Access Name (SCAN) for the cluster

- Use an existing GNS configuration. Starting with Oracle Grid Infrastructure 12c Release 1 (12.1), a single GNS instance can be used by multiple clusters. To use GNS for multiple clusters, the DNS administrator must have delegated a zone for use by GNS. Also, there must be an instance of GNS started somewhere on the network and the GNS instance must be accessible (not blocked by a firewall). All of the node names registered with the GNS instance must be unique.

- Static IP address assignment using DNS or host file resolution. If you select this option, then network administrators assign a fixed IP address for each physical host name in the cluster and for IPs for the Oracle Clusterware managed VIPs. In addition, domain name system (DNS)-based static name resolution is used for each node, or host files for both the clusters and clients have to be updated, and SCAN functionality is limited. Selecting this option requires that you request network administration updates when you modify the cluster.

**Note:**

- Oracle recommends that you use a static host name for all non-VIP server node public host names.

- Public IP addresses and virtual IP addresses must be in the same subnet.

- Oracle only supports DHCP-assigned networks for the default network, not for any subsequent networks.

For clusters using single interfaces for private networks, each node's private interface for interconnects must be on the same subnet, and that subnet must connect to every node of the cluster. For example, if the private interfaces have a subnet mask of 255.255.255.0, then your private network is in the range 192.168.0.0--192.168.0.255, and your private addresses must be in the range of 192.168.0.\[0-255\]. If the private interfaces have a subnet mask of 255.255.0.0, then your private addresses can be in the range of 192.168.\[0-255\].\[0-255\].

**Parent topic:** [Oracle Grid Infrastructure IP Name and Address Requirements](oracle-grid-infrastructure-ip-name-and-address-requirements.md)
