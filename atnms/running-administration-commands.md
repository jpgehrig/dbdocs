You need `root` access to `tfactl`, or `sudo` access to run all administration commands.

Table E-2 Basic TFACTL commands

| Command                   | Description                                                                                                           |
|:--------------------------|:----------------------------------------------------------------------------------------------------------------------|
| `tfactl start`            | Starts the Oracle Trace File Analyzer daemon on the local node.                                                       |
| `tfactl stop`             | Stops the Oracle Trace File Analyzer daemon on the local node.                                                        |
| `tfactl enable`           | Enables automatic restart of the Oracle Trace File Analyzer daemon after a failure or system reboot.                  |
| `tfactl disable`          | Stops any running Oracle Trace File Analyzer daemon and disables automatic restart.                                   |
| `tfactl uninstall`        | Removes Oracle Trace File Analyzer from the local node.                                                               |
| `tfactl syncnodes`        | Generates and copies Oracle Trace File Analyzer certificates from one Oracle Trace File Analyzer node to other nodes. |
| `tfactl restrictprotocol` | Restricts the use of certain protocols.                                                                               |
| `tfactl status`           | Checks the status of an Oracle Trace File Analyzer process.<br>The output is same as `tfactl print status`.           |

- tfactl access
  Use the `tfactl access` command to allow non-root users to have controlled access to Oracle Trace File Analyzer, and to run diagnostic collections.
- tfactl availability
  Use the `tfactl availability` command to enable or disable resources for Availability Score.
- tfactl diagnosetfa
  Use the `tfactl diagnosetfa` command to collect Oracle Trace File Analyzer diagnostic data from the local node to identify issues with Oracle Trace File Analyzer.
- tfactl disable
  Use the `tfactl disable` command to stop any running Oracle Trace File Analyzer daemon and disable automatic restart.
- tfactl enable
  Use the `tfactl enable` command to enable automatic restart of the Oracle Trace File Analyzer daemon after a failure or system reboot.
- tfactl host
  Use the `tfactl host` command to add hosts to, or remove hosts from the Oracle Trace File Analyzer configuration.
- tfactl print
  Use the `tfactl print` command to print information from the Berkeley database.
- tfactl rest
  Use the `tfactl rest` command to configure REST service.
- tfactl restrictprotocol
  Use the `tfactl restrictprotocol` command to restrict certain protocols.
- tfactl sendmail
  Use the `tfactl sendmail` command to send a test email to verify SMTP configuration.
- tfactl set
  Use the `tfactl set` command to enable or disable, or modify various Oracle Trace File Analyzer functions.
- tfactl setupmos
  Use the `tfactl setupmos` command to store My Oracle Support credentials in Oracle wallet.
- tfactl start
  Use the `tfactl start` command to start the Oracle Trace File Analyzer daemon on the local node, and also to start the desired support tool.
- tfactl status
  Use the `tfactl status` command to check the run status of Oracle Trace File Analyzer.
- tfactl stop
  Use the `tfactl stop` command to stop the Oracle Trace File Analyzer daemon on the local node, and also to stop the desired support tool.
- tfactl syncnodes
  Use the `tfactl syncnodes` command to generate and copy Oracle Trace File Analyzer certificates to other Oracle Trace File Analyzer nodes.
- tfactl uninstall
  Use the `tfactl start` command to to uninstall Oracle Trace File Analyzer.
- tfactl upload
  Use the `tfactl upload` command to upload collections or files to a Service Request.

**Parent topic:** [Oracle Trace File Analyzer Installer, Command-Line and Shell Options](tfa-command-reference.md)

### E.2.1 tfactl access

Use the `tfactl access` command to allow non-root users to have controlled access to Oracle Trace File Analyzer, and to run diagnostic collections.

Non-root users can run a subset of `tfactl` commands. Running a subset of commands enables non-root users to have controlled access to Oracle Trace File Analyzer, and to run diagnostic collections. However, `root` access is still required to install and administer Oracle Trace File Analyzer. Control non-root users and groups using the `tfactl access` command. Add or remove non-root users and groups depending upon your business requirements.

**Note:**

By default, all Oracle home owners, OS DBA groups, and ASM groups are added to the Oracle Trace File Analyzer Access Manager list while installing or upgrading Oracle Trace File Analyzer.

