For Oracle Flex Clusters and Oracle Member Cluster for Applications, configure static cluster node names and addresses if you do not enable GNS.

### IP Address Requirements for Static Clusters

Public and virtual IP names must conform with the RFC 952 standard, which allows alphanumeric characters and hyphens ("-"), but does not allow underscores ("\_").

Oracle Clusterware manages private IP addresses in the private subnet on interfaces you identify as private during the installation interview.

### Public IP Address Requirements

The cluster must have a public IP address for each node, with the following characteristics:

- Static IP address

- Configured before installation for each node, and resolvable to that node before installation

- On the same subnet as all other public IP addresses, VIP addresses, and SCAN addresses in the cluster

### Virtual IP Address Requirements

The cluster must have a virtual IP address for each node, with the following characteristics:

- Static IP address

- Configured before installation for each node, but not currently in use

- On the same subnet as all other public IP addresses, VIP addresses, and SCAN addresses in the cluster

### Single Client Access Name Requirements

The cluster must have a Single Client Access Name (SCAN) for the cluster, with the following characteristics:

- Three static IP addresses configured on the domain name server (DNS) before installation so that the three IP addresses are associated with the name provided as the SCAN, and all three addresses are returned in random order by the DNS to the requestor

- Configured before installation in the DNS to resolve to addresses that are not currently in use

- Given addresses on the same subnet as all other public IP addresses, VIP addresses, and SCAN addresses in the cluster

- Given a name conforms with the RFC 952 standard, which allows alphanumeric characters and hyphens ("-"), but does not allow underscores ("\_")

### Private IP Address Requirements

The cluster must have a private IP address for each node, with the following characteristics:

- Static IP address

- Configured before installation, but on a separate, private network, with its own subnet, that is not resolvable except by other cluster member nodes

The SCAN is a name used to provide service access for clients to the cluster. Because the SCAN is associated with the cluster as a whole, rather than to a particular node, the SCAN makes it possible to add or remove nodes from the cluster without needing to reconfigure clients. It also adds location independence for the databases, so that client configuration does not have to depend on which nodes are running a particular database. Clients can continue to access the cluster in the same way as with previous releases, but Oracle recommends that clients accessing the cluster use the SCAN.

**Note:**

The SCAN and cluster name are entered in separate fields during installation, so cluster name requirements do not apply to the SCAN name.

Oracle strongly recommends that you do not configure SCAN VIP addresses in the hosts file. Use DNS resolution for SCAN VIPs. If you use the hosts file to resolve SCANs, then the SCAN can resolve to one IP address only.

Configuring SCANs in a DNS or a hosts file is the only supported configuration. Configuring SCANs in a Network Information Service (NIS) is not supported.

**Parent topic:** [Oracle Grid Infrastructure IP Name and Address Requirements](oracle-grid-infrastructure-ip-name-and-address-requirements.md)
