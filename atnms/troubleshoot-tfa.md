This section helps you diagnose and remediate Oracle Trace File Analyzer issues.

- Cluster Nodes are Not Showing As One Cluster When Viewed by Running the tfactl status Command
- Oracle Trace File Analyzer is Not Starting and the init.tfa script is Missing After Reboot
- Error Message Similar to "Can't locate \*\*\*\* in @inc (@inc contains:....)"
- Non-Release Update Revisions (RURs) Oracle Trace File Analyzer Patching Fails on Remote Nodes
- Non-Root Access is Not Enabled After Installation
- TFA_HOME and Repository Locations are Moved After Patching or Upgrade
- Oracle Trace File Analyzer Fails with TFA-00103 After Applying the July 2015 Release Update Revision (RUR) or Later
- OSWatcher Parameters are Different After a Reboot or Otherwise Unexpectedly Different
- Oracle Trace File Analyzer Installation or Oracle Trace File Analyzer Discovery (tfactl rediscover) Fails on Linux 7
- OSWatcher Analyzer Fails When OSWatcher is Not Running from the TFA_HOME
- Oracle Trace File Analyzer Fails to Start with com.sleepycat.je.EnvironmentLockedException Java Exception
- Oracle Trace File Analyzer Startup Fails When Solution-Soft Time Machine Software is Installed, but Not Running on the System
- Non-privileged User is Not Able to Run tfactl Commands?
- Oracle Trace File Analyzer Daemon is Not Starting or Not Running?

**Parent topic:** [Collecting Diagnostic Data and Triaging, Diagnosing, and Resolving Issues](diagnose-troubleshoot-issues-errors.md)

### 21.1 Cluster Nodes are Not Showing As One Cluster When Viewed by Running the tfactl status Command

Cause: Certificates are not synchronized.

Action: Manually synchronize the keys.

Go to any one of the cluster nodes and run the `synctfanodes.sh` script as `root`.

    # $GIHOME/tfa/nodename/tfa_home/bin/synctfanodes.sh

**Note:**

The script uses SSH and SCP. If passwordless SSH is not set for `root`, then Oracle Trace File Analyzer prompts you 3 times per node for password each time a command is run.

If the Expect utility is available on the node, then Oracle Trace File Analyzer uses Expect thus reducing the number of prompts for password.

**Parent topic:** Troubleshooting Oracle Trace File Analyzer

### 21.2 Oracle Trace File Analyzer is Not Starting and the init.tfa script is Missing After Reboot

Description: The file system housing `TFA_HOME` with Oracle Trace File Analyzer binaries was not mounted when `init.tfa` was run from `init` or `System D` on Linux 6 and above.

Cause: There are many reasons and not restricted to the following:

- Mounting the file system was disabled for maintenance or patching

- Problems or errors related to the file system

- NFS inaccessible network

- File system with `TFA_HOME` is mounting slowly

Action: Refer to My Oracle Support note 2224163.1 to fix this issue.

**Related Topics**

