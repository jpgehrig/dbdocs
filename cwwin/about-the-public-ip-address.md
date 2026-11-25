## About the Public IP Address

The public IP address uses the public interface (the interface with access available to clients).

The public IP address is assigned dynamically using Dynamic Host Configuration Protocol (DHCP), or defined statically in a domain name system (DNS) or `hosts` file. The public IP address is the primary address for a cluster member node, and should be the address that resolves to the name returned when you enter the command `hostname`.

If you configure IP addresses manually, then avoid changing host names after you complete the Oracle Grid Infrastructure installation, including adding or deleting domain qualifications. A node with a new host name is considered a new host, and must be added to the cluster. A node under the old name will appear to be down until it is removed from the cluster.

**Parent topic:** [Understanding Network Addresses](understanding-network-addresses.md)
