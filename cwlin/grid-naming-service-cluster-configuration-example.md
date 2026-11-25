## Grid Naming Service Cluster Configuration Example

Review this example to understand Grid Naming Service configuration.

To use GNS, you must specify a static IP address for the GNS VIP address, and you must have a subdomain configured on your DNS to delegate resolution for that subdomain to the static GNS IP address.

As nodes are added to the cluster, your organization's DHCP server can provide addresses for these nodes dynamically. These addresses are then registered automatically in GNS, and GNS provides resolution within the subdomain to cluster node addresses registered with GNS.

Because allocation and configuration of addresses is performed automatically with GNS, no further configuration is required. Oracle Clusterware provides dynamic network configuration as nodes are added to or removed from the cluster. The following example is provided only for information.

With IPv6 networks, the IPv6 auto configuration feature assigns IP addresses and no DHCP server is required.

With a two node cluster where you have defined the GNS VIP, after installation you might have a configuration similar to the following for a two-node cluster, where the cluster name is `mycluster`, the GNS parent domain is `gns.example.com`, the subdomain is `cluster01.example.com`, the `192.0.2` portion of the IP addresses represents the cluster public IP address subdomain, and `192.168` represents the private IP address subdomain:

Table 5-1 Grid Naming Service Cluster Configuration Example

| Identity       | Home Node | Host Node                      | Given Name                                     | Type    | Address     | Address Assigned By        | Resolved By |
|:---------------|:----------|:-------------------------------|:-----------------------------------------------|:--------|:------------|:---------------------------|:------------|
| GNS VIP        | None      | Selected by Oracle Clusterware | mycluster-gns-vip.example.com                  | virtual | 192.0.2.1   | Fixed by net administrator | DNS         |
| Node 1 Public  | Node 1    | node1                          | node1                                          | public  | 192.0.2.101 | Fixed                      | GNS         |
| Node 1 VIP     | Node 1    | Selected by Oracle Clusterware | node1-vip                                      | virtual | 192.0.2.104 | DHCP                       | GNS         |
| Node 1 Private | Node 1    | node1                          | node1-priv                                     | private | 192.168.0.1 | Fixed or DHCP              | GNS         |
| Node 2 Public  | Node 2    | node2                          | node2                                          | public  | 192.0.2.102 | Fixed                      | GNS         |
| Node 2 VIP     | Node 2    | Selected by Oracle Clusterware | node2-vip                                      | virtual | 192.0.2.105 | DHCP                       | GNS         |
| Node 2 Private | Node 2    | node2                          | node2-priv                                     | private | 192.168.0.2 | Fixed or DHCP              | GNS         |
| SCAN VIP 1     | none      | Selected by Oracle Clusterware | mycluster-scan.mycluster.cluster01.example.com | virtual | 192.0.2.201 | DHCP                       | GNS         |
| SCAN VIP 2     | none      | Selected by Oracle Clusterware | mycluster-scan.mycluster.cluster01.example.com | virtual | 192.0.2.202 | DHCP                       | GNS         |
| SCAN VIP 3     | none      | Selected by Oracle Clusterware | mycluster-scan.mycluster.cluster01.example.com | virtual | 192.0.2.203 | DHCP                       | GNS         |

**Parent topic:** [Configuring Networks for Oracle Grid Infrastructure and Oracle RAC](configuring-networks-for-oracle-grid-infrastructure-and-oracle-rac.md)