- [https://support.oracle.com/rs?type=doc&amp;id=2224163.1](https://support.oracle.com/rs?type=doc&amp;amp;id=2224163.1)

**Parent topic:** Troubleshooting Oracle Trace File Analyzer

### 21.3 Error Message Similar to "Can't locate \*\*\*\* in @inc (@inc contains:....)"

Cause: Using an old version of Perl causes this error.

Action: Oracle Trace File Analyzer requires Perl version 5.10 or above. If you encounter similar errors, then upgrade Perl to version 5.10 or above.

After installing, update the location of Perl in the `tfa_home/tfa_setup.txt` file to point to the new location:

    PERL=/u01/perl/bin/perl

If the problem occurs during install, then use the `-perlhome ``dir`` ` install option.

The directory you specify must contain `/bin/perl`. If you install Perl as `root`, then `root` must own the Perl executable.

    # which perl
    /usr/bin/perl

    # ./installTFA-LINUX -perlhome /usr

**Parent topic:** Troubleshooting Oracle Trace File Analyzer

### 21.4 Non-Release Update Revisions (RURs) Oracle Trace File Analyzer Patching Fails on Remote Nodes

Cause: Remote nodes fail to upgrade due to a socket issue when upgrading Oracle Trace File Analyzer through Oracle Trace File Analyzer sockets.

Description: After completing the upgrade, crosscheck the report if all nodes are at the same version, build id, and status.

    .-------------------------------------------------------------.
    | Host  | TFA Version | TFA Build ID         | Upgrade Status |
    +-------+-------------+----------------------+----------------+
    | node1 | 12.1.2.6.0  | 12126020151019114604 | UPGRADED       |
    | node2 | 12.1.2.6.0  | 12126020151019114604 | UPGRADED       |
    '-------+-------------+----------------------+----------------'

If you see any differences as follows, then you must fix the issue.

    .--------------------------------------------------------------.
    | Host  | TFA Version | TFA Build ID          | Upgrade Status |
    +-------+-------------+-----------------------+----------------+
    | node1 | 12.1.2.6.0  | 12126020151019114604  | UPGRADED       |
    | node2 | 12.1.2.3.0  | 12120020140619094932  | NOT UPGRADED   |
    '-------+-------------+-----------------------+----------------'

Action: Copy the Oracle Trace File Analyzer installer to all nodes that failed to upgrade and run the installer locally on those nodes.

    ./installTFALite –local

After upgrading the binaries, replace the root SSL certificates from the node that initiated upgrade.

Copy the following files from the existing configuration node to the node to be added. Change the permission for those files to `700` for `root` on the machine to be added.

    tfa_home/server.jks
    tfa_home/client.jks
    tfa_home/internal/ssl.properties

**Parent topic:** Troubleshooting Oracle Trace File Analyzer

### 21.5 Non-Root Access is Not Enabled After Installation

Description: Non-root access for the Oracle Grid Infrastructure software owner must be activated by default when non-root access is enabled.

Action: To enable non-root access to Oracle Trace File Analyzer, run the `tfactl access add -user` command as `root`.

For example:

    tfactl access add -user xyx

Running command enables the non-root user group xyz to access Oracle Trace File Analyzer.

**Parent topic:** Troubleshooting Oracle Trace File Analyzer

### 21.6 TFA_HOME and Repository Locations are Moved After Patching or Upgrade

Description: Before Oracle Trace File Analyzer version 12.1.2.6.0, when an existing free standing Oracle Trace File Analyzer was installed (MOS version installed outside the `GRID_HOME`) and Oracle Trace File Analyzer is then patched with Oracle Grid Infrastructure as part of Oracle 12.1.0.2, then `TFA_HOME` is moved into the `GRID_HOME` and the repository directory is moved to the Oracle Grid Infrastructure owners `ORACLE_BASE` directory.

If the repository directory is changed to a non-default location, then the change is lost.

- To set the Oracle Trace File Analyzer zip file repository location to the required base directory, run the `tfactl set repositorydir` command.

- To change the maximum size of the Oracle Trace File Analyzer repository, run the `tfactl set reposizeMB` command.

Starting with Oracle Trace File Analyzer version 12.1.2.6.0 and above, if `TFA_HOME` exists outside the `GRID_HOME`, then Oracle Trace File Analyzer installation is moved as part of Release Update Revision (RUR) installation. However, if the Release Update Revision (RUR) has a newer version of Oracle Trace File Analyzer, then Oracle Trace File Analyzer is upgraded in its current location.

If Oracle Trace File Analyzer is installed in the `GRID_HOME` and the `GRID_HOME` is moved as part of any patching, then the existing `TFA_HOME` is migrated to the new `GRID_HOME` and upgraded as required.

**Parent topic:** Troubleshooting Oracle Trace File Analyzer

### 21.7 Oracle Trace File Analyzer Fails with TFA-00103 After Applying the July 2015 Release Update Revision (RUR) or Later

- Phase 1 of Oracle Trace File Analyzer upgrade

- Phase 2 of Oracle Trace File Analyzer upgrade

- How can I verify that both phases have been completed and that Oracle Trace File Analyzer communication among all the nodes has been established?

- What if I do not upgrade all my nodes at the same time by choice or if some are down for maintenance?

- I know that not all nodes are upgraded at the same time. I do not want to wait 24 hours for Oracle Trace File Analyzer to sync the key files. What do I do?

#### Phase 1 of Oracle Trace File Analyzer upgrade

Oracle Trace File Analyzer communication model has been changed in versions greater than 12.1.2.4.1. To avoid communication problems, Oracle Trace File Analyzer communication change must be complete across all nodes of the Oracle Trace File Analyzer configuration. Oracle Trace File Analyzer is upgraded on each node locally as part of application of Release Update Revision (RUR). The Release Update Revision (RUR) process applies the new software and restarts Oracle Trace File Analyzer, but does not put in place the new connection model.

#### Phase 2 of Oracle Trace File Analyzer upgrade

Before automatically implementing the new communication model, Oracle Trace File Analyzer waits for 24 hours to complete the application of Release Update Revision (RUR) on all nodes. Once Oracle Trace File Analyzer is upgraded on all the nodes, phase 2 must occur within 10 minutes. The new Oracle Trace File Analyzer communication model is not implemented (phase 2) until Release Update Revision (RUR) is applied on all nodes (phase 1).

Oracle Trace File Analyzer indicates by displaying the message:

    TFA-00103 - TFA is not yet secured to run all commands.

Once Oracle Trace File Analyzer is upgraded on all nodes in the configuration (phase 1), Oracle Trace File Analyzer:

- Generates new SSL keys

- Sends the keys to the valid nodes in the cluster

- Restart Oracle Trace File Analyzer on each of these nodes (phase 2)

On completion of phase 2, Oracle Trace File Analyzer must process commands normally using the new communication model.

#### How can I verify that both phases have been completed and that Oracle Trace File Analyzer communication among all the nodes has been established?

First, as `root` run:

     tfactl print status

    .--------------------------------------------------------------------------------.
    | Host   | Status  | PID   | Port |   Version  |      Build ID        | Inventory|
    +--------+---------+-------+------+------------+----------------------+----------+
    | sales1 | RUNNING | 4390  | 5000 | 12.1.2.4.2 | 12124220150629072212 | COMPLETE |
    | sales2 | RUNNING | 23604 | 5000 | 12.1.2.4.2 | 12124220150629072212 | COMPLETE |
    | sales3 | RUNNING | 28653 | 5000 | 12.1.2.4.2 | 12124220150629072212 | COMPLETE |
    | sales4 | RUNNING | 5989  | 5000 | 12.1.2.4.2 | 12124220150629072212 | COMPLETE |
    '--------+---------+-------+------+------------+----------------------+----------'

Once all nodes are shown to be at the same version and build ID then within about 10 minutes maximum the synchronization of keys must complete.

Ensure that you run the following command:

    tfactl print directories

Running `tfactl print directories` must return the list of directories registered in Oracle Trace File Analyzer. If the communication is not established among all the nodes, then the command returns the message, `TFA is not yet secured to run all commands`.

The message also indicates that phase 2 has not been completed. To verify on which nodes phase 2 has not yet been completed, on each node, check the existence of the following files. The files must be readable only by `root`, `ownership:group` of `root`. The checksum for each file must match on all nodes.

    # ls -al /u01/app/12.1.0/grid/tfa/sales1/tfa_home/client.jks

    -rwx------   1 root  root   3199 Jun 30 14:12 /u01/app/12.1.0/grid/tfa/sales1/tfa_home/client.jks

    # ls -al /u01/app/12.1.0/grid/tfa/sales1/tfa_home/server.jks

    -rwx------   1 root  root   3201 Jun 30 14:12 /u01/app/12.1.0/grid/tfa/sales1/tfa_home/server.jks

    # ls -al /u01/app/12.1.0/grid/tfa/sales1/tfa_home/internal/ssl.properties

    -rwx------   1 root  root   220 Jun 30 14:12 /u01/app/12.1.0/grid/tfa/sales1/tfa_home/internal/ssl.properties

#### What if I do not upgrade all my nodes at the same time by choice or if some are down for maintenance?

Oracle Trace File Analyzer waits to complete the phase 2 operations until all nodes have completed upgrade or until 24 hours has passed.

After 24 hours, Oracle Trace File Analyzer:

- Generates new keys

- Copies the key to all the nodes that have been upgraded

- Restarts Oracle Trace File Analyzer on those nodes

Any nodes that did not get the keys are outside of the Oracle Trace File Analyzer configuration. After upgrading Oracle Trace File Analyzer, manually synchronize the keys with other nodes.

If the application of Release Update Revision (RUR) on all the nodes is completed within 24 hours, then manually synchronize the keys.

To manually synchronize the keys, go to one node that has completed Phase 2 and run the `synctfanodes.sh` script as `root`.

    # $GIHOME/tfa/nodename/tfa_home/bin/synctfanodes.sh

**Note:**

The script uses SSH and SCP. If `root` does not have passwordless SSH, then Oracle Trace File Analyzer prompts you 3 time per node for password each time a command is run.

If the Expect utility is available on the node, then Oracle Trace File Analyzer uses Expect thus reducing the number of prompts for password.

The script displays all the nodes in Oracle Trace File Analyzer configuration, including the nodes where Oracle Trace File Analyzer is yet to upgrade.

The script also shows the nodes that are part of the Oracle Grid Infrastructure configuration.

Verify the node list provided and supply a space-separated list of nodes to synchronize. It doesn't hurt to include the nodes that were previously upgraded as the process is idempotent.

For example:

Nodes sales1, sales2, sales3, and sales4 are all part of Oracle Grid Infrastructure. The nodes were running Oracle Trace File Analyzer 12.1.2.0.0 until the July 2015 Release Update Revision (RUR) was applied.

The Release Update Revision (RUR) was applied initially only to sales1 and sales3 due to outage restrictions.

After completion of phase 1 of the Oracle Trace File Analyzer upgrade, run `print status`. Running the command lists all nodes even though different versions of Oracle Trace File Analyzer are running on some of the nodes.

    -bash-3.2# /u01/app/12.1.0/grid/bin/tfactl print status
    .--------------------------------------------------------------------------------.
    | Host   | Status  | PID   | Port |   Version  |       Build ID       |Inventory |
    +--------+---------+------ +------+------------+----------------------+----------+
    | sales1 | RUNNING | 27270 | 5000 | 12.1.2.4.2 | 12124220150629072212 | COMPLETE |
    | sales3 | RUNNING | 19222 | 5000 | 12.1.2.4.2 | 12124220150629072212 | COMPLETE |
    | sales2 | RUNNING | 10141 | 5000 | 12.1.2.0.0 | 12120020140619094932 | COMPLETE |
    | sales4 | RUNNING | 17725 | 5000 | 12.1.2.0.0 | 12120020140619094932 | COMPLETE |
    '--------+---------+-------+------+------------+----------------------+----------'

Since the new Oracle Trace File Analyzer communication model is not set up among all the nodes, many commands when run as `root` fail with the message:

    TFA is not yet secured to run all commands.

Failed attempts to run `tfactl` commands as a non-root indicates that there is no sufficient permission to use Oracle Trace File Analyzer.

After 24 hours, Oracle Trace File Analyzer completes phase 2 for sales1 and sales3. Oracle Trace File Analyzer communication model is established for sales1 and sales3. You can perform normal Oracle Trace File Analyzer operations on sales1 and sales3. Communication with sales2 and sales4 has not yet been established and so running remote commands to them fail.

When running `print status` on sales1 and sales3, we no longer see sales2 and sales4. Only Oracle Trace File Analyzer using the new Oracle Trace File Analyzer communication model communicates.

    -bash-3.2# /u01/app/12.1.0/grid/bin/tfactl print status

    .--------------------------------------------------------------------------------.
    | Host   | Status  | PID   | Port |   Version  |     Build ID         |Inventory |
    +--------+---------+-------+------+------------+----------------------+----------+
    | sales1 | RUNNING | 4390  | 5000 | 12.1.2.4.2 | 12124220150629072212 | COMPLETE |
    | sales3 | RUNNING | 23604 | 5000 | 12.1.2.4.2 | 12124220150629072212 | COMPLETE |
    '--------+---------+-------+------+------------+----------------------+----------'

Running the command `tfactl diagcollect` collects from sales1 and sales3 but not from the other nodes.

    -bash-3.2$ /u01/app/12.1.0/grid/bin/tfactl diagcollect
    Collecting data for the last 4 hours for this component...
    Collecting data for all nodes

    Repository Location in sales1 : /u01/app/oragrid/tfa/repository
    2015/06/30 05:25:27 PDT : Collection Name : tfa_Tue_Jun_30_05_25_20_PDT_2015.zip
    2015/06/30 05:25:27 PDT : Sending diagcollect request to host : sales2
    2015/06/30 05:25:27 PDT : Sending diagcollect request to host : sales3
    2015/06/30 05:25:27 PDT : Sending diagcollect request to host : sales4
    2015/06/30 05:25:27 PDT : Scanning of files for Collection in progress...
    ....
    ....
    ....
    2015/06/30 05:25:37 PDT : Remote Collection in Progress...
    2015/06/30 05:25:57 PDT : sales3:Completed Collection
    2015/06/30 05:26:07 PDT : sales2:Failed Unable to connect to Node sales2
    2015/06/30 05:26:07 PDT : sales4:Failed Unable to connect to Node sales4
    2015/06/30 05:26:07 PDT : Completed collection of zip files.

While upgrading on the remaining nodes, Oracle Trace File Analyzer cannot see the nodes already upgraded until the configuration is synchronized.

    bash-3.2# /u01/app/12.1.0/grid/bin/tfactl print status

    .------------------------------------------------------------------------------.
    | Host   | Status  | PID | Port | Version    |     Build ID         | Inventory|
    +--------+---------+-----+------+------------+----------------------+----------+
    | sales3 | RUNNING | 9   | 5000 | 12.1.2.4.2 | 12124220150629072212 | COMPLETE |
    '--------+---------+-----+------+------------+----------------------+----------'

For nodes, on which the application of Release Update Revision (RUR) was not completed within the 24 hour waiting period to become part of Oracle Trace File Analyzer configuration:

1.  Run the synchronize script from a node that has the keys already generated

2.  Manually copy the SSL configuration to those nodes

In our example from sales1:

    /u01/app/12.1.0/grid/tfa/sales1/tfa_home/bin/synctfanodes.sh
    Current Node List in TFA :
    sales1
    sales2
    sales3
    sales4

    Node List in Cluster :
    sales1 sales2 sales3 sales4

    Node List to sync TFA Certificates :
    1 sales2
    2 sales3
    3 sales4

    Do you want to update this node list? [Y|N] [N]: Y

    Please Enter all the nodes you want to sync...

    Enter Node List (seperated by space) : sales2 sales4

    Syncing TFA Certificates on sales2 :

    TFA_HOME on sales2 : /u01/app/12.1.0/grid/tfa/sales2/tfa_home

    Copying TFA Certificates to sales2...
    Copying SSL Properties to sales2...
    Shutting down TFA on sales2...
    Sleeping for 5 seconds...
    Starting TFA on sales2...

    Syncing TFA Certificates on sales4 :

    TFA_HOME on sales4 : /u01/app/12.1.0/grid/tfa/sales4/tfa_home

    Copying TFA Certificates to sales4...
    Copying SSL Properties to sales4...
    Shutting down TFA on sales4...
    Sleeping for 5 seconds...
    Starting TFA on sales4...

    Successfully re-started TFA..

    .--------------------------------------------------------------------------------.
    | Host   | Status  | PID   | Port |   Version  |      Build ID        | Inventory|
    +--------+---------+-------+------+------------+----------------------+----------+
    | sales1 | RUNNING | 4390  | 5000 | 12.1.2.4.2 | 12124220150629072212 | COMPLETE |
    | sales2 | RUNNING | 23604 | 5000 | 12.1.2.4.2 | 12124220150629072212 | COMPLETE |
    | sales3 | RUNNING | 28653 | 5000 | 12.1.2.4.2 | 12124220150629072212 | COMPLETE |
    | sales4 | RUNNING | 5989  | 5000 | 12.1.2.4.2 | 12124220150629072212 | COMPLETE |
    '--------+---------+-------+------+------------+----------------------+----------'

**Note:**

The node list was changed to only the nodes that needed the keys synchronized, sales2 and sales4.

In this case, it’s fine to synchronize sales3 as it would have received the same files and restart Oracle Trace File Analyzer.

#### I know that not all nodes are upgraded at the same time. I do not want to wait 24 hours for Oracle Trace File Analyzer to sync the key files. What do I do?

Use the synchronize script to force Oracle Trace File Analyzer to generate and synchronize certificates. While running, the script prompts if you wish to generate SSL configuration files and then synchronizes them to the remote nodes.

For example:

    -bash-3.2# /u01/app/12.1.0/grid/tfa/sales1/tfa_home/bin/synctfanodes.sh

    Current Node List in TFA :
    sales1
    sales2
    sales3
    sales4

    TFA has not yet generated any certificates on this Node.

    Do you want to generate new certificates to synchronize across the nodes? [Y|N] [Y]:

    Generating new TFA Certificates...

    Restarting TFA on sales1...
    Shutting down TFA
    TFA-00002 : Oracle Trace File Analyzer (TFA) is not running
    TFA Stopped Successfully
    . . . . .
    . . .
    Successfully shutdown TFA..
    Starting TFA..
    Waiting up to 100 seconds for TFA to be started..
    . . . . .
    . . . . .
    Successfully started TFA Process..
    . . . . .
    TFA Started and listening for commands

    Node List in Cluster :
    sales1 sales2 sales3 sales4

    Node List to sync TFA Certificates :
    1 sales2
    2 sales3
    3 sales4

    Do you want to update this node list? [Y|N] [N]:

After the key files are generated and synchronized, on each node you must find the files as follows:

    # ls -al /u01/app/12.1.0/grid/tfa/sales1/tfa_home/client.jks

    -rwx------   1 root     root    3199 Jun 30 14:12 /u01/app/12.1.0/grid/tfa/sales1/tfa_home/client.jks

    # ls -al /u01/app/12.1.0/grid/tfa/sales1/tfa_home/server.jks

    -rwx------   1 root     root    3201 Jun 30 14:12 /u01/app/12.1.0/grid/tfa/sales1/tfa_home/server.jks

    # ls -al /u01/app/12.1.0/grid/tfa/sales1/tfa_home/internal/ssl.properties

    -rwx------   1 root     root    220 Jun 30 14:12 /u01/app/12.1.0/grid/tfa/sales1/tfa_home/internal/ssl.properties

Readable only by `root`, `ownership:group` of `root`. The checksum for each file must match on all nodes.

**Parent topic:** Troubleshooting Oracle Trace File Analyzer

### 21.8 OSWatcher Parameters are Different After a Reboot or Otherwise Unexpectedly Different

When Oracle Trace File Analyzer manages OSWatcher, after an install or a reboot, OSWatcher is started as a non-privileged user such as:

- `grid` on Oracle RAC systems

- `oracle` on non-Oracle RAC systems

Oracle does not recommend stopping and restarting OSWatcher as `root`.

For example:

    tfactl oswbb stop

    tfactl start oswbb 20 72 (interval of 20 seconds and retention of 72 hours)

OSWatcher is then run as `root` until it is stopped and re-started as `oracle` or `grid`, or there is a reboot. In either case, the parameters are persisted in a property file. OSWatcher defaults (30,48) are used unless other parameters are specified for interval and retention period. Beginning with Oracle Trace File Analyzer version 12.1.2.5.2, an OSWatcher property file is maintained for each user. Each time OSWatcher is started, the parameters for interval or retention hours are made persistent for that user. In earlier versions, if the OSWatcher startup parameters are different than expected, then it is because OSWatcher was stopped and started as `root` with different parameters. These settings would have persisted across reboots because there was only one properties file.

In 12.1.2.5.2 and above, if there is a reboot, then OSWatcher must always be brought up using the parameters from the properties of `oracle` or `grid`. The OSWatcher startup parameters are different if OSWatcher is stopped and re-started as `root` with different parameters before a reboot. The parameters fetched from the `root` properties must not take effect after a reboot. The parameters must revert to the parameters of `oracle` properties.

The parameters are different and the persistent settings are changed because Oracle Support would have recommended different settings to investigate an issue. In that case, stop, and re-start OSWatcher with the normal parameters as a non-privileged user.

    tfactl oswbb stop

    tfactl start oswbb (in this case the default interval of 30 seconds and retention of 48 hours would be persisted)

**Note:**

If OSWatcher is installed and running, and not managed by Oracle Trace File Analyzer, then Oracle Trace File Analyzer defers to that installation and parameters. When listing the `oswbb` tool status, the status must be **NOT RUNNING**, that is, not managed by Oracle Trace File Analyzer.

**Parent topic:** Troubleshooting Oracle Trace File Analyzer

### 21.9 Oracle Trace File Analyzer Installation or Oracle Trace File Analyzer Discovery (tfactl rediscover) Fails on Linux 7

Description: Reported errors are similar to:

    Can't locate Data/Dumper.pm in @INC (@INC contains: /usr/local/lib64/perl5
    /usr/local/share/perl5 /usr/lib64/perl5/vendor_perl
    /usr/share/perl5/vendor_perl /usr/lib64/perl5 /usr/share/perl5 .
    /u01/app/12.1.0/grid/tfa/dc75orarac02/tfa_home/bin
    /u01/app/12.1.0/grid/tfa/dc75orarac02/tfa_home/bin/common
    /u01/app/12.1.0/grid/tfa/dc75orarac02/tfa_home/bin/modules
    /u01/app/12.1.0/grid/tfa/dc75orarac02/tfa_home/bin/common/exceptions) at
    /u01/app/12.1.0/grid/tfa/dc75orarac02/tfa_home/bin/common/tfactlshare.pm line 545.

