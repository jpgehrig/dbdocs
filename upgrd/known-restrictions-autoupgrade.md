## Known Restrictions for AutoUpgrade

If you encounter issues with your upgrade, review the known restrictions to find solutions.

- AutoUpgrade and Disk Space Issues
  If you run out of disk space while running AutoUpgrade, then review and apply the solutions outlined here.
- AutoUpgrade and OracleServiceAutoUpgradeSid
  The ability to use the Microsoft Windows service `OracleServiceAutoUpgradeSid` for patching and upgrading is deprected.

**Parent topic:** [Using AutoUpgrade for Oracle Database Upgrades](using-autoupgrade-oracle-database-upgrades.md)

### AutoUpgrade and Disk Space Issues

If you run out of disk space while running AutoUpgrade, then review and apply the solutions outlined here.

To assist you to avoid disk space issues. Oracle has added a check to calculate the required disk space. To see log sizing specifications, review the AutoUpgrade analyze reports. If the database runs out of disk space during the upgrade, then free up the required disk space for the database, and resume the job, if necessary.

Example 3-25 Disk Space Errors While Upgrade is Running

1.  Stop the current running upgrade

        abort -job 100

2.  Free up disk space so that the upgrade can resume.

3.  Resume the stopped upgrade

        resume -job 100

Example 3-26 Disk Space Errors After Upgrade has Completed

If AutoUpgrade completes with disk space errors then proceed as follows:

1.  Free up disk space so that the upgrade can resume.

2.  Restart AutoUpgrade to complete any remaining issues.

    For example, where the configuration file name is `yourconfigfile.cfg`:

        java -jar autoupgrade.jar -mode deploy -config yourconfigfile.cfg

**Parent topic:** Known Restrictions for AutoUpgrade

### AutoUpgrade and OracleServiceAutoUpgradeSid

The ability to use the Microsoft Windows service `OracleServiceAutoUpgradeSid` for patching and upgrading is deprected.

In previous releases, while it was not documented, it was possible to create the Microsoft Windows service `OracleServiceAutoUpgradeSid` for patching and upgrading. This capability will be removed. In future releases, AutoUpgrade will only support the creation of Microsoft Windows services for Oracle that require passwords to use the AutoUpgrade `load_win_credential` parameter. When this parameter is used, AutoUpgrade will then be able to create Oracle Services with the correct password in a secure manner, and provide a seamless operation for database administrators.

**Parent topic:** Known Restrictions for AutoUpgrade
