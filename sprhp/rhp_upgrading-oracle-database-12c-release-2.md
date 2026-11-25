This procedure describes how to upgrade an Oracle database from Oracle Database 11g release 2 (11.2) to 12c release 2 with a single command, using Fleet Patching and Provisioning, both for managed and unmanaged Oracle homes.

### Before you Begin

- To upgrade to Oracle Database 12c release 2 (12.2.0.1), your source database must be either Oracle Database 11g release 2 (11.2.0.3 or 11.2.0.4), or Oracle Database 12c release 1 (12.1.0.2).

- Oracle Grid Infrastructure on which the pre-upgrade database is running must be of the same release or later than the database release to which you are upgrading.

- The source Oracle home to be upgraded can be a managed working copy, that is an Oracle home provisioned using Fleet Patching and Provisioning, or an unmanaged home, that is, an Oracle home not provisioned using Fleet Patching and Provisioning. If you are upgrading an unmanaged Oracle home, provide the complete path of the database for upgrade.

### Procedure to Upgrade Oracle Database using Fleet Patching and Provisioning

1.  From the Fleet Patching and Provisioning Server, run one of the following commands as per your source and destination database:
    1.  To upgrade an Oracle home managed by Fleet Patching and Provisioning, and there exist working copies of the source and destination databases, run:
            $ rhpctl upgrade database -dbname test_database -sourcewc db112 -destwc db122
              {authentication_option}

        `test_database` is the name of the database being upgraded.

        `db112` is the source working copy of the pre-upgrade database.

        `db122` is the working copy of the upgraded Oracle Database software.
    2.  To upgrade an unmanaged Oracle home (source working copy does not exist because the Oracle home is not managed by Fleet Patching and Provisioning), run:
            $ rhpctl move database -sourcehome /u01/app/orabase/product/11.2.0/dbhome_1
              -destwc db122 -targetnode node1 {authentication_option}

        `/u01/app/orabase/product/11.2.0/dbhome_1` is the path of the database being upgraded.

        `db122` is the working copy of the upgraded Oracle Database software.

        `targetnode` specifies the node on which the database to be upgraded is running, because the source Oracle Database is on a 11.2.0.4 cluster.

The upgraded database is now managed by Fleet Patching and Provisioning. You can ensure that your database is patched to the latest level, using Fleet Patching and Provisioning.

**Note:**

During upgrade, if an error occurs, the procedure stops and allows you to fix the error. After fixing the error, you can resume the upgrade operation from where it last stopped.

Watch a video

**Parent topic:** [Fleet Patching and Provisioning Use Cases](fleet-patching-and-provisioning-use-cases.md)
