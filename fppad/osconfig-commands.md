## osconfig Commands

Use commands with the `osconfig` keyword to backup, compare, and manage operating system configuration information.

- rhpctl collect osconfig
  Collects a backup of the operating system configuration for a cluster.
- rhpctl compare osconfig
  Compares operating system configurations for a specific cluster.
- rhpctl disable osconfig
  Disables a scheduled backup of the operating system configuration and gives the option to delete all collected configuration backups.
- rhpctl enable osconfig
  Enable operating system configuration information collection for the client cluster.
- rhpctl query osconfig
  Provides historic operating system configuration collection information, such as the collection schedule, retention count, scheduled job for periodic collection, and collection data.

**Parent topic:** [RHPCTL Command Reference](rhpctl-command-reference.md)

### rhpctl collect osconfig

Collects a backup of the operating system configuration for a cluster.

#### Syntax

    rhpctl collect osconfig -client cluster_name [-targetnode node_name
      {-sudouser sudo_user_name -sudopath sudo_binary_location | -root}]

#### Parameters

Table A-42 rhpctl collect osconfig Command Parameters

| Parameter                                                              | Description                                                                                                           |
|:-----------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------|
| `-client ``cluster_name`                                               | Specify the name of the client cluster.                                                                               |
| `-targetnode ``node_name`                                              | Optionally, you can specify the name of an `rhpclient`-less target.                                                   |
| `-sudouser ``sudo_user_name`` -sudopath ``sudo_binary_path`` | -root]` | If you use the `-targetnode` parameter, then you must specify either sudo or `root` to perform super user operations. |

**Parent topic:** osconfig Commands

### rhpctl compare osconfig

Compares operating system configurations for a specific cluster.

#### Syntax

    rhpctl compare osconfig -client cluster_name -node node_name -id1 identifier -id2 identifier

#### Parameters

Table A-43 rhpctl compare osconfig Command Parameters

| Parameter                | Description                                                                                          |
|:-------------------------|:-----------------------------------------------------------------------------------------------------|
| `-client ``cluster_name` | Specify the name of the client cluster in which you want to compare operating system configurations. |
| `-node ``node_name`      | Specify the name of a node in a remote cluster.                                                      |
| `-id1 ``identifier`      | Specify an identifier of an operating system configuration to be considered as a reference.          |
| `-id2 ``identifier`      | Specify an identifier of an operating system configuration to be compared.                           |

**Parent topic:** osconfig Commands

### rhpctl disable osconfig

Disables a scheduled backup of the operating system configuration and gives the option to delete all collected configuration backups.

#### Syntax

    rhpctl disable osconfig [-client cluster_name] [-clean]

#### Usage Notes

- Optionally, you can specify a client cluster name on which you want to disable collection of operating system configuration information.

- Optionally, you can use the `–clean` parameter to delete all operating system configuration backups.

**Parent topic:** osconfig Commands

### rhpctl enable osconfig

Enable operating system configuration information collection for the client cluster.

#### Syntax

    rhpctl enable osconfig -client cluster_name [-retaincopies count]
      [-start timer_value] [-frequency collect_frequency] [-collectnow
       [-targetnode node_name {-sudouser sudo_user_name -sudopath sudo_binary_location
        | -root}]] [-force]

#### Parameters

Table A-44 rhpctl enable osconfig Command Parameters

| Parameter                                                              | Description                                                                                                                                  |
|:-----------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------|
| `-client ``cluster_name`                                               | Specify the name of the client cluster.                                                                                                      |
| `-retaincopies ``count`                                                | Optionally, you can specify the number of scheduled backups you want to be maintained. The default value is `37`.                            |
| `-start ``timer_value`                                                 | Optionally, you can specify a start date and time to run configuration collection according to the following example: 2018-07-23T00:00:00-07 |
| `-frequency ``collect_frequency`                                       | Optionally, you can specify the configuration collection interval in number of days.                                                         |
| `-collectnow`                                                          | Optionally, you can use this parameter to collect configuration information, immediately.                                                    |
| `-targetnode ``node_name`                                              | Optionally, you can specify the name of an `rhpclient`-less target.                                                                          |
| `-sudouser ``sudo_user_name`` -sudopath ``sudo_binary_path`` | -root]` | If you use the `-targetnode` parameter, then you must specify either sudo or `root` to perform super user operations.                        |
| `-force`                                                               | Optionally, you can use this parameter to forcibly modify the count for the `-retaincopies` parameter previously set.                        |

**Parent topic:** osconfig Commands

### rhpctl query osconfig

Provides historic operating system configuration collection information, such as the collection schedule, retention count, scheduled job for periodic collection, and collection data.

#### Syntax

    rhpctl query osconfig -client client_name

#### Usage Notes

Provide the name of the client cluster that you want to query operating system configuration collection information.

#### Example

This command returns output similar to the following:

    $ rhpctl query osconfig -client rhpdemocluster

    OSConfig Enabled: true
    Collection start time: “00:00:00"
    Collection frequency: "1"
    retaincopies count: "35"
    OSConfig periodic Job ID: "38"
    Collection storage path: "/scratch/rhp_storage/chkbase/osconfig/rhpdemocluster"
    Latest list of nodes for collections : "mjk00fwc"
    OSConfig ID: "22" Collected on: "Jul 27, 2018 22:00:58 PM"
    OSConfig ID: "21" Collected on: "Jul 26, 2018 22:00:47 PM"
    OSConfig ID: "20" Collected on: "Jul 25, 2018 22:00:29 PM"

**Parent topic:** osconfig Commands
