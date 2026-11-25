Use the Oracle ORAchk and Oracle EXAchk `-fileattr` option and command flags to record and track file attribute settings, and compare snapshots.

Changes to the attributes of files such as owner, group, or permissions can cause unexpected consequences. Proactively monitor and mitigate the issues before your business gets impacted.

- Using the File Attribute Check With the Daemon
  You must have Oracle Grid Infrastructure installed and running before you use `-fileattr`.
- Taking File Attribute Snapshots
  By default, Oracle Grid Infrastructure homes and all the installed Oracle Database homes are included in the snapshots.
- Including Directories to Check
  Include directories in the file attribute changes check.
- Excluding Directories from Checks
  Exclude directories from file attribute changes checks.
- Rechecking Changes
  Compare the new snapshot with the previous one to track changes.
- Designating a Snapshot As a Baseline
  Designate a snapshot as a baseline to compare with other snapshots.
- Restricting System Checks
  Restrict Oracle ORAchk and Oracle EXAchk to perform only file attribute changes checks.
- Removing Snapshots
  Remove the snapshots diligently.

**Parent topic:** [Analyzing Risks and Complying with Best Practices](purpose-oracle-orachk-and-oracle-exachk.md)

### 2.7.1 Using the File Attribute Check With the Daemon

You must have Oracle Grid Infrastructure installed and running before you use `-fileattr`.

#### To use file attribute check with the daemon:

1.  Start the daemon.
        ./orachk -d start
2.  Start the client run with the `-fileattr` options.
        ./orachk -fileattr start -includedir "/root/myapp,/etc/oratab" -excludediscovery
        ./orachk -fileattr check -includedir "/root/myapp,/etc/oratab" -excludediscovery
3.  Specify the output directory to store snapshots with the `–output` option.
        ./orachk -fileattr start -output "/tmp/mysnapshots"
4.  Specify a descriptive name for the snapshot with the `–tag` option to identify your snapshots.
    For example:
        ./orachk -fileattr start -tag "BeforeXYZChange"
          Generated snapshot directory-
          orachk_myserver65_20160329_052056_ BeforeXYZChange

**Parent topic:** Tracking File Attribute Changes and Comparing Snapshots

### 2.7.2 Taking File Attribute Snapshots

By default, Oracle Grid Infrastructure homes and all the installed Oracle Database homes are included in the snapshots.

#### To take file attribute snapshots:

1.  To start the first snapshot, run the `–fileattr start` command.
        ./orachk –fileattr start

        ./exachk –fileattr start

<!-- -->

    $ ./orachk -fileattr start
    CRS stack is running and CRS_HOME is not set. Do you want to set CRS_HOME to /u01/app/11.2.0.4/grid?[y/n][y]
    Checking ssh user equivalency settings on all nodes in cluster
    Node mysrv22 is configured for ssh user equivalency for oradb user
    Node mysrv23 is configured for ssh user equivalency for oradb user

    List of directories(recursive) for checking file attributes:
    /u01/app/oradb/product/11.2.0/dbhome_11202
    /u01/app/oradb/product/11.2.0/dbhome_11203
    /u01/app/oradb/product/11.2.0/dbhome_11204
    orachk has taken snapshot of file attributes for above directories at: /orahome/oradb/orachk/orachk_mysrv21_20160504_041214

**Parent topic:** Tracking File Attribute Changes and Comparing Snapshots

### 2.7.3 Including Directories to Check

Include directories in the file attribute changes check.

#### To include directories to check:

1.  Run the file attribute changes check command with the `–includedir ``directories` option.
    Where, `directories` is a comma-delimited list of directories to include in the check.

    For example:
        ./orachk -fileattr start -includedir "/home/oradb,/etc/oratab"

        ./exachk -fileattr start -includedir "/home/oradb,/etc/oratab"

<!-- -->

    $ ./orachk -fileattr start -includedir "/root/myapp/config/"
    CRS stack is running and CRS_HOME is not set. Do you want to set CRS_HOME to /u01/app/12.2.0/grid?[y/n][y]
    Checking for prompts on myserver18 for oragrid user...
    Checking ssh user equivalency settings on all nodes in cluster
    Node myserver17 is configured for ssh user equivalency for root user
    List of directories(recursive) for checking file attributes:
    /u01/app/12.2.0/grid
    /u01/app/oradb/product/12.2.0/dbhome_1
    /u01/app/oradb2/product/12.2.0/dbhome_1
    /root/myapp/config/
    orachk has taken snapshot of file attributes for above directories at: /root/orachk/orachk_ myserver18_20160511_032034

**Parent topic:** Tracking File Attribute Changes and Comparing Snapshots

