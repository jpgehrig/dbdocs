## IP Address Requirements for Manual Configuration

If you do not enable GNS, then the public and VIP addresses for each node must be static IP addresses. Public, VIP and SCAN addresses must be on the same subnet.

IP addresses on the subnet you identify as private are assigned as private IP addresses for cluster member nodes. Oracle Clusterware manages private IP addresses in the private subnet. You do not have to configure these addresses manually in a hosts file.

The cluster must have the following addresses configured:

- A public IP address for each node configured before installation, and resolvable to that node before installation.

- A VIP address for each node configured before installation, but not currently in use (or not resolvable to that node before installation).

- Three static IP addresses configured on the domain name server (DNS) before installation so that the three IP addresses are associated with the name provided as the SCAN, and all three addresses are returned by the DNS to the requestor. These addresses must be configured before installation in the DNS to resolve to addresses that are not currently in use. The SCAN name must meet the requirements specified in "[Cluster Name and SCAN Requirements](cluster-name-and-scan-requirements.md)".

- A private IP address for each node configured before installation, but on a separate, private network, with its own subnet. The IP address should not be resolvable except by other cluster member nodes.

- A set of one or more networks over which Oracle ASM serves its clients. The ASM network does not have to be a physical network; it can be a virtual network. The ASM network must use either a third NIC, or share a private network adapter. The NIC can be a virtual NIC.

**Note:**

Oracle strongly recommends that you do not configure SCAN VIP addresses in the hosts file. Use DNS resolution for SCAN VIPs. If you use the hosts file to resolve SCANs, then you will only be able to resolve to one IP address and you will have only one SCAN address.

Configuring SCANs in a DNS or a hosts file is the only supported configuration. Configuring SCANs in a Network Information Service (NIS) is not supported.

**Related Topics**

- [Understanding Network Addresses](understanding-network-addresses.md)

**Parent topic:** [Oracle Grid Infrastructure IP Name and Address Requirements](oracle-grid-infrastructure-ip-name-and-address-requirements.md)
