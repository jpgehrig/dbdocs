## Manual IP Address Configuration Example

If you choose not to use GNS, then before installation you must configure public, virtual, and private IP addresses.

Check that the default gateway can be accessed by a ping command. To find the default gateway, use the `route` command, as described in your operating system's help utility.

For example, with a two-node cluster where each node has one public and one private interface, and you have defined a SCAN domain address to resolve on your DNS to one of three IP addresses, you might have the configuration shown in the following table for your network interfaces:

Table 5-2 Manual Network Configuration Example

| Identity       | Home Node | Host Node                      | Given Name     | Type    | Address     | Address Assigned By | Resolved By                 |
|:---------------|:----------|:-------------------------------|:---------------|:--------|:------------|:--------------------|:----------------------------|
| Node 1 Public  | Node 1    | node1                          | node1          | public  | 192.0.2.101 | Fixed               | DNS                         |
| Node 1 VIP     | Node 1    | Selected by Oracle Clusterware | node1-vip      | virtual | 192.0.2.104 | Fixed               | DNS and hosts file          |
| Node 1 Private | Node 1    | node1                          | node1-priv     | private | 192.168.0.1 | Fixed               | DNS and hosts file, or none |
| Node 2 Public  | Node 2    | node2                          | node2          | public  | 192.0.2.102 | Fixed               | DNS                         |
| Node 2 VIP     | Node 2    | Selected by Oracle Clusterware | node2-vip      | virtual | 192.0.2.105 | Fixed               | DNS and hosts file          |
| Node 2 Private | Node 2    | node2                          | node2-priv     | private | 192.168.0.2 | Fixed               | DNS and hosts file, or none |
| SCAN VIP 1     | none      | Selected by Oracle Clusterware | mycluster-scan | virtual | 192.0.2.201 | Fixed               | DNS                         |
| SCAN VIP 2     | none      | Selected by Oracle Clusterware | mycluster-scan | virtual | 192.0.2.202 | Fixed               | DNS                         |
| SCAN VIP 3     | none      | Selected by Oracle Clusterware | mycluster-scan | virtual | 192.0.2.203 | Fixed               | DNS                         |

You do not need to provide a private name for the interconnect. If you want name resolution for the interconnect, then you can configure private IP names in the hosts file or the DNS. However, Oracle Clusterware assigns interconnect addresses on the interface defined during installation as the private interface (eth1, for example), and to the subnet used for the private subnet.

The addresses to which the SCAN resolves are assigned by Oracle Clusterware, so they are not fixed to a particular node. To enable VIP failover, the configuration shown in the preceding table defines the SCAN addresses and the public and VIP addresses of both nodes on the same subnet, 192.0.2.0/24.

**Note:**

All host names must conform to the RFC–952 standard, which permits alphanumeric characters, but does not allow underscores ("\_").

**Parent topic:** [Configuring Networks for Oracle Grid Infrastructure and Oracle RAC](configuring-networks-for-oracle-grid-infrastructure-and-oracle-rac.md)