#### Syntax

    tfactl access command [options]
    Commands:lsusers|add|remove|block|unblock|enable|disable|reset|removeall

    tfactl access lsusers [ -local ]

    tfactl access add -user user_name [ -local ]

    tfactl access remove -user user_name [ -all ] [ -local ]

    tfactl access block -user user_name [ -local ]

    tfactl access unblock -user user_name [ -local ]

    tfactl access enable [ -local ]

    tfactl access disable [ -local ]

    tfactl access reset

    tfactl access removeall

#### Parameters

Table E-3 tfactl access Command Parameters

| Parameter   | Description                                                                                                                                                                                                                                                                         |
|:------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `lsusers`   | Lists all the Oracle Trace File Analyzer users and groups.                                                                                                                                                                                                                          |
| `enable`    | Enables Oracle Trace File Analyzer access for non-root users.<br>Use the `–local` flag to change settings only on the local node.                                                                                                                                                   |
| `disable`   | Disables Oracle Trace File Analyzer access for non-root users.<br>However, the list of users who were granted access to Oracle Trace File Analyzer is stored, if the access to non-root users is enabled later.<br>Use the `–local` flag to change settings only on the local node. |
| `add`       | Adds a user or a group to the Oracle Trace File Analyzer access list.                                                                                                                                                                                                               |
| `remove`    | Removes a user or a group from the Oracle Trace File Analyzer access list.                                                                                                                                                                                                          |
| `block`     | Blocks Oracle Trace File Analyzer access for non-root user.<br>Use this command to block a specific user even though the user is a member of a group that is granted access to Oracle Trace File Analyzer.                                                                          |
| `unblock`   | Enables Oracle Trace File Analyzer access for non-root users who were blocked earlier.<br>Use this command to unblock a user that was blocked earlier by running the command `tfactl access block`.                                                                                 |
| `reset`     | Resets to the default access list that includes all Oracle Home owners and DBA groups.                                                                                                                                                                                              |
| `removeall` | Removes all Oracle Trace File Analyzer users and groups.<br>Remove all users from the Oracle Trace File Analyzer access list including the default users and groups.                                                                                                                |

Example E-1 tfactl access

To list all the Oracle Trace File Analyzer users and groups.

    $ tfactl access lsusers

    .---------------------------------.
    |     TFA Users in rws1270069     |
    +-----------+-----------+---------+
    | User Name | User Type | Status  |
    +-----------+-----------+---------+
    | oradb     | USER      | Allowed |
    | oragrid   | USER      | Allowed |
    '-----------+-----------+---------'

To add a user, for example, abc to the Oracle Trace File Analyzer access list and enable access to Oracle Trace File Analyzer across cluster.

    $ tfactl access add -user abc

To add all members of a group, for example, xyz to the Oracle Trace File Analyzer access list and enable access to Oracle Trace File Analyzer on the localhost.

    $ tfactl access add -group xyz -local

To remove a user, for example, abc from the Oracle Trace File Analyzer access list.

    $ tfactl access remove -user abc

To block a user, for example, xyz from accessing Oracle Trace File Analyzer.

    $ tfactl access block -user xyz

To remove all Oracle Trace File Analyzer users and groups.

    $ tfactl access removeall

**Parent topic:** Running Administration Commands

### E.2.2 tfactl availability

Use the `tfactl availability` command to enable or disable resources for Availability Score.

#### Syntax

    tfactl enable -key key -value value  | -list

    tfactl  disable -key key -value value [-for nd|D|h|H|m|M]  | -list [-for nd|D|h|H|m|M]

#### Parameters

Table E-4 tfactl enable Command Parameters

| Parameter               | Description                                                     |
|:------------------------|:----------------------------------------------------------------|
| `-type ``resource_type` | Specify the resource type that you want to enable.              |
| `-key ``key`            | Specify the key of the resource that you want to enable.        |
| `-list`                 | Displays the list of resources that are available for enabling. |

#### Parameters

Table E-5 tfactl disable Command Parameters

| Parameter                                                                                         | Description                                                                                                 |
|:--------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------|
| `-type ``resource_type`                                                                           | Specify the resource type that you want to enable.                                                          |
| `-key ``key`                                                                                      | Specify the key of the resource that you want to enable.                                                    |
| `[-for n``d``|``D``|``h``|``H``|``m``|``M``] | -list [-for n``d``|``D``|``h``|``H``|``m``|``M``]` | Specify the days, hours, or minutes to determine how long the resource will be disabled. Default is 7 days. |
| `-list`                                                                                           | Displays the list of resources that are available for disabling..                                           |

