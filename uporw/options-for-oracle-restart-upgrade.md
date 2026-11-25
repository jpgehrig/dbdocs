Review these upgrade options and restrictions when you upgrade to Oracle Grid Infrastructure for a standalone server (Oracle Restart) 19c.

Supported upgrade paths for Oracle Restart for this release are:

- Oracle Restart upgrade from 11g Release 2 (11.2.0.4) to Oracle Restart 19c.

- Oracle Restart upgrade from 12c Release 1 (12.1.0.2) to Oracle Restart 19c.

- Oracle Restart upgrade from 12c Release 2 (12.2) to Oracle Restart 19c.

- Oracle Restart upgrade from 18c to Oracle Restart 19c.

### Restrictions for Oracle Restart Upgrades

- Oracle Restart upgrades are always out-of-place upgrades. You cannot perform an in-place upgrade of Oracle Restart to an existing Grid home.
- The same user that owned the earlier release of the Oracle Restart software must perform the Oracle Restart 19c upgrade.
- Do not delete directories in the Grid home. For example, do not delete the directory `Grid_home\OPatch`. If you delete the directory, then the Oracle Restart installation owner cannot use the OPatch utility to patch the Grid home, and OPatch displays the error message `"'checkdir' error: cannot create Grid_home\OPatch"`.
- The software in the 19c Oracle Restart home is not fully functional until the upgrade is complete. Running `srvctl`, `crsctl`, and other commands from the new Grid home are not supported until the the upgrade is complete.
- To manage databases in an existing earlier release database home during the Oracle Restart upgrade, use the `srvctl` utility from the existing database home.

**Parent topic:** [Preparing to Upgrade Oracle Restart](preparing-to-upgrade-oracle-restart.md)
