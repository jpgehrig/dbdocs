## Manual IP Address Configuration Example

If you choose not to use GNS, then before installation you must configure public, virtual, and private IP addresses. Also, check that the default gateway can be accessed by a `ping` command.

To find the default gateway, use the `ipconfig` command, as described in your operating system's help utility.

For example, with a two node cluster where the cluster name is `mycluster`, and each node has one public and one private interface, and you have defined a SCAN domain address to resolve on your DNS to one of three IP addresses, you might have the configuration shown in the following table for your network interfaces.

Table 4-2 Manual Network Configuration Example

| Identity       | Home Node | Host Node                      | Given Name                     | Type    | Address     | Address Assigned By | Resolved By              |
|:---------------|:----------|:-------------------------------|:-------------------------------|:--------|:------------|:--------------------|:-------------------------|
| Node 1 Public  | Node 1    | `node1`                        | `node1`<sup>Foot 1Foot 1</sup> | Public  | 192.0.2.101 | Fixed               | DNS                      |
| Node 1 VIP     | Node 1    | Selected by Oracle Clusterware | `node1-vip`                    | Virtual | 192.0.2.104 | Fixed               | DNS, hosts file          |
| Node 1 Private | Node 1    | `node1`                        | `node1-priv`                   | Private | 192.168.0.1 | Fixed               | DNS, hosts file, or none |
| Node 2 Public  | Node 2    | `node2`                        | `node2`<sup>Foot 1</sup>       | Public  | 192.0.2.102 | Fixed               | DNS                      |
| Node 2 VIP     | Node 2    | Selected by Oracle Clusterware | `node2-vip`                    | Virtual | 192.0.2.105 | Fixed               | DNS, hosts file          |
| Node 2 Private | Node 2    | `node2`                        | `node2-priv`                   | Private | 192.168.0.2 | Fixed               | DNS, hosts file, or none |
| SCAN VIP 1     | none      | Selected by Oracle Clusterware | `mycluster-scan`               | Virtual | 192.0.2.201 | Fixed               | DNS                      |
| SCAN VIP 2     | none      | Selected by Oracle Clusterware | `mycluster-scan`               | Virtual | 192.0.2.202 | Fixed               | DNS                      |
| SCAN VIP 3     | none      | Selected by Oracle Clusterware | `mycluster-scan`               | Virtual | 192.0.2.203 | Fixed               | DNS                      |

<sup>Footnote 1</sup> Node host names may resolve to multiple addresses.

You do not have to provide a private name for the interconnect. If you want name resolution for the interconnect, then you can configure private IP names in the system `hosts` file or DNS. However, Oracle Clusterware assigns interconnect addresses on the interface defined during installation as the private interface (`Local Area Connection 2`, for example), and to the subnet used for the private subnet.

The addresses to which the SCAN resolves are assigned by Oracle Clusterware, so they are not fixed to a particular node. To enable VIP failover, the configuration shown in the previous table defines the SCAN addresses and the public and VIP addresses of both nodes on the same subnet, 192.0.2.

**Note:**

All host names must conform to the Internet Engineering Task Force RFC 952 standard, which permits alphanumeric characters. Host names using underscores ("\_") are not allowed.

**Parent topic:** [Oracle Grid Infrastructure IP Name and Address Requirements](oracle-grid-infrastructure-ip-name-and-address-requirements.md)