Example E-2 tfactl enable

    /scratch/app/11.2.0.4/grid/bin/tfactl availability enable -list
    /scratch/app/11.2.0.4/grid/bin/tfactl availability enable -type server_disk -key filesystem -value "/dev/xvdad1"
    /scratch/app/11.2.0.4/grid/bin/tfactl availability enable -type server_network -key interface -value eth1

Example E-3 tfactl disable

    /scratch/app/11.2.0.4/grid/bin/tfactl availability disable -list
    /scratch/app/11.2.0.4/grid/bin/tfactl availability disable -list -for 3d
    /scratch/app/11.2.0.4/grid/bin/tfactl availability disable -list -for 15h
    /scratch/app/11.2.0.4/grid/bin/tfactl availability disable -type server_disk -key filesystem -value "/dev/xvdad1"
    /scratch/app/11.2.0.4/grid/bin/tfactl availability disable -type server_network -key interface -value eth1
    /scratch/app/11.2.0.4/grid/bin/tfactl availability disable -type server_disk -key filesystem -value "/dev/xvdad1" -for 3d
    /scratch/app/11.2.0.4/grid/bin/tfactl availability disable -type server_network -key interface -value eth1 -for 12h

**Parent topic:** Running Administration Commands

### E.2.3 tfactl diagnosetfa

Use the `tfactl diagnosetfa` command to collect Oracle Trace File Analyzer diagnostic data from the local node to identify issues with Oracle Trace File Analyzer.

#### Syntax

    tfactl diagnosetfa [-repo repository] [-tag tag_name] [-local]

#### Parameters

Table E-6 tfactl diagnosetfa Command Parameters

| Parameter            | Description                                                                             |
|:---------------------|:----------------------------------------------------------------------------------------|
| `-repo ``repository` | Specify the repository directory for Oracle Trace File Analyzer diagnostic collections. |
| `-tag ``tag_name`    | Oracle Trace File Analyzer collects the files into `tag_name` directory.                |
| `-local`             | Runs Oracle Trace File Analyzer diagnostics only on the local node.                     |

Example E-4 tfactl diagnosetfa

    $ tfactl diagnosetfa -local

    Running TFA Diagnostics...

    Node List to collect TFA Diagnostics :
         1  myhost

    Running TFA Diagnostics on myhost...

    Wed Sep 12 00:12:18 2018 : Collecting TFA Process details...
    Wed Sep 12 00:12:18 2018 : Collecting Details of TFA Files...
    Wed Sep 12 00:12:19 2018 : Collecting CRS Status...
    Wed Sep 12 00:12:19 2018 : Collecting GI Install Logs...
    Wed Sep 12 00:19:15 2018 : Collecting TFA Install Logs...
    Wed Sep 12 00:19:15 2018 : Collecting Disk Space...
    Wed Sep 12 00:19:16 2018 : Collecting Top Output...
    Wed Sep 12 00:19:16 2018 : Collecting TFA Status...
    Wed Sep 12 00:19:19 2018 : Collecting JStack Output...
    Wed Sep 12 00:19:31 2018 : Collecting TFA Logs...
    Wed Sep 12 00:19:32 2018 : Collecting TFA BDB Stats...
    Wed Sep 12 00:19:43 2018 : Zipping Collections...

    Sleeping for 10 Seconds...

    TFA Diagnostics are being collected to /tmp/tfadiagnostics_20180912_001217 :
    /tmp/tfadiagnostics_20180912_001217/myhost.zip

**Parent topic:** Running Administration Commands

### E.2.4 tfactl disable

Use the `tfactl disable` command to stop any running Oracle Trace File Analyzer daemon and disable automatic restart.

#### Syntax

    tfactl disable

**Parent topic:** Running Administration Commands

### E.2.5 tfactl enable

Use the `tfactl enable` command to enable automatic restart of the Oracle Trace File Analyzer daemon after a failure or system reboot.

#### Syntax

    tfactl enable

**Parent topic:** Running Administration Commands

### E.2.6 tfactl host

Use the `tfactl host` command to add hosts to, or remove hosts from the Oracle Trace File Analyzer configuration.

#### Syntax

    tfactl host [add host_name | remove host_name]

#### Usage Notes

