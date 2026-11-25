## Preparing the New Oracle Home for Upgrading

To prepare the new Oracle home in a new location, check to see if you must move configuration files, or complete other tasks.

After backing up the database that you want to upgrade, if you are not using a Read-Only Oracle home, then prepare the new Oracle home in a new location, and install the software for the new Oracle Database release into the new location.

1.  (Manual upgrades only) Copy configuration files from the Oracle home of the database being upgraded (source) to the new release Oracle Database Oracle home (target). If you are using the AutoUpgrade utility, or DBUA, or a Read-Only Oracle home, then you can ignore this step, because the configuration files are copied for you automatically.

    Use the following procedure to copy configuration files to the new Oracle home:

    1.  If your parameter file resides within the old environment Oracle home, then copy it to the new Oracle home. By default, Oracle looks for the parameter file in the `ORACLE_HOME``/dbs` directory on Linux or Unix platforms and in the `ORACLE_HOME``\database` directory on Windows operating systems. After upgrade, the parameter file can reside anywhere else, but it cannot reside in the Oracle home of the old environment.

        **Note:**

        If necessary, create a text initialization parameter file (`PFILE`) from the server parameter file (`SPFILE`) so that you can edit the initialization parameters.

    2.  If your parameter file resides within an Oracle ASM instance, then back up the parameter file using one of the following commands:

            CREATE pfile FROM spfile;

        You can also create the parameter file by using the following command, where `/path/to/pfile/` is the path to the new Oracle home, and `pfile_name` is the name of the parameter file:

            create pfile[='/path/to/pfile/pfile_name.ora/

        If you must downgrade the database and your `SPFILE` resided within Oracle ASM, then you must restore the parameter file before the downgrade.

    3.  If your parameter file is a text-based initialization parameter file with either an `IFILE` (include file) or a `SPFILE` (server parameter file) entry, and the file specified in the `IFILE` or `SPFILE` entry resides within the earlier release environment Oracle home, then copy the file specified by the `IFILE` or `SPFILE` entry to the new Oracle home. The file specified in the `IFILE` or `SPFILE` entry contains additional initialization parameters.

    4.  If you have a password file that resides within the old environment Oracle home, then move or copy the password file to the new Oracle home.

        The name and location of the password file are operating system-specific. Where `SID` is your Oracle instance ID, you can find the password file in the following locations:

        - Linux or Unix platforms: The default password file is `orapw ``SID`. It is located in the directory `ORACLE_HOME``/dbs`.

        - Microsoft Windows operating systems: The default password file is `pwd``SID``.ora`. It is located in the directory `ORACLE_HOME``\database`.

2.  Adjust your parameter file in the new Oracle Database release by completing the following steps:

    1.  Remove desupported initialization parameters and adjust deprecated initialization parameters. In new releases, some parameters are desupported, and other parameters are deprecated. Remove all desupported parameters from any parameter file that starts the new Oracle Database instance. Desupported parameters can cause errors in new Oracle Database releases. Also, alter any parameter whose syntax has changed in the new release.

        AutoUpgrade run with the `-preupgrade` parameter in `analyze` mode displays any deprecated parameters and desupported parameters it finds in the `upgrade.xml` file that it generates.

        Adjust the values of the initialization parameters to at least the minimum values indicated in `upgrade.xml`

        Ensure all path names in the parameter file are fully specified. You should not have relative path names in the parameter file.

    2.  If the parameter file contains an `IFILE` entry, then change the `IFILE` entry in the parameter file. The `IFILE` entry should point to the new location text initialization parameter file that you specified in step 1. Also edit the file specified in the `IFILE` entry in the same way that you edited the parameter file in step 1.

    3.  If you are upgrading a cluster database, then if necessary, you can modify the `SPFILE` or `init``ORACLE_SID``.ora` files.

    After making these parameter file adjustments, make sure that you save all of the files that you modified.

3.  (Manual upgrades only) If you are upgrading a cluster database, and you are not using AutoUpgrade or Replay Upgrade, then you must manually separate the database instance from the cluster. Set the CLUSTER_DATABASE initialization parameter to `false`. After the upgrade, you must set this initialization parameter back to `true`. If you are using DBUA, then the assistant takes care of this task for you.

**Parent topic:** [Preparing to Upgrade Oracle Database](tasks-prepare-upgrade-oracle-database.md)
