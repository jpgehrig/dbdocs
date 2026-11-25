## How to Override Default Fixups

You can use the `RUNFIX` column entry to disable automated fixups, except in cases where disabling the fixup violates security or Oracle policy.

The default fixups that are part of the AutoUpgrade procedure are generated during the Analyze processing mode stage. You can modify the generated fixups list to disable automatic fixups, so that you can run your own fixups.

The sequence of steps is as follows:

1.  Run the AutoUpgrade utility in Analyze mode
2.  Open and edit the `sid``_checklist.cfg` file that is generated during Analyze mode, so that the fixups you want to do manually are disabled from running automatically.
3.  In your most recent AutoUpgrade configuration file, under your local parameters list for the job on which you want to suppress the automatic fixup, find the parameter `sid``.checklist`, where `sid` is the system identifier (SID) of the database on which you want to suppress an automatic fixup. By default, AutoUpgrade uses the most recent generated file. If you want to point it to a different configuration file, then edit the parameter to provide a path to the `checklist.cfg` file that you have edited.

**Note:**

AutoUpgrade resume always uses the most recent `sid``_checklist.config` file.

For example, if you have two generated AutoUpgrade configuration files, `/logdir/100/``sid``_checklist.cfg`, and `/logdir/101/sid_checklist.cfg`, then you must either specify a direct path to the configuration file that you want to use, or edit the most recent file, which in this case is the `sid``_checklist.cfg` file in `/logdir/101/`

Suppose you have corrected an issue manually that you found, and want to have AutoUpgrade to use a fixup file with different checks. If you want to direct AutoUpgrade to use a different file, then you can specify the file path directly in the `checklist.cfg` file by using the `prefix``.checklist` parameter, where `prefix` is the identifier for the database. For example: `prefix.checklist=logdir/repress-standard/sid_checklist.cfg`

If the AutoUpgrade utility finds an error level database condition, and there is not a fixup available for it, or you have manually disabled the available fixup, then the AutoUpgrade job that contains the database with the error condition stops.

Use the examples that follow to assist you with this procedure.

Example 3-27 Starting Up the AutoUpgrade Utility in Analyze Mode

    java -jar autoupgrade.jar -config config.cfg –mode analyze

Example 3-28 Creating a New Checklist for a Configuration File

In this scenario, you are running AutoUpgrade checks on an Oracle Database 11g Release 2 (11.2) database home, in preparation for an upgrade to Oracle Database 18c, with release update 8. You start with the following configuration file, called `config.cfg`:

    global.autoupg_log_dir=/home/oracle/autoupg
    upg1.sid=db11204
    upg1.source_home=/databases/ee/product/11.2.0/dbhome_1
    upg1.target_home=/databases/ee/product/18x/dbhome_1
    upg1.target_base=/databases
    upg1.target_version=18.8.0

You then complete the following steps:

1.  Run the command `java -jar autoupgrade.jar -config config.cfg -mode analyze`

    The command produces a checklist file in the following path:

        /home/oracle/autoupg/db11204/100/prechecks/db11204_checklist.cfg

2.  Move the checklist file to another location. For example:

        oracle@example: $ cd $PRECHECKS
        oracle@example: $ pwd
        /home/oracle/autoupg/db11204/100/prechecks
        oracle@example: $ mv ./db11204_checklist.cfg /tmp

3.  Use a text editor to open up the file, and look for the checks `AMD_EXISTS` and` EM_PRESENT`.

    For example:


        [SID] [db11204]
        ==========================================
        [container] [db11204]
        ==========================================
        [checkname] AMD_EXISTS
        [stage] PRECHECKS
        [fixup_available] YES
        [runfix] YES
        [severity] WARNING
        ----------------------------------------------------
        [checkname] DICTIONARY_STATS
        [stage] PRECHECKS
        [fixup_available] YES
        [runfix] YES
        [severity] RECOMMEND
        ----------------------------------------------------
        [checkname] EM_PRESENT
        [stage] PRECHECKS
        [fixup_available] YES
        [runfix] YES
        [severity] WARNING
        ----------------------------------------------------
        ...
        [truncated]

