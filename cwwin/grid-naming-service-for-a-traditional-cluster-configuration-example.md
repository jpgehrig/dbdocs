## Grid Naming Service for a Traditional Cluster Configuration Example

To use GNS, you must specify a static IP address for the GNS VIP address, and you must have a subdomain configured on your domain name servers (DNS) to delegate resolution for that subdomain to the static GNS IP address.

As nodes are added to the cluster, your organization's DHCP server can provide addresses for these nodes dynamically. These addresses are then registered automatically in GNS, and GNS provides resolution within the subdomain to cluster node addresses registered with GNS.

Because allocation and configuration of addresses is performed automatically with GNS, no further configuration is required. Oracle Clusterware provides dynamic network configuration as nodes are added to or removed from the cluster. The following example is provided only for information.

With IPv6 networks, the IPv6 auto configuration feature assigns IP addresses and no DHCP server is required.

Assuming a two node cluster where you have defined the GNS VIP, after installation you might have a configuration similar to that shown in the following table. In this configuration, the cluster name is `mycluster`, the GNS parent domain is `gns.example.com`, the subdomain is `cluster01.example.com`, the 192.0.2 portion of the IP addresses represents the cluster public IP address subdomain, and 192.168.0 represents the private IP address subdomain.

Table 4-1 Example of a Grid Naming Service Network Configuration

| Identity       | Home Node | Host Node                      | Given Name                             | Type    | Address     | Address Assigned By            | Resolved By |
|:---------------|:----------|:-------------------------------|:---------------------------------------|:--------|:------------|:-------------------------------|:------------|
| GNS VIP        | None      | Selected by Oracle Clusterware | `mycluster-gns-vip.example.com`        | Virtual | 192.0.2.1   | Fixed by network administrator | DNS         |
| Node 1 Public  | Node 1    | `node1`                        | `node1`<sup>Foot 1Foot 1</sup>         | Public  | 192.0.2.101 | Fixed                          | GNS         |
| Node 1 VIP     | Node 1    | Selected by Oracle Clusterware | `node1-vip`                            | Virtual | 192.0.2.104 | DHCP                           | GNS         |
| Node 1 Private | Node 1    | `node1`                        | `node1-priv`                           | Private | 192.168.0.1 | Fixed or DHCP                  | GNS         |
| Node 2 Public  | Node 2    | `node2`                        | node2<sup>Foot 1</sup>                 | Public  | 192.0.2.102 | Fixed                          | GNS         |
| Node 2 VIP     | Node 2    | Selected by Oracle Clusterware | `node2-vip`                            | Virtual | 192.0.2.105 | DHCP                           | GNS         |
| Node 2 Private | Node 2    | `node2`                        | `node2-priv`                           | Private | 192.168.0.2 | Fixed or DHCP                  | GNS         |
| SCAN VIP 1     | none      | Selected by Oracle Clusterware | `mycluster-scan.cluster01.example.com` | Virtual | 192.0.2.201 | DHCP                           | GNS         |
| SCAN VIP 2     | none      | Selected by Oracle Clusterware | `mycluster-scan.cluster01.example.com` | Virtual | 192.0.2.202 | DHCP                           | GNS         |
| SCAN VIP 3     | none      | Selected by Oracle Clusterware | `mycluster-scan.cluster01.example.com` | Virtual | 192.0.2.203 | DHCP                           | GNS         |

<sup>Footnote 1</sup> Node host names may resolve to multiple addresses, including VIP addresses currently running on that host.

**Parent topic:** [Oracle Grid Infrastructure IP Name and Address Requirements](oracle-grid-infrastructure-ip-name-and-address-requirements.md)
