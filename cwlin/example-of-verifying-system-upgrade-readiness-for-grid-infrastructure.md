## Example of Verifying System Upgrade Readiness for Grid Infrastructure

You can verify that the permissions required for installing Oracle Clusterware have been configured on the nodes `node1` and `node2` by running a command similar to the following.

    $ /u01/app/19.0.0/grid/runcluvfy.sh stage -pre crsinst -upgrade -rolling -src_crshome
    /u01/app/18.0.0/grid -dest_crshome /u01/app/19.0.0/grid -dest_version
    19.0.0.0.0 -fixup -verbose

**Related Topics**

- [Oracle Database Upgrade Guide](../upgrd/intro-to-upgrading-oracle-database.md)

**Parent topic:** [Using CVU to Validate Readiness for Oracle Clusterware Upgrades](using-cvu-to-validate-readiness-for-oracle-clusterware-upgrades.md)