4.  Change the values for checks `AMD_EXISTS` and` EM_PRESENT` from `yes` to `no`.

    For example

        [SID] [db11204]
        ==========================================
        [container] [db11204]
        ==========================================
        [checkname] AMD_EXISTS
        [stage] PRECHECKS
        [fixup_available] YES
        [runfix] NO
        [severity] WARNING
        ----------------------------------------------------
        [checkname] DICTIONARY_STATS
        [stage] PRECHECKS
        [fixup_available] YES
        [runfix] YES
        [severity] RECOMMEND
        ----------------------------------------------------
        [checkname] EM_PRESENT
        [stage] PRECHECKS
        [fixup_available] YES
        [runfix] NO
        [severity] WARNING
        ----------------------------------------------------
        ...
        [truncated]

    Notice that with both parameters, the `fixup_available` value is `YES`. That means that there is a fixup available, which you choose not to run. If no fixup is available, then the value for `runfix `is `N/A`.

5.  Change the location where AutoUpgrade looks for the configuration file by updating the path for the parameter checklist. To do this, add an entry to the configuration file with the checklist pointer to the directory where your edited file resides. For example:

        global.autoupg_log_dir=/home/oracle/autoupg
        upg1.sid=db11204
        upg1.source_home=/databases/ee/product/11.2.0/dbhome_1
        upg1.target_home=/databases/ee/product/18x/dbhome_1
        upg1.target_base=/databases
        upg1.target_version=18.8.0
        upg1.checklist=/home/oracle/db11204_checklist.cfg

6.  Run the fixups using the configuration file that you have edited and moved. For example:

        java -jar autoupgrade.jar -config config.cfg -mode fixups

    Autoupgrade uses the configuration file in /home/oracle to run the AutoUpgrade utility.

Example 3-29 Find and Edit `checklist.cfg`

The Analyze mode generates a fixup file with the file name `checklist.cfg`. Navigate to the file, where `DATABASE_LOGS_DIR` is the value set for the AutoUpgrade `log_dir` parameter of the database, `job-id` refers to the job identifier that the AutoUpgrade utility generates, and `sid` is the system identifier for the database on which you want to suppress automatic fixups:

    DATABASE_LOGS_DIR/job-id/prechecks/sid_checklist.cfg

Open the `checklist.cfg` file with a text editor. The following is an example of the `checklist.cfg` file for the database with the SID `DB11204`:

    [dbname]          [DB11204]
    ==========================================
    [container]          [DB11204]
    ==========================================
    [checkname]          AMD_EXISTS
    [stage]              PRECHECKS
    [fixup_available]    YES
    [runfix]             YES
    [severity]           WARNING
    ----------------------------------------------------

    [checkname]          DEPEND_USR_TABLES
    [stage]              POSTCHECKS
    [fixup_available]    YES
    [runfix]             YES
    [severity]           WARNING
    ----------------------------------------------------

    [checkname]          DICTIONARY_STATS
    [stage]              PRECHECKS
    [fixup_available]    YES
    [runfix]             YES
    [severity]           RECOMMEND
    ----------------------------------------------------

    [checkname]          EM_PRESENT
    [stage]              PRECHECKS
    [fixup_available]    YES
    [runfix]             YES
    [severity]           WARNING
    ----------------------------------------------------
    .
    .
    .

The file has a hierarchical structure. It starts with the database name, and the container name for which the entries of the `checklist.cfg` apply. The file contains a series of fixup checks that are applied automatically. For each entry, there are 5 relevant values parameters:

| Parameter           | Description                                                                                                                                                |
|:--------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| `[checkname]`       | Name of the database check                                                                                                                                 |
| `[stage]`           | AutoUpgrade stage in which the check is performed. It can be either prechecks, or post checks.                                                             |
| `[fixup available]` | Availability of an automatic fixup. This parameter value is either `YES` (an automatic fixup is available), or `NO` (an automatic fixup is not available). |
| `runfix`            | Run status for the fixup. This parameter takes one of two values:<br>`YES`: Run the fixup.<br>`NO`: Do not run the fixup.                                  |
| `severity`          | Class of severity of the issue that the automatic fixup addresses.                                                                                         |

For each fixup that you want to perform manually, change the `[runfix]` parameter value from `YES `to `NO`.

**Related Topics**

- [My Oracle Support Doc ID 2380601.1 "Database Preupgrade tool check list"](https://support.oracle.com/rs?type=2380601.1)

**Parent topic:** [Using AutoUpgrade for Oracle Database Upgrades](using-autoupgrade-oracle-database-upgrades.md)
