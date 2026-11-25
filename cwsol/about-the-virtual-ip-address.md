The virtual IP (VIP) address is registered in the grid naming service (GNS), the DNS, or in a hosts file.

**Note:**

Starting with Oracle Grid Infrastructure 18c, using VIP is optional for Oracle Clusterware deployments. You can specify VIPs for all or none of the cluster nodes. However, specifying VIPs for selected cluster nodes is not supported.

Select an address for your VIP that meets the following requirements:

- The IP address and host name are currently unused (it can be registered in a DNS, but should not be accessible by a ping command)

- The VIP is on the same subnet as your public interface

If you are not using Grid Naming Service (GNS), then determine a virtual host name for each node. A virtual host name is a public node name that reroutes client requests sent to the node if the node is down. Oracle Database uses VIPs for client-to-database connections, so the VIP address must be publicly accessible. Oracle recommends that you provide a name in the format hostname-vip. For example: `myclstr2-vip`.

**Parent topic:** [Understanding Network Addresses](understanding-network-addresses.md)
