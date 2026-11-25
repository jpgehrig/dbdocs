Complete these preupgrade checks to avoid issues during the Oracle Restart upgrade process.

1.  Review the new features for the Oracle Restart release to which you want to upgrade.

2.  Ensure that you have all of the information you need for the upgrade. For example:

    - An Oracle base location for Oracle Restart.

    - An Oracle Restart home location that is different from your existing Oracle Restart home.

    - Privileged user operating system groups.

3.  Unset the `%ORACLE_HOME%`, `%ORACLE_BASE%`, and `%ORACLE_SID%` environment variables because these environment variables are used during the upgrade. For example, as the `grid` user, run the following commands:

        SET ORACLE_HOME=""
        SET ORACLE_BASE=""
        SET ORACLE_SID=""

4.  Set the value of the `TNS_ADMIN` variable under environment variables to `NULL`.

5.  Unset the `PATH` environment variable:
    1.  Right-click My Computer, and select Properties.
    2.  Select the Advanced system settings option in the right pane.
    3.  Select the Environment Variables option in the Advanced tab.
    4.  Select the `Path` variable and click Edit.
    5.  Click Delete in the Edit environment variable window, and click OK to confirm.

**Related Topics**

- [Oracle Database New Features Guide](../newft/index.md)

**Parent topic:** [Preparing to Upgrade Oracle Restart](preparing-to-upgrade-oracle-restart.md)