View the current list of hosts in the Oracle Trace File Analyzer configuration using the `tfactl print hosts` command. The `tfactl print hosts` command lists the hosts that are part of the Oracle Trace File Analyzer cluster:

    $ tfactl print hosts
    Host Name : node1
    Host Name : node2

When you add a new host, Oracle Trace File Analyzer contacts the Oracle Trace File Analyzer instance on the other host. Oracle Trace File Analyzer authenticates the new host using certificates and both the Oracle Trace File Analyzer instances synchronize their respective hosts lists. Oracle Trace File Analyzer does not add the new host until the certificates are synchronized.

After you successfully add a host, all the cluster-wide commands are activated on all nodes registered in the Berkeley database.

Example E-5 tfactl host

Specify a host name to add:

    $ tfactl host add myhost

Specify a host name to remove:

    $ tfactl host remove myhost

**Parent topic:** Running Administration Commands

### E.2.7 tfactl print

Use the `tfactl print` command to print information from the Berkeley database.

#### Syntax

    tfactl print command [options]
    Commands:status|components|config|directories|hosts|actions|repository|suspendedips|protocols|smtp

    tfactl print status

    tfactl print components [ [component_name1] [component_name2] ... [component_nameN] ]

    tfactl print config [ -node all | local | n1,n2,...  -name param]

    tfactl print directories [ -node all | local | n1,n2,... ] [ -comp component_name1,component_name2,... ] [ -policy exclusions | noexclusions ]
    [ -permission public | private ]

    tfactl print hosts

    tfactl print actions [ -status status ] [ -since nh|d ]

    tfactl print repository

    tfactl print suspendedips

    tfactl print protocols

    tfactl print smtp

#### Parameters

Table E-7 tfactl print Command Parameters

| Parameter      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:---------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `status`       | Displays the status of Oracle Trace File Analyzer across all nodes in the cluster. Also, displays the Oracle Trace File Analyzer version and the port on which it is running.                                                                                                                                                                                                                                                                            |
| `components`   | Displays the desired components in the configuration.                                                                                                                                                                                                                                                                                                                                                                                                    |
| `config`       | Displays the current Oracle Trace File Analyzer configuration settings.                                                                                                                                                                                                                                                                                                                                                                                  |
| `directories`  | Lists all the directories that Oracle Trace File Analyzer scans for trace or log file data. Also, displays the location of the trace directories allocated for the database, Oracle ASM, and instance.                                                                                                                                                                                                                                                   |
| `hosts`        | Lists the hosts that are part of the Oracle Trace File Analyzer cluster, and that can receive cluster-wide commands.                                                                                                                                                                                                                                                                                                                                     |
| `actions`      | Lists all the actions submitted to Oracle Trace File Analyzer, such as diagnostic collection. By default, `tfactl print` commands only display actions that are running or that have completed in the last hour.                                                                                                                                                                                                                                         |
| `repository`   | Displays the current location and amount of used space of the repository directory. Initially, the maximum size of the repository directory is the smaller of either 10 GB or 50% of available file system space. If the maximum size is exceeded or the file system space gets to 1 GB or less, then Oracle Trace File Analyzer suspends operations and closes the repository. Use the `tfactl purge` command to clear collections from the repository. |
| `suspendedips` | Lists all paused Oracle Trace File Analyzer IPS collections.                                                                                                                                                                                                                                                                                                                                                                                             |
| `protocols`    | Lists all available and restricted protocols.                                                                                                                                                                                                                                                                                                                                                                                                            |
| `smtp`         | Displays the SMTP server configuration                                                                                                                                                                                                                                                                                                                                                                                                                   |

#### Options

| Option                | Description                                                                                                                     |
|:----------------------|:--------------------------------------------------------------------------------------------------------------------------------|
| `-status ``status`    | Action status can be one or more of `COMPLETE`, `RUNNING`, `FAILED`, `REQUESTED`<br>Specify a comma-separated list of statuses. |
| `-since ``n``h``|``d` | Specify actions from past n days or n hours.                                                                                    |

Example E-6 tfactl print smtp

    tfactl print smtp

    .---------------------------.
    | SMTP Server Configuration |
    +---------------+-----------+
    | Parameter     | Value     |
    +---------------+-----------+
    | smtp.auth     | false     |
    | smtp.from     | tfa       |
    | smtp.user     | -         |
    | smtp.cc       | -         |
    | smtp.port     |        25 |
    | smtp.bcc      | -         |
    | smtp.password | *******   |
    | smtp.host     | localhost |
    | smtp.to       | -         |
    | smtp.debug    | true      |
    | smtp.ssl      | false     |
    '---------------+-----------'