### 2.7.4 Excluding Directories from Checks

Exclude directories from file attribute changes checks.

#### To exclude directories from checks:

1.  Run the file attribute changes check command to exclude directories that you do not list in the `-includedir` discover list by using the `-excludediscovery` option.

For example:

    $ ./orachk -fileattr start -includedir "/root/myapp/config/" -excludediscovery
    CRS stack is running and CRS_HOME is not set. Do you want to set CRS_HOME to /u01/app/12.2.0/grid?[y/n][y]
    Checking for prompts on myserver18 for oragrid user...
    Checking ssh user equivalency settings on all nodes in cluster
    Node myserver17 is configured for ssh user equivalency for root user
    List of directories(recursive) for checking file attributes:
    /root/myapp/config/
    orachk has taken snapshot of file attributes for above directories at: /root/orachk/orachk_myserver18_20160511_032209

**Parent topic:** Tracking File Attribute Changes and Comparing Snapshots

### 2.7.5 Rechecking Changes

Compare the new snapshot with the previous one to track changes.

#### To recheck changes:

1.  Run the file attribute changes check command with the `check` option to take a new snapshot, and run a normal health check collection.
    The `–fileattr check` command compares the new snapshot with the previous snapshot.

    For example:
        ./orachk –fileattr check

        ./exachk –fileattr check

    **Note:**

    To obtain an accurate comparison between the snapshots, you must use `–fileattr check` with the same options that you used with the previous snapshot collection that you obtained with `–fileattr start`.

    For example, if you obtained your first snapshot by using the options `-includedir "/somedir" –excludediscovery` when you ran `–fileattr start`, then you must include the same options with `–fileattr check` to obtain an accurate comparison.

<!-- -->

    $ ./orachk -fileattr check -includedir "/root/myapp/config" -excludediscovery
    CRS stack is running and CRS_HOME is not set. Do you want to set CRS_HOME to /u01/app/12.2.0/grid?[y/n][y]
    Checking for prompts on myserver18 for oragrid user...
    Checking ssh user equivalency settings on all nodes in cluster
    Node myserver17 is configured for ssh user equivalency for root user
     List of directories(recursive) for checking file attributes:
    /root/myapp/config
    Checking file attribute changes...
    .
    "/root/myapp/config/myappconfig.xml" is different:
    Baseline :       0644     oracle       root /root/myapp/config/myappconfig.xml
    Current  :       0644       root       root /root/myapp/config/myappconfig.xml
    ...

Results of the file attribute changes are reflected in the File Attribute Changes section of the HTML output report.

**Parent topic:** Tracking File Attribute Changes and Comparing Snapshots

### 2.7.6 Designating a Snapshot As a Baseline

Designate a snapshot as a baseline to compare with other snapshots.

#### To designate a snapshot as a baseline:

1.  Run the file attribute changes check command with the `–baseline ``path_to_snapshot` option.
    The `–baseline ``path_to_snapshot` command compares a specific baseline snapshot with other snapshots, if you have multiple different baselines to check.

        ./orachk -fileattr check -baseline path_to_snapshot

        ./exachk –fileattr check –baseline path_to_snapshot

    For example:
        ./orachk -fileattr check -baseline "/tmp/Snapshot"

**Parent topic:** Tracking File Attribute Changes and Comparing Snapshots

### 2.7.7 Restricting System Checks

Restrict Oracle ORAchk and Oracle EXAchk to perform only file attribute changes checks.

By default, `–fileattr check` also performs a full health check run.

#### To restrict system checks:

1.  Run the file attribute changes check command with the `–fileattronly` option.
        ./orachk -fileattr check –fileattronly

        ./exachk -fileattr check –fileattronly

**Parent topic:** Tracking File Attribute Changes and Comparing Snapshots

### 2.7.8 Removing Snapshots

Remove the snapshots diligently.

#### To remove snapshots:

1.  Run the file attribute changes check command with the `remove` option:
        ./orachk –fileattr remove

        ./exachk –fileattr remove

    For example:
        $ ./orachk -fileattr remove
        CRS stack is running and CRS_HOME is not set. Do you want to set CRS_HOME to /u01/app/12.2.0/grid?[y/n][y]y
        Checking for prompts on myserver18 for oragrid user...
        Checking ssh user equivalency settings on all nodes in cluster
        Node myserver17 is configured for ssh user equivalency for root user

        List of directories(recursive) for checking file attributes:
        /u01/app/12.2.0/grid
        /u01/app/oradb/product/12.2.0/dbhome_1
        /u01/app/oradb2/product/12.2.0/dbhome_1
        Removing file attribute related files...
        ...

**Parent topic:** Tracking File Attribute Changes and Comparing Snapshots
