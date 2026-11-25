## Upgrading to Oracle Database 19c

This procedure describes how to upgrade an Oracle database from Oracle Database 18c to 19c with a single command, using Fleet Patching and Provisioning, both for managed and unmanaged Oracle homes.

### Before you Begin

- To upgrade to Oracle Database 19c, your source database must be either Oracle Database 11g release 2 (11.2.0.4), Oracle Database 12c release 1 (12.1.0.2 or 12.2.0.1), or Oracle Database 18c.

- Oracle Grid Infrastructure on which the pre-upgrade database is running must be of the same release or later than the database release to which you are upgrading.

- The source Oracle home to be upgraded can be a managed working copy, that is an Oracle home provisioned using Fleet Patching and Provisioning, or an unmanaged home, that is, an Oracle home not provisioned using Fleet Patching and Provisioning. If you are upgrading an unmanaged Oracle home, provide the complete path of the database for upgrade.

### Procedure to Upgrade Oracle Database using Fleet Patching and Provisioning

1.  From the Fleet Patching and Provisioning Server, run one of the following commands as per your source and destination database:
    1.  To upgrade an Oracle home managed by Fleet Patching and Provisioning, and there exist working copies of the source and destination databases, run:
            $ rhpctl upgrade database -dbname test_database -sourcewc db18c -destwc db19c
              {authentication_option}

        `test_database` is the name of the database being upgraded.

        `db18c` is the source working copy of the pre-upgrade database.

        `db19c` is the working copy of the upgraded Oracle Database software.
    2.  To upgrade an unmanaged Oracle home (source working copy does not exist because the Oracle home is not managed by Fleet Patching and Provisioning), run:
            $ rhpctl move database -sourcehome /u01/app/orabase/product/18.0.0/dbhome_1
              -destwc db19c -targetnode node1 {authentication_option}

        `/u01/app/orabase/product/18.0.0/dbhome_1` is the path of the database being upgraded.

        `db19c` is the working copy of the upgraded Oracle Database software.

        `targetnode` specifies the node on which the database to be upgraded is running, because the source Oracle Database is on a 18c cluster.

The upgraded database is now managed by Fleet Patching and Provisioning. You can ensure that your database is patched to the latest level, using Fleet Patching and Provisioning.

**Note:**

During upgrade, if an error occurs, the procedure stops and allows you to fix the error. After fixing the error, you can resume the upgrade operation from where it last stopped.

Watch a video

**Related Topics**

- [rhpctl upgrade database](database-commands.md)
- [rhpctl move database](database-commands.md)

**Parent topic:** [Oracle Fleet Patching and Provisioning Use Cases](fleet-patching-provisioning-use-cases.md)