Example E-7 tfactl print protocols

    tfactl print protocols

    .--------------------------------------------------.
    |                    rws1270069                    |
    +--------------------------------------------------+
    | Protocols                                        |
    +--------------------------------------------------+
    | Available : [TLSv1.2]                            |
    | Restricted : [SSLv3, SSLv2Hello, TLSv1, TLSv1.1] |
    '--------------------------------------------------'

Example E-8 tfactl print components ASM

    $ tfactl print components ASM

    .--------------------------------------------------.
    |                  XML Components                  |
    +---------------+----------------------------------+
    | Field         | Value                            |
    +---------------+----------------------------------+
    | Name          | ASM                              |
    | Description   | ASM logs                         |
    | Comp. Types   | collection action                |
    | Configuration | all                              |
    | Subcomponents | name:instance required: default: |
    | Also collect  | TNS                              |
    |               | AFD                              |
    |               | ASMPROXY                         |
    |               | ASMIO                            |
    '---------------+----------------------------------'

Example E-9 tfactl print components ODASTORAGE

    $ tfactl print components ODASTORAGE

    .-------------------------------------------.
    |               XML Components              |
    +---------------+---------------------------+
    | Field         | Value                     |
    +---------------+---------------------------+
    | Name          | ODASTORAGE                |
    | Description   | ODA Storage logs and Data |
    | Comp. Types   | action                    |
    | Configuration | ODA                       |
    | Also collect  | OS                        |
    |               | ODA                       |
    |               | ASM                       |
    |               | DCS                       |
    '---------------+---------------------------'

Example E-10 tfactl print config

    $ tfactl print config

    .------------------------------------------------------------------------------------.
    |                                     rws1270069                                     |
    +-----------------------------------------------------------------------+------------+
    | Configuration Parameter                                               | Value      |
    +-----------------------------------------------------------------------+------------+
    | TFA Version                                                           | 18.3.0.0.0 |
    | Java Version                                                          | 1.8        |
    | Public IP Network                                                     | true       |
    | Automatic Diagnostic Collection                                       | true       |
    | Alert Log Scan                                                        | true       |
    | Disk Usage Monitor                                                    | true       |
    | Managelogs Auto Purge                                                 | false      |
    | Trimming of files during diagcollection                               | true       |
    | Inventory Trace level                                                 | 1          |
    | Collection Trace level                                                | 1          |
    | Scan Trace level                                                      | 1          |
    | Other Trace level                                                     | 1          |
    | Repository current size (MB)                                          | 588        |
    | Repository maximum size (MB)                                          | 4724       |
    | Max Size of TFA Log (MB)                                              | 50         |
    | Max Number of TFA Logs                                                | 10         |
    | Max Size of Core File (MB)                                            | 50         |
    | Max Collection Size of Core Files (MB)                                | 500        |
    | Minimum Free Space to enable Alert Log Scan (MB)                      | 500        |
    | Time interval between consecutive Disk Usage Snapshot(minutes)        | 60         |
    | Time interval between consecutive Managelogs Auto Purge(minutes)      | 60         |
    | Logs older than the time period will be auto purged(days[d]|hours[h]) | 30d        |
    | Automatic Purging                                                     | true       |
    | Age of Purging Collections (Hours)                                    | 12         |
    | TFA IPS Pool Size                                                     | 5          |
    | TFA ISA Purge Age (seconds)                                           | 2592000    |
    | TFA ISA Purge Mode                                                    | simple     |
    '-----------------------------------------------------------------------+------------'

In the preceding sample output:

- `Automatic diagnostic collection`: When `ON` (default is `OFF`), if scanning an alert log, then finding specific events in those logs triggers diagnostic collection.

- `Trimming of files during diagcollection`: Determines if Oracle Trace File Analyzer trims large files to contain only data that is within the specified time ranges. When trimming is `OFF`, no trimming of trace files occurs for automatic diagnostic collection.

- `Repository current size in MB`: How much space in the repository is used.

- `Repository maximum size in MB`: The maximum size of storage space in the repository. Initially, the maximum size is set to the smaller of either 10 GB or 50% of free space in the file system.

