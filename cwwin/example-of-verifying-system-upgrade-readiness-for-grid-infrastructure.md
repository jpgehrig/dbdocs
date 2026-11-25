## Example of Verifying System Upgrade Readiness for Grid Infrastructure

You can use the `runcluvfy.bat` command to check your system before upgrading.

Verify that the permissions required for installing Oracle Grid Infrastructure have been configured by running the following command:

    C:\app\19.0.0\grid> runcluvfy.bat stage -pre crsinst -upgrade -rolling
    -src_crshome C:\app\18.0.0\grid -dest_crshome C:\app\19.0.0\grid
    -dest_version 19.0.0.0.0 -verbose

**Related Topics**

- [Restrictions and Guidelines for Oracle Grid Infrastructure Upgrades](restrictions-and-guidelines-for-oracle-grid-infrastructure-upgrades.md)

**Parent topic:** [Using CVU to Validate Readiness for Oracle Clusterware Upgrades](using-cvu-to-validate-readiness-for-oracle-clusterware-upgrades.md)
