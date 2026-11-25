Review this information to manually assign cluster node VIP names for the cluster nodes.

### Requirements for Manually-Assigned Addresses

If you choose to configure manually-assigned VIPs, then during installation, you must configure cluster node VIP names for all cluster nodes using one of the following options:

- Manual Names: Enter the host name and virtual IP name for each node manually. The names you provide must resolve to addresses configured on the DNS. Names must conform with the RFC 952 standard, which allows alphanumeric characters and hyphens ("-"), but does not allow underscores ("\_").

- Automatically Assigned Names: Enter string variables for values corresponding to host names that you have configured on the DNS. String variables allow you to assign a large number of names rapidly during installation. Configure addresses on the DNS with the following characteristics:

  - Hostname prefix: a prefix string used in each address configured on the DNS for use by cluster member nodes. For example: `mycloud`.

  - Range: A range of numbers to be assigned to the cluster member nodes, consisting of a starting node number and an ending node number, designating the end of the range. For example: `001` and `999`.

  - Node name suffix: A suffix added after the end of a range number to a public node name. For example: `nd`.

  - VIP name suffix: A suffix added after the end of a virtual IP node name. For example: `-vip`.

### Syntax

You can create manual addresses using alphanumeric strings.

Example 5-1 Examples of Manually-Assigned Addresses

`mycloud001nd; mycloud046nd; mycloud046-vip; mycloud348nd; mycloud784-vip`

**Parent topic:** [Configuration Requirements for Oracle Flex Clusters](configuration-requirements-for-oracle-flex-clusters.md)