- `Trace Level`: 1 is the default, and the values 2, 3, and 4 have increasing verbosity. While you can set the trace level dynamically for running the Oracle Trace File Analyzer daemon, increasing the trace level significantly impacts the performance of Oracle Trace File Analyzer. Increase the trace level only at the request of My Oracle Support.

- `Automatic Purging`: Automatic purging of Oracle Trace File Analyzer collections is enabled by default. Oracle Trace File Analyzer collections are purged if their age exceeds the value of `Minimum Age of Collections to Purge`, and the repository space is exhausted.

- `Minimum Age of Collections to Purge (Hours)`: The minimum number of hours that Oracle Trace File Analyzer keeps a collection, after which Oracle Trace File Analyzer purges the collection. You can set the number of hours using the `tfactl set minagetopurge=``hours` command.

- `Minimum Space free to enable Alert Log Scan (MB)`: The space limit, in MB, at which Oracle Trace File Analyzer temporarily suspends alert log scanning until space becomes free. Oracle Trace File Analyzer does not store alert log events if space on the file system used for the metadata database falls below the limit.

**Parent topic:** Running Administration Commands

### E.2.8 tfactl rest

Use the `tfactl rest` command to configure REST service.

#### Syntax

    tfactl rest
    [-status|-start|-stop|-upgrade|-uninstall]
    [-dir directory]
    [-port port]
    [-user user]
    [-debug [-level debug_level 1-6]]

**Note:**

You can run the REST command only as `root` user.

#### Parameters

Table E-8 REST Command Parameters

