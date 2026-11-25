You must define one Multi-node Disk Heartbeat (MNDHB) network for each Oracle Clusterware voting file.

Each MNDHB and voting disk pair must be located on a single hard disk, separate from the other pairs. You must also configure MNDHB so that the node is halted if access is lost to a quorum of the MNDHB networks in the enhanced concurrent volume group.

To reduce the likelihood of a cluster partition, IBM recommends that HACMP is deployed with multiple IP networks and at least one non-IP network. The non-IP networks can be implemented using RS232 or disk heart-beating. For systems using Oracle RAC and HACMP enhanced concurrent resources (enhanced concurrent logical volumes) for database storage, you must configure MNDHB networks.

Install, configure and have HACMP running before installing Oracle Clusterware. For an Oracle RAC configuration, do not use HACMP for IP failovers on the Oracle RAC network interfaces (public, VIP or private). These network interfaces should not be configured to use HACMP IP failover, as Oracle Clusterware manages VIP failovers for Oracle RAC. The Oracle RAC network interfaces are bound to individual nodes and Oracle RAC instances. Problems can occur with Oracle Clusterware if HACMP reconfigures IP addresses over different interfaces, or fails over addresses across nodes. You only can use HACMP for failover of IP address on Oracle RAC nodes if Oracle RAC does not use these addresses.

**Parent topic:** [Configuring HACMP Multinode Disk Heartbeat (MNDHB)](configuring-multi-node-disk-heartbeat.md)
