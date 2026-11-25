## Proper Management of AutoUpgrade Database Changes

AutoUpgrade is a powerful utility, which requires that you use it responsibly. Review and avoid using AutoUpgrade in ways that put the database at risk.

The following is a list of improper uses of AutoUpgrade, and ways of attempting to work around problems that result from these errors.

### Breaking AutoUpgrade Resume Capability During Deployment

Problem Description::Using the `–clean_recovery_data` option prevents AutoUpgrade from resuming or restoring the database.

Workaround: Restore from a backup copy of the database.

Cause: Running the AutoUpgrade in deploy mode, and then interrupting its execution on any stage after the fixups are completed, and running the option `clear_recovery_data` before resuming and completing successfully an AutoUpgrade deploy command. For example:

    java -jar autoupgrade.jar -config config.cfg -mode deploy
    Ctrl+C //sample interruption
    java -jar autoupgrade.jar -config config.cfg –clear_recovery_data
    java -jar autoupgrade.jar -config config.cfg -mode deploy

### Changing AutoUpgrade Global Log Directory During or After Deployment

Problem Description: If you change the global directory during or after running a deploy command, then the AutoUpgrade utility is unable to resume its pending work.

Workaround: Restore from a backup copy of the database.

Cause: The AutoUpgrade global logs directory also contains files used by the AutoUpgrade Utility to track the state of its operations. If you run the tool in deploy mode, and the deploy operation is stopped, and then rename or drop the global log directory, then the AutoUpgrade utility is unable to determine the state in which the deploy operation was stopped. As a result, when you restart AutoUpgrade, it begins the upgrade operation from the beginning, and the initial GRP is overwritten. You cannot use that GRP to restore the original database.

### Use of Keystore With Credentials Not Set With AUTOLOGIN

Problem Description: You run the tool, and you have keystore credentials configured, but AutoUpgrade is unable to log in to the database.

Workaround: Create an Autologin Keystore, and configure the database with auto-login enabled.

At the time of this release. AutoUpgrade does not support the use of keystore credentials unless they are configured for automatic logins into the database

**Related Topics**

- [Performing Operations That Require a Keystore Password](../asoag/managing-keystore-and-tde-master-encryption-key.md)

**Parent topic:** [Using AutoUpgrade for Oracle Database Upgrades](using-autoupgrade-oracle-database-upgrades.md)
