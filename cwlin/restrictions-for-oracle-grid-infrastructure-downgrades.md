## Restrictions for Oracle Grid Infrastructure Downgrades

Review the following information for restrictions and changes for downgrading Oracle Grid Infrastructure installations.

- When downgrading Oracle Member Cluster to 12c Release 2 (12.2), you must start Oracle Clusterware on last downgraded node first and then on other nodes.

- When you downgrade from an Oracle Grid Infrastructure 12c Release 2 (12.2) or later releases to Oracle Grid Infrastructure 11g Release 2 (11.2), you downgrade from an Oracle Flex cluster configuration to a Standard cluster configuration since all cluster configurations in releases earlier than Oracle Grid Infrastructure 12c are Standard cluster configurations.

- You can only downgrade to the Oracle Grid Infrastructure release you upgraded from. For example, if you upgraded from Oracle Grid Infrastructure 11g Release 2 (11.2) to Oracle Grid Infrastructure 19c, you can only downgrade to Oracle Grid Infrastructure 11g Release 2 (11.2).

**Parent topic:** [Downgrading Oracle Clusterware to an Earlier Release](downgrading-oracle-clusterware-after-an-upgrade.md)