Cause: This error occurs due to Bug 21790910 and Bug 22393355, which are fixed in Oracle Trace File Analyzer version 12.1.2.6.4.

Action: Link the operating system Perl to the version of Perl in the `GRID_HOME`.

**Parent topic:** Troubleshooting Oracle Trace File Analyzer

### 21.10 OSWatcher Analyzer Fails When OSWatcher is Not Running from the TFA_HOME

Description: Reported errors are similar to:

    tfactl> oswbb
    Error: Cannot find OSWatcher files under
    /u01/app/grid/tfa/repository/suptools//oswbb//archive
    OSWatcher analyzer commands are supported only when it is running from TFA_HOME

Cause: Expected behavior when OSWatcher is not running from `TFA_HOME`.

Action:

1.  Stop and disable the OSWatcher version running outside of Oracle Trace File Analyzer.

2.  Start OSWatcher from within Oracle Trace File Analyzer.

**Parent topic:** Troubleshooting Oracle Trace File Analyzer

### 21.11 Oracle Trace File Analyzer Fails to Start with com.sleepycat.je.EnvironmentLockedException Java Exception

Description: Reported errors found in the Oracle Trace File Analyzer `syserrorout` log located in `$TFA_BASE//log` are:

    /u01/app/oracle/tfa//log$ cat syserrorout.08.06.2015-16.19.54

    Exception in thread "TFAMain" com.sleepycat.je.EnvironmentLockedException: (JE 5.0.84)
    /u01/app/oracle/tfa//database/BERKELEY_JE_DB The environment cannot be locked for single writer access.
    ENV_LOCKED: The je.lck file could not be locked. Environment is invalid and must be closed.
    at com.sleepycat.je.log.FileManager.(FileManager.java:368)
    at com.sleepycat.je.dbi.EnvironmentImpl.(EnvironmentImpl.java:483)
    at com.sleepycat.je.dbi.EnvironmentImpl.(EnvironmentImpl.java:409

Cause: The root cause is unknown.

Action:

1.  Check if there are any processes accessing the BDB.

        # fuser $GI_BASE/tfa//database/BERKELEY_JE_DB/je.lck

2.  If a process is returned, then kill it.

        # kill -9

3.  Remove the `$GI_BASE/tfa//database/BERKELEY_JE_DB/je.lck` file.

        # rm -rf $GI_BASE/tfa//database/BERKELEY_JE_DB/je.lck

4.  Start Oracle Trace File Analyzer.

        # $TFA_HOME/bin/tfactl start

**Parent topic:** Troubleshooting Oracle Trace File Analyzer

### 21.12 Oracle Trace File Analyzer Startup Fails When Solution-Soft Time Machine Software is Installed, but Not Running on the System

Action: Uninstall the Time Machine software.

**Parent topic:** Troubleshooting Oracle Trace File Analyzer

### 21.13 Non-privileged User is Not Able to Run tfactl Commands?

Description:

As `root` verify that the non-privileged user has Oracle Trace File Analyzer privilege to run the `tfactl` commands.

    tfactl access lsuser
    /u01/app/12.1.0/grid/bin/tfactl access lsusers
    .---------------------------------.
    | TFA Users in myNode1            |
    +-----------+-----------+---------+
    | User Name | User Type | Status  |
    +-----------+-----------+---------+
    | oracle    | USER      | Allowed |
    '-----------+-----------+---------'

If the user is listed and the status is displayed as **Disabled**, then that indicates all non-privileged user access has been disabled.

Action:

To enable non-privileged user access:

    tfactl access enable

If the user, for example, `oracle` is not listed, then add `oracle`.

    tfactl access add -user oracle

If none of the above techniques resolve the problem, then run `tfactl diagnosetfa -local`. Upload the resultant file to Oracle Support.

**Parent topic:** Troubleshooting Oracle Trace File Analyzer

### 21.14 Oracle Trace File Analyzer Daemon is Not Starting or Not Running?

Description:

    TFA-00001: Failed to start Oracle Trace File Analyzer (TFA) daemon

    TFA-00002: Oracle Trace File Analyzer (TFA) is not running

The errors indicate that Java does not start.

Action:

1.  Verify that Oracle Trace File Analyzer is not running.

        ps -ef|grep -i tfa

    **Note:**

    On some operating systems, the `ps` command truncates the output at 80 characters. The `ps` command does not display the process even if it is running.

2.  To confirm that the Oracle Trace File Analyzer daemon is not running, run the following command run as `root`.

        # tfactl print status

3.  Try starting the Oracle Trace File Analyzer daemon as `root`.

        # tfactl start

    If Oracle Trace File Analyzer still fails to start, then run `tfactl diagnosetfa -local`. Upload the resultant file to Oracle Support.

**Parent topic:** Troubleshooting Oracle Trace File Analyzer
