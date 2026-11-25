## Example of Verifying System Upgrade Readiness for Oracle RAC Infrastructure

You can verify that the permissions required for installing Oracle RAC have been configured on the nodes `node1` and `node2` using `cluvfy`.

    C:\..bin> cluvfy stage -pre dbinst -upgrade
    -src_dbhome C:\app\oracle\product\12.2.0\dbhome_1
    -dest_dbhome C:\app\oracle\product\19.0.0\dbhome_1
    -dest_version 19.0.0.0.0 -verbose

**Parent topic:** [Using CVU to Validate Readiness for Oracle RAC Upgrades](using-cvu-to-validate-readiness-for-oracle-rac-upgrades.md)
