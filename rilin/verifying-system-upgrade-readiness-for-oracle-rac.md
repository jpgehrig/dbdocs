## Example of Verifying System Upgrade Readiness for Oracle RAC

You can verify that the permissions required for installing Oracle RAC have been configured on the nodes `node1` and `node2` by running the following command.

    $ ./cluvfy stage -pre dbinst -upgrade
    -src_dbhome /u01/app/oracle/product/18.0.0/dbhome_1
    -dest_dbhome /u01/app/oracle/product/19.0.0/dbhome_1
    -dest_version 19.0.0.0.0 -fixup -verbose

**Parent topic:** [Using CVU to Validate Readiness for Oracle RAC Upgrades](using-cvu-to-validate-readiness-for-oracle-rac-upgrades.md)