| Parameter    | Description                                                                                                                                                 |
|:-------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-status`    | Prints the current status.                                                                                                                                  |
| `-start`     | Starts Oracle Trace File Analyzer REST services if not already running.                                                                                     |
| `-stop`      | Stops Oracle Trace File Analyzer REST services if running.                                                                                                  |
| `-upgrade`   | Checks if the configured ORDS API should be upgraded.<br>If the ORDS API needs upgrading, then stops ORDS, upgrades the API, and then restarts ORDS.        |
| `-uninstall` | Removes the Oracle Trace File Analyzer REST configuration.                                                                                                  |
| `–dir`       | The directory to use to store the Oracle Trace File Analyzer REST configuration details.<br>Defaults to the users home directory.                           |
| `–port`      | The port to run ORDS on.<br>Defaults to 9090.                                                                                                               |
| `-user`      | The user to start ORDS as.<br>Defaults to the GRID owner.                                                                                                   |
| `–debug`     | Enables debug.                                                                                                                                              |
| `–level`     | The level of debug to use, where available levels are:<br>• 1 – FATAL<br>• 2 – ERROR<br>• 3 – WARNING<br>• 4 – INFO (default)<br>• 5 – DEBUG<br>• 6 – TRACE |

**Parent topic:** Running Administration Commands

### E.2.9 tfactl restrictprotocol

Use the `tfactl restrictprotocol` command to restrict certain protocols.

#### Syntax

    tfactl restrictprotocol [-force] protocol

Example E-11 tfactl restrictprotocol

    $ tfactl restrictprotocol TLSv1

**Parent topic:** Running Administration Commands

### E.2.10 tfactl sendmail

Use the `tfactl sendmail` command to send a test email to verify SMTP configuration.

#### Syntax

    tfactl sendmail email_address

**Parent topic:** Running Administration Commands

### E.2.11 tfactl set

Use the `tfactl set` command to enable or disable, or modify various Oracle Trace File Analyzer functions.

#### Syntax

    tfactl set
    [ autodiagcollect=ON|OFF
    | trimfiles=ON|OFF
    | tracelevel=COLLECT|SCAN|INVENTORY|OTHER:1|2|3|4
    | reposizeMB=n
    | repositorydir=dir [-force]
    | logsize=n [-local]
    | logcount=n [-local]
    | maxcorefilesize=n [-local]
    | maxcorecollectionsize=n [-local] autopurge=ON|OFF
    | publicip=ON|OFF
    | minSpaceForRTScan=n
    | rtscan=ON|OFF
    | diskUsageMon=ON|OFF
    | diskUsageMonInterval=n
    | manageLogsAutoPurge=ON|OFF
    | manageLogsAutoPurgeInterval=n
    | manageLogsAutoPurgePolicyAge=d|h
    | minagetopurge=n
    | tfaIpsPoolSize=n
    | tfaDbUtlPurgeAge=n
    | tfaDbUtlPurgeMode=simple|resource ]
    [-c]

#### Parameters

Table E-9 tfactl set Command Parameters

| Parameter                                                      | Description                                                                                                                                                                                                                                                                                                                                                                       |
|:---------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `autodiagcollect=ON | OFF`                                     | When set to `OFF` (default) automatic diagnostic collection is disabled. If set to `ON`, then Oracle Trace File Analyzer automatically collects diagnostics when certain patterns occur while Oracle Trace File Analyzer scans the alert logs.<br>To set automatic collection for all nodes of the Oracle Trace File Analyzer cluster, you must specify the `-c` parameter.       |
| `trimfiles=ON|OFF`                                             | When set to `ON`, Oracle Trace File Analyzer trims the files to have only the relevant data when diagnostic collection is done as part of a scan.<br>Note: When using `tfactl diagcollect`, you determine the time range for trimming with the parameters you specify. Oracle recommends that you not set this parameter to `OFF`, because untrimmed data can consume much space. |
| `tracelevel=COLLECT | SCAN | INVENTORY | OTHER: 1 | 2 | 3 | 4` | You can set trace levels for certain operations, including `INVENTORY:``n`, `SCAN:``n`, `COLLECT:``n`, `OTHER:``n`. In this syntax, `n` is a number from 1 to 4 and `OTHER` includes all messages not relevant to the first three components.<br>Note: Do not change the tracing level unless you are directed to do so by My Oracle Support.                                     |
| `reposizeMB=``number`                                          | Sets the maximum size, in MB, of the collection repository.                                                                                                                                                                                                                                                                                                                       |
| `repositorydir=``directory`` [-force]`                         | Specify the collection repository directory.<br>Use the `-force` option to skip initial checks while changing repository (Not Recommended)                                                                                                                                                                                                                                        |
| `logsize=``n`` [-local]`                                       | Sets the maximum size, in MB, of each log before Oracle Trace File Analyzer rotates to a new log (default is 50 MB). Use the `-local` parameter to apply the change only to the local node.                                                                                                                                                                                       |
| `logcount=``n`` [-local]`                                      | Sets the maximum number of logs of specified size that Oracle Trace File Analyzer retains (default is 10). Use the `-local` option to apply the change only to the local node.                                                                                                                                                                                                    |
| `port=``n`                                                     | Specify the Oracle Trace File Analyzer port.                                                                                                                                                                                                                                                                                                                                      |
| `maxcorefilesize=``n`` [-local] `                              | Sets the maximum size of the core files to the size specified in MB (default is 20 MB ).                                                                                                                                                                                                                                                                                          |
| `maxcorecollectionsize=``n`                                    | Sets the maximum collection size of the core files to the size specified in MB (default is 200 MB ).                                                                                                                                                                                                                                                                              |
| `publicip=ON|OFF `                                             | Allows Oracle Trace File Analyzer to run on public network.                                                                                                                                                                                                                                                                                                                       |
| `smtp`                                                         | Specify the configuration details for the SMTP server to use for email notifications when prompted.                                                                                                                                                                                                                                                                               |
| `minSpaceForRTScan=``n`                                        | Specify the minimum space required to run RT scan (default is 500).                                                                                                                                                                                                                                                                                                               |
| `rtscan`                                                       | Specify to allow Oracle Trace File Analyzer to perform alert log scanning.                                                                                                                                                                                                                                                                                                        |
| `diskUsageMon=ON|OFF`                                          | Turns ON (default) or OFF monitoring disk usage and recording snapshots.<br>Oracle Trace File Analyzer stores the snapshots under `tfa/repository/suptools/``node``/managelogs/usage_snapshot/`.                                                                                                                                                                                  |
| `diskUsageMonInterval=``minutes`                               | Specify the time interval between snapshots (60 minutes by default).                                                                                                                                                                                                                                                                                                              |
| `manageLogsAutoPurge=ON | OFF`                                 | Turns automatic purging on or off (ON by default in DSC and OFF by default elsewhere).                                                                                                                                                                                                                                                                                            |
| `manageLogsAutoPurgeInterval=``minutes`                        | Specify the purge frequency (default is 60 minutes).                                                                                                                                                                                                                                                                                                                              |
| `manageLogsAutoPurgePolicyAge=``n``d|h`                        | Age of logs to be purged (30 days by default).                                                                                                                                                                                                                                                                                                                                    |
| `minagetopurge=``n`                                            | Set the minimum age, in hours, for a collection before Oracle Trace File Analyzer considers it for purging (default is 12 hours).                                                                                                                                                                                                                                                 |
| `autopurge`                                                    | When set to `ON`, enables automatic purging of collections when Oracle Trace File Analyzer observes less space in the repository (default is `ON`).                                                                                                                                                                                                                               |
| `tfaIpsPoolSize=``n`                                           | Sets the Oracle Trace File Analyzer IPS pool size.                                                                                                                                                                                                                                                                                                                                |
| `tfaDbUtlPurgeAge=``n`                                         | Sets the Oracle Trace File Analyzer ISA purge age (in seconds).                                                                                                                                                                                                                                                                                                                   |
| `tfaDbUtlPurgeMode=simple|resource`                            | Sets the Oracle Trace File Analyzer ISA purge mode (simple/resource).                                                                                                                                                                                                                                                                                                             |
| `-c`                                                           | Propagates the settings to all nodes in the Oracle Trace File Analyzer configuration.                                                                                                                                                                                                                                                                                             |

Example E-12 tfactl set

    $ tfactl set autodiagcollect=ON reposizeMB=20480
    $ tfactl set autodiagcollect=ON
    $ tfactl set autopurge=ON
    $ tfactl set tracelevel=INVENTORY:3
    $ tfactl set reposizeMB=20480
    $ tfactl set logsize=100
    $ tfactl set port=5000

**Parent topic:** Running Administration Commands

### E.2.12 tfactl setupmos

Use the `tfactl setupmos` command to store My Oracle Support credentials in Oracle wallet.

#### Syntax

    tfactl setupmos

**Parent topic:** Running Administration Commands

### E.2.13 tfactl start

Use the `tfactl start` command to start the Oracle Trace File Analyzer daemon on the local node, and also to start the desired support tool.

#### Syntax

    tfactl start [tool]

**Parent topic:** Running Administration Commands

### E.2.14 tfactl status

Use the `tfactl status` command to check the run status of Oracle Trace File Analyzer.

#### Syntax

    tfactl status

Example E-13 tfactl status

    $ /tfactl status

    .------------------------------------------------------------------------------------------------.
    | Host       | Status of TFA | PID | Port | Version    | Build ID             | Inventory Status |
    +------------+---------------+-----+------+------------+----------------------+------------------+
    | rws1270069 | RUNNING       | 316 | 5000 | 18.3.0.0.0 | 18300020180828031750 | COMPLETE         |
    '------------+---------------+-----+------+------------+----------------------+------------------'

**Parent topic:** Running Administration Commands

### E.2.15 tfactl stop

Use the `tfactl stop` command to stop the Oracle Trace File Analyzer daemon on the local node, and also to stop the desired support tool.

#### Syntax

    tfactl stop [tool]

**Parent topic:** Running Administration Commands

### E.2.16 tfactl syncnodes

Use the `tfactl syncnodes` command to generate and copy Oracle Trace File Analyzer certificates to other Oracle Trace File Analyzer nodes.

#### Syntax

    tfactl syncnodes [-regenerate]

#### Parameters

Table E-10 tfactl syncnodes Command Parameters

| Parameter     | Description                                          |
|:--------------|:-----------------------------------------------------|
| `-regenerate` | Regenerates Oracle Trace File Analyzer certificates. |

**Parent topic:** Running Administration Commands

### E.2.17 tfactl uninstall

Use the `tfactl start` command to to uninstall Oracle Trace File Analyzer.

#### Syntax

Run the `uninstall` command as `root`, or install user

    tfactl uninstall

**Parent topic:** Running Administration Commands

### E.2.18 tfactl upload

Use the `tfactl upload` command to upload collections or files to a Service Request.

#### Syntax

    tfactl upload -sr SR# [ -user UserId | -wallet ] Files

#### Parameters

Table E-11 tfactl upload Command Parameters

| Parameter        | Description                                                                     |
|:-----------------|:--------------------------------------------------------------------------------|
| `-sr ``SR#`      | Specify the service request number to use for file upload.                      |
| `-user ``userid` | Specify the My Oracle Support user ID.                                          |
| `-wallet`        | Use this option for the `upload` command to use credentials from Oracle wallet. |
| `Files`          | Specify a space-separated list of files that you want to upload.                |

**Parent topic:** Running Administration Commands
