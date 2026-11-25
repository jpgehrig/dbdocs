This topic provides a summary of commands to manage Oracle ACFS in the cluster domain.

Table 16-105 lists commands for managing Oracle ACFS in the cluster domain and provides brief descriptions. For information about Oracle ACFS in the cluster domain and Oracle ACFS remote service, refer to [About Oracle ACFS in the Cluster Domain](understand-acfs-concepts.md).

For more information about running Oracle ACFS commands, refer to [About Using Oracle ACFS Command-Line Tools](steps-manage-acfs.md).

Table 16-105 Summary of commands for Oracle ACFS in the cluster domain

| Command                     | Description                                                                                                                 |
|:----------------------------|:----------------------------------------------------------------------------------------------------------------------------|
| acfsremote installed        | Checks whether your current node has the Oracle ACFS remote service drivers and any applicable system transports installed. |
| acfsremote loaded           | Checks the status of system resources to determine if Oracle ACFS remote service is loaded.                                 |
| acfsremote supported        | Checks to ensure that your current node is supported for Oracle ACFS remote service.                                        |
| acfsutil cluster credential | Generates, updates, and imports the Oracle ACFS remote service credentials.                                                 |
| acfsutil cluster info       | Displays the information on the type of cluster and internal information for the running cluster.                           |
| acfsutil remote clear       | Clears the Oracle ACFS remote attribute from a file.                                                                        |
| acfsutil remote set         | Sets a file attribute as Oracle ACFS remote.                                                                                |
| advmutil export create      | Creates the exports for a cluster and allocates their initial storage.                                                      |
| advmutil export list        | Queries information for export management.                                                                                  |
| advmutil export lsof        | Displays active files for all repositories or in a single repository.                                                       |
| advmutil export mapping     | Reexports all exports or only exports for a particular cluster.                                                             |
| advmutil export remove      | Removes the configuration metadata of an export.                                                                            |
| advmutil export resize      | Resizes storage to the underlying backing file for an export.                                                               |
| advmutil session list       | Lists the current state and description of Oracle ACFS remote service sessions on the Oracle Database member cluster.       |
| advmutil transport create   | Creates a transport on the Domain Services Cluster (DSC).                                                                   |
| advmutil transport list     | Displays the configured transports on the system.                                                                           |
| advmutil transport remove   | Removes a transport.                                                                                                        |

### acfsremote installed

#### Purpose

Checks whether your current node has the Oracle ACFS remote service drivers installed.

#### Syntax and Description

    acfsremote installed -h
    acfsremote installed [-trace trace_level] [-member] [-domain]

The following table contains the options available with the `acfsremote` `installed` command.

Table 16-106 Options for the acfsremote installed command

| Option                 | Description                                           |
|:-----------------------|:------------------------------------------------------|
| `-trace` `trace_level` | Specifies the trace level.                            |
| `-member`              | Specifies to check the member cluster                 |
| `—domain`              | Specifies to check the Domain Services Cluster (DSC). |

`acfsremote` `installed` checks whether your current node has the Oracle ACFS remote service drivers and any applicable system transports installed.

This command is applicable on both member clusters and Domain Services Clusters (DSC).

Example 16-100 Using acfsremote installed

In this example the Oracle ACFS remote service drivers and an iSCSI transport have been installed.

    #acfsremote installed
    ACFS-9843: ACFS Remote installed: True
    ACFS-9844: iSCSI installed: True

### acfsremote loaded

#### Purpose

Checks the status of system resources to determine if Oracle ACFS remote service is loaded.

#### Syntax and Description

    acfsremote loaded -h
    acfsremote loaded [-trace trace_level] [-member] [-domain]

The following table contains the options available with the `acfsremote` `loaded` command.

Table 16-107 Options for the acfsremote loaded command

| Option                 | Description                                           |
|:-----------------------|:------------------------------------------------------|
| `-trace` `trace_level` | Specifies the trace level.                            |
| `-member`              | Specifies to check the member cluster                 |
| `—domain`              | Specifies to check the Domain Services Cluster (DSC). |

`acfsremote` `loaded` checks the status of system resources to determine if Oracle ACFS remote service is loaded. If all services are loaded, then Oracle ACFS remote service is loaded and running correctly. If a transport is not used or configured, then it may show as `False`.

This command is applicable on both member clusters and Domain Services Clusters (DSC).

Example 16-101 Using acfsremote loaded

In the following example, Oracle ACFS remote service drivers and configuration are determined to be correct and running. However, there are no iSCSI transports currently configured, so iSCSI has not been started.

    #acfsremote loaded
    ACFS-9846: ACFS Remote loaded: True
    ACFS-9847: iSCSI loaded: False

### acfsremote supported

#### Purpose

Checks to ensure that your current node is supported for Oracle ACFS remote service.

#### Syntax and Description

    acfsremote supported -h
    acfsremote supported [-trace trace_level] [-member] [-domain]

The following table contains the options available with the `acfsremote` `supported` command.

Table 16-108 Options for the acfsremote supported command

| Option                 | Description                                           |
|:-----------------------|:------------------------------------------------------|
| `-trace` `trace_level` | Specifies the trace level.                            |
| `-member`              | Specifies to check the member cluster                 |
| `—domain`              | Specifies to check the Domain Services Cluster (DSC). |

`acfsremote` `supported` checks to ensure that your current node is supported for Oracle ACFS remote service.

This command is applicable on both member clusters and Domain Services Clusters (DSC).

Example 16-102 Using acfsremote supported

In this example, the node is supported for Oracle ACFS remote service with the correct kernels and package requirements, and also supported for the iSCSI transport.

    #acfsremote supported
    ACFS-9840: ACFS Remote supported: True
    ACFS-9841: iSCSI supported: True

### acfsutil cluster credential

#### Purpose

Generates, updates, or imports the Oracle ACFS remote service credentials.

#### Syntax and Description

    acfsutil cluster credential -h
    acfsutil cluster credential { [-n] |
                                  -l [cluster_name] [-n] |
                                  -g cluster_name -o cluster_manifest_file [-c version] |
                                  -r cluster_name [-f] |
                                  -s user_name:group_name |
                                  -i cluster_manifest_file
                                 }

The following table contains the options available with the `acfsutil` `cluster` `credential` command.

Table 16-109 Options for the acfsutil cluster credential command

| Option                                                         | Description                                                                                                                                                                                                 |
|:---------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-n`                                                           | Suppresses headers when listing registered member clusters.                                                                                                                                                 |
| `-l` \[`cluster_name`\]                                        | Lists registered member clusters. Optionally, include a cluster name to list only a specific cluster or include the `-n` flag to suppress the headers in the output.                                        |
| `-g` `cluster_name`-o `cluster_manifest_file` \[-c `version`\] | Generate the member cluster's credentials with specified name and export the credentials to the specified file. Optionally, add the `-c` flag to specify the version that the client cluster is running.    |
| `-r` `cluster_name`                                            | Deletes the credential for the specified cluster. Optionally, use `-f` to force the deletion.                                                                                                               |
| `-s` `user_name`:`group_name`                                  | Adds user_name and group_name to the credential file to enable permissions for access to Oracle ACFS remote service. The user_name and group_name must specify an existing operating system user and group. |
| `-i` `cluster_manifest_file`                                   | Import the credentials contained in the cluster_manifest_file.                                                                                                                                              |

`acfsutil` `cluster` `credential` generates or imports the Oracle ACFS remote service credentials. In most cases, this command is not directly called by an end user.

This command is applicable on all cluster types.

Example 16-103 Using acfsutil cluster credential

In the following example, `acfsutil` `cluster` `credential` sets up the OCR for Oracle ACFS remote service, and then imports an existing credential file into it.

    #/sbin/acfsutil cluster credential -s grid_user:asm_group
    #/sbin/acfsutil cluster credential –s grid2:oinstall
    #/sbin/acfsutil cluster credential -i my_credential_file

### acfsutil cluster info

#### Purpose

Displays information about the type of cluster and the internal information for the running cluster.

#### Syntax and Description

    acfsutil cluster info -h
    acfsutil cluster info

`acfsutil` `cluster` `info` displays information about the type of cluster and the internal information for the running cluster. The command can be used to ensure that the kernel Oracle ACFS cluster is in sync with Oracle ASM. This command is applicable on all cluster types.

Example 16-104 Using acfsutil cluster info

    # /sbin/acfsutil cluster info
    Node Count: 2
    Rebuild Master: 2
    Local Node: 1
    Current Incarnation: 10
    ACFS DLM Interfaces: ENABLED
    OKS DLM Interfaces: ENABLED
    Cluster State: [ NORMAL_OPERATION ]
    ACFS Remote mode: [DOMAIN SERVICES]
    ASM Storage mode: [LOCAL]
    Oracle Appliance: [NONAPP]
    Nodes:
    Node 1 - IP 10.0.0.2 – node1
    Node 2 - IP 10.0.0.3 - node2

The output from the `acfsutil` `cluster` `info` command includes the following information about the current cluster.

- Node Count: Number of nodes in the cluster.

  In this example, this is a 2–node cluster.

- Rebuild Master: Rebuild master node.

  In this example, node 2 is in charge of rebuilding the cluster.

- Current Incarnation: An incarnation is any significant membership change in the cluster.

  In this example, there have been 10 incarnations of the cluster.

- Cluster State: NORMAL_OPERATION, MIGRATION, UNKNOWN

  In this example, the cluster is operating normally.

- ACFS Remote mode:

  - MEMBER – a member cluster

  - DOMAIN SERVICES – a domain services cluster

    In this example, the ACFS remote mode is set to a domain services cluster,

  - OFF – a standalone cluster

- ASM Storage Mode:

  - LOCAL – the cluster has locally attached storage

    In this example, the ASM Storage mode is set to local attached storage.

  - REMOTE – the cluster is using storage served from a REMOTE Domain Services Cluster. REMOTE should only display when Oracle ACFS Remote mode is MEMBER.

### acfsutil remote clear

#### Purpose

Clears the Oracle ACFS remote attribute from a file.

#### Syntax and Description

    acfsutil remote clear -h
    acfsutil remote clear path_name

The following table contains the options available with the `acfsutil` `remote` `clear` command.

Table 16-110 Options for the acfsutil remote clear command

| Option      | Description                         |
|:------------|:------------------------------------|
| `path_name` | Specifies the location of the file. |

`acfsutil` `remote` `clear` clears the Oracle ACFS remote attribute from a file identified by the specified path name. Clearing the remote attribute allows the file on disk to be removed or truncated by a system administrator.

Example 16-105 Using acfsutil remote clear

    $ acfsutil remote clear my_remote_file

### acfsutil remote set

#### Purpose

Sets a file attribute as Oracle ACFS remote.

#### Syntax and Description

    acfsutil remote set -h
    acfsutil remote set path_name

The following table contains the options available with the `acfsutil` `remote` `set` command.

Table 16-111 Options for the acfsutil remote set command

| Option      | Description                         |
|:------------|:------------------------------------|
| `path_name` | Specifies the location of the file. |

`acfsutil` `remote` `set` sets the Oracle ACFS remote attribute on a file identified by the specified path name. Setting the remote attribute prevents the file on disk from being removed or truncated by a system administrator.

Example 16-106 Using the acfsutil remote set command

    $ acfsutil remote set my_remote_file

### advmutil export create

#### Purpose

Creates exports and allocates their initial storage.

#### Syntax and Description

    advmutil export create -h
    advmutil export create -n export_name -c cluster_name -p storage_repos {-s file_size | -f}

The following table contains the options available with the `advmutil` `export` `create` command.

Table 16-112 Options for the advmutil export create command

| Option               | Description                                                                                                                                                         |
|:---------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-n` `export_name`   | Specifies the export name.                                                                                                                                          |
| `-c` `cluster_name`  | Specifies the member cluster name.                                                                                                                                  |
| `-p` `storage_repos` | Specifies the location of the repository where the backing file is stored.                                                                                          |
| `-s` `file_size`     | Specifies the file size in the format n{K\|M\|G\|T\|P\|E}. The units are K (Kilobytes), M (Megabytes), G (Gigabytes), T (Terabytes), P (Petabytes) or E (Exabytes). |
| `-f`                 | Specifies to reuse an existing storage repository.                                                                                                                  |

`advmutil` `export` `create` manages the exports for a cluster. It is responsible for creating exports and allocating their initial storage. When creating an export, a fully-allocated (non-sparse) file is allocated for performance reasons.

When creating an export, the name provided with `-n` option also becomes the name of the volume on the member cluster. If `-n` `expvol1` is provided, then that would result in device `/dev/asm/expvol1-000` created on the member cluster.

The `-p` option must specify an Oracle ACFS file system for the storage repository. If an Oracle ACFS clusterware (CRS) resource exists, then it is modified to depend on any transport VIP resources registered to the cluster.

If the backing file already exists in a repository, then the `-f` option must be provided. After a backing file is created, Oracle ACFS lists it as in-use by Oracle ACFS remote service (with the `Remote` flag) and prevents various actions against the file.

Snapshots of exports are on the DSC only. Snapshots created on the member cluster of the Oracle ACFS file system mounted on the member cluster are accessible on the member cluster only.

This command is only applicable to the Domain Services Cluster (DSC).

Example 16-107 Using advmutil export create

In the following example, `export1` is created on `cluster1` with the repository located at `/repository1` and the size allocated is 512 M.

    #/sbin/advmutil export create -n export1 -c cluster1 -p /repository1 -s 512M
    Creating File Backed Volume.
    Export and backing store for volume 'export1' for cluster 'cluster1' created.

To use Oracle ACFS remote service repositories with Oracle ACFS snapshots of the DSC repository, some manual steps must be performed on the DSC. When snapping a DSC repository, all backing files in the repository are snapped.

In the following example, a snapshot is exported to the same member cluster.

1.  Create a backing file.

        #/sbin/advmutil export create -c mc1 -p /repo -n vol1 -s 2G

2.  Snap the backing file.

        $/sbin/acfsutil snap create -w snap1 /repo

3.  Create a snapshot link in the root of the repository:

         $/sbin/acfsutil snap link -s snap1 /repo/snap1_link

4.  Export the snap, using the -f option.

        #/sbin/advmutil export create -f -n vol1 -p /repo/snap1_link -c mc1

In the following example, a snapshot is exported to a different member cluster.

1.  Create a backing file.

        #/sbin/advmutil export create -c mc1 -p /repo -n vol1 -s 2G

2.  Snap the backing file.

        $/sbin/acfsutil snap create -w snap3 /repo

3.  Create a snapshot link in the root of the repository:

         $/sbin/acfsutil snap link -s snap3 /repo/snap3_link

4.  Use `ln` to link to the file from the new member cluster repository.

    Note that f903… is the GUID of the old member cluster and 54633… is the GUID of the new member cluster.

        $ln -sf /repo/54633dd2059d6f2cbff1217a6054564b/vol1 /repo/snap3_link/f9038b6ff0d64f36fff4d345803dfacd/vol1

5.  Add the new snapshot to the new member cluster.

        #/sbin/advmutil export create -f -n vol1 -p //repo/ -c mc2

### advmutil export list

#### Purpose

Displays information about exports and member clusters.

#### Syntax and Description

    advmutil export list -h
    advmutil export list [-c cluster_name] [-o options] [-g group_type] [-a] [-n]

The following table contains the options available with the `advmutil` `export` `list` command.

Table 16-113 Options for the advmutil export list command

| Option              | Description                                                                                                                                                                                  |
|:--------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-c` `cluster_name` | Specifies the name of the member cluster.                                                                                                                                                    |
| `-o` `options`      | Specifies an options list, comma separated, with no spaces. The options are clientDev,clusterGUID,clusterName,storageRepo,exportName,filePath,state,exportSize,active,domainNode, and minor. |
| `-g` `group_type`   | Specifies the group type by clusterName, clusterGUID, or storageRepo.                                                                                                                        |
| `-a`                | Displays only active exports.                                                                                                                                                                |
| `-n`                | Specifies not to print column headers.                                                                                                                                                       |

`advmutil` `export` `list` is a powerful query command for export management. It contains a default view that displays basic information, but can also be used to sort by different groups, and to display different pieces of information on different clusters.

By default, `advmutil` `export` `list` sorts by cluster name (the clusterName group sort option). Exports can also be sorted by storage repository (storageRepo) or by cluster GUID (clusterGUID).

The default view of the exports is meant to be easily readable with appropriate headers and informational queues. You can use the `-n` option to display all output on a single line with no headers so that the information can be used in a script.

The default view includes the clientDev option which displays the pathname to the device on the member cluster system. This default view can be provided to member cluster administrators to describe the information the administrators require to administer their systems.

This command is only applicable to the Domain Services Cluster (DSC).

Example 16-108 Using advmutil export list

The following example lists the export name, storage size, export minor, storage repository, and client ADVM volume device for the member cluster `cluster1`. Note the client ADVM volume device is displayed by default.

    #/sbin/advmutil export list -c cluster1 -o exportSize,minor,storageRepo
    clusterName: cluster1
    exportName storageSize exportMinor storageRepository  (client ADVM device)
    -------------------------------------------------------------------------
    exporta       512.00M          0   /repo              (/dev/asm/exporta-000)
    exportb       512.00M          1   /repo              (/dev/asm/exportb-001)
    exportc       512.00M          2   /repo              (/dev/asm/exportc-002)

### advmutil export lsof

#### Purpose

Lists active files for in repositories.

#### Syntax and Description

    advmutil export lsof -h
    advmutil export lsof [-p path] [-a]

The following table contains the options available with the `advmutil` `export` `lsof` command.

Table 16-114 Options for the advmutil export lsof command

| Option      | Description                                      |
|:------------|:-------------------------------------------------|
| `-p` `path` | Specifies the location of the directory or file. |
| `-a`        | Displays only active exports.                    |

`advmutil` `export` `lsof` shows active files for all repositories, or a specified file or directory in a single repository.

This command is only applicable to the Domain Services Cluster (DSC).

Example 16-109 Using advmutil export lsof

In the following example, the active files are displayed for the member cluster `cluster1`.

    #/sbin/advmutil export lsof
    EXPORT_NAME STATE    CLUSTER_NAME REPO_ID  REPO_PATH
    exporta     unknown  cluster1     45057_2  /repo
    exportb     unknown  cluster1     45057_2  /repo
    exportc     unknown  cluster1     45057_2  /repo

### advmutil export mapping

#### Purpose

Reexports all exports or only exports for a particular cluster.

#### Syntax and Description

    advmutil export mapping -h
    advmutil export mapping [-c cluster_name]

The following table contains the options available with the `advmutil` `export` `mapping` command.

Table 16-115 Options for the advmutil export mapping command

| Option              | Description                               |
|:--------------------|:------------------------------------------|
| `-c` `cluster_name` | Specifies the name of the member cluster. |

`advmutil` `export` `mapping` reexports all exports or only exports for a specified member cluster. It can be used to force Oracle ACFS remote service to reexport all configured exports in the event of a system administrator action that has removed access to a particular export.

This command is only applicable to the Domain Services Cluster (DSC).

Example 16-110 Using advmutil export mapping

In the following example, exports are reexported for the member cluster `cluster1`.

    #/sbin/advmutil export mapping -c cluster1

### advmutil export remove

#### Purpose

Removes the configuration metadata of an export.

#### Syntax and Description

    advmutil export remove -h
    advmutil export remove -c cluster_name [-p storage_repos -n export_name] [-f] [-b] [-y]

The following table contains the options available with the `advmutil` `export` `remove` command.

Table 16-116 Options for the advmutil export remove command

| Option               | Description                                                                |
|:---------------------|:---------------------------------------------------------------------------|
| `-c` `cluster_name`  | Specifies the member cluster name.                                         |
| `-p` `storage_repos` | Specifies the location of the repository where the backing file is stored. |
| `-n` `export_name`   | Specifies the export name.                                                 |
| `-f`                 | Forces removal whether or not export mapping is active.                    |
| `-b`                 | Removes the backing file for this mapping.                                 |
| `-y`                 | Does not prompt when removing the backing file for cluster.                |

`advmutil` `export` `remove` removes the configuration metadata of an export.

By default, the backing file remains after the removal operation. This file can be reused by running `advmutil` `export` `create` with the `-f` option. If the backing file is no longer required, then you can use the `-b` option to delete the backing file and return the storage space to the repository.

This command is only applicable to the Domain Services Cluster (DSC).

Example 16-111 Using advmutil export remove

In the following example, the metadata for `export1` is removed.

    #/sbin/advmutil export remove -c cluster1 -p /repository1 -n export1

### advmutil export resize

#### Purpose

Adds storage to the underlying backing file for an export.

#### Syntax and Description

    advmutil export resize -h
    advmutil export resize -c cluster_name -p storage_repos -n export_name -s file_size

The following table contains the options available with the `advmutil` `export` `resize` command.

Table 16-117 Options for the advmutil export resize command

| Option               | Description                                                                                                                                                         |
|:---------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-c` `cluster_name`  | Specifies the member cluster name.                                                                                                                                  |
| `-p` `storage_repos` | Specifies the location of the repository where the backing file is stored.                                                                                          |
| `-n` `export_name`   | Specifies the export name.                                                                                                                                          |
| `-s` `file_size`     | Specifies the file size in the format n{K\|M\|G\|T\|P\|E}. The units are K (Kilobytes), M (Megabytes), G (Gigabytes), T (Terabytes), P (Petabytes) or E (Exabytes). |

`advmutil` `export` `resize` adds storage to the underlying backing file for an export. After the backing file is grown, the device on the member cluster is also resized. To use the new size, an administrator must run `acfsutil` `size` on the member cluster mounted file system that is using the newly-sized device. Optionally, the new storage is used when needed if Oracle ACFS automatic resize functionality is configured on the mounted member cluster Oracle ACFS file system that is associated with this device.

To shrink a device, you must run `acfsutil` `size` on the member cluster to decrease the size of the file system. This action also shrinks the size of the associated backing file.

You can run `advmutil` `volinfo` on the member cluster to display the size of the underlying volume. However, this may be different than the size of the current Oracle ACFS file system that is using this device.

This command is only applicable to the Domain Services Cluster (DSC).

Example 16-112 Using advmutil export resize

In the following example, the size of the backing file for `export1` has been increased to 1 G.

    #/sbin/advmutil export resize -c cluster1 -p /repository1 -n export1 -s 1G

### advmutil session list

#### Purpose

Lists the current state and description of Oracle ACFS remote service sessions on the Oracle Database member cluster.

#### Syntax and Description

    advmutil session list -h
    advmutil session list [-n node_name] [[-i transport_id] [-v]]

The following table contains the options available with the `advmutil` `session` `list` command.

Table 16-118 Options for the advmutil session list command

| Option              | Description                                                                       |
|:--------------------|:----------------------------------------------------------------------------------|
| `-n` `node_name`    | Specifies the node name.                                                          |
| `-i` `transport_id` | Specifies the transport Id in the format `‘``transport_type``.``sequence_num``’`. |
| `-v`                | Displays verbose output, including XML data.                                      |

`advmutil` `session` `list` lists the current state and description of Oracle ACFS remote service sessions on the Oracle Database member cluster. This list is useful for debugging and informational purposes.

In the output of the command, the possible state value are:

- `ONLINE`

  Oracle ACFS remote service transport session is currently up and configured.

- `REFRESH`

  Oracle ACFS remote service transport session, that is associated with the configured transport of `‘``transport_type``.``sequence_num``’` on the DSC, is being refreshed. A refresh logs out of all existing targets and attempts to reinitialize the underlying operating system transport sessions associated with the Oracle ACFS remote service transport configuration.

- `RESCAN`

  Oracle ACFS remote service transport session is currently being scanned. The rescan process only removes operating system transport sessions that no longer exist, or adds new sessions that have been added. Existing sessions are not scanned.

The `advmutil` `session` `list` command only applies to the Oracle Database member cluster.

Example 16-113 Using advmutil session list

In the following example, session information is displayed for `Node1` and `Node2` on the member cluster.

    #/sbin/advmutil session list
    nodeName transportType sequenceNum state
    -----------------------------------------
    Node1    iSCSI                   0 ONLINE
    Node2    iSCSI                   0 ONLINE

### advmutil transport create

#### Purpose

Creates a transport on the Domain Services Cluster (DSC).

#### Syntax and Description

    advmutil transport create -h
    advmutil transport create -c cluster_name [-b binding [-n network_num ] | [-i resource_id] [-f]


The following table contains the options available with the `advmutil` `transport` `create` command.

Table 16-119 Options for the advmutil transport create command

| Option              | Description                                                               |
|:--------------------|:--------------------------------------------------------------------------|
| `-c` `cluster_name` | Specifies the member cluster name that the transport belongs to.          |
| `-b` `binding`      | Specifies the transport VIP, either the host name or the network address. |
| `-n` `network_num`  | Specifies the network number for the specified VIP. The default is `1`.   |
| `-i` `resource_id`  | Specifies an existing alternate resource identifier.                      |
| `-f`                | Forces the acceptance of the specified existing binding.                  |

`advmutil` `transport` `create` creates a transport on the Domain Services Cluster (DSC).

The cluster name can be discovered using the `crsctl` `query` `member_cluster_configuration` command. The transport VIP can be an IPv4 or IPv6 address, and can be either a resolvable DNS entry, or an IP address.

When creating a transport with additional features enabled, such as multipathing and failover, multiple transports must be enabled for a single member cluster. You can create multiple transports by running the `advmutil` `transport` `create` command multiple times, specifying additional VIP addresses.

Member clusters may share VIPs. You can accomplish this by specifying a common VIP name when registering a transport for a new member cluster. However, all member clusters must have the `advmutil` `transport` `create` command run at least once to specify their transport.

Transport IDs are created for each transport with the identifier of the form cluster_name_transport_type_sequence#, where n is an number starting from 0 and increased by 1 for each transport.

This command is only applicable on the Domain Services Cluster.

Example 16-114 Using advmutil transport create

In the following example, a transport is created for member cluster `cluster1` with VIP `havip1` using network `2`.

    #/sbin/advmutil transport create –c cluster1 –b havip1 –n 2

### advmutil transport list

#### Purpose

Displays the configured transports on the system.

#### Syntax and Description

    advmutil transport list [-h]
    advmutil transport list [-c cluster_name [-i transport_id] [-v]] | [-g cluster_guid [-i transport_id [-v]]]

The following table contains the options available with the `advmutil` `transport` `list` command.

Table 16-120 Options for the advmutil transport list command

| Option              | Description                                                                 |
|:--------------------|:----------------------------------------------------------------------------|
| `-c` `cluster_name` | Specifies the member cluster name that the transport belongs to.            |
| `-i` `transport_id` | Specifies the transport Id in the format `transport_type``.``sequence_num`. |
| `-g` `cluster_guid` | Specifies the cluster Globally Unique IDentifier (GUID).                    |
| `-v`                | Specifies verbose output including XML data.                                |

`advmutil` `transport` `list` displays the configured transports on the system. The command can be configured to display information about specific clusters using the `-c` or `-g` options, as well as displaying the full configuration output.

This command is only applicable on the Domain Services Cluster.

Example 16-115 Using advmutil transport list

In the following example, the output shows a single iSCSI transport configured with sequence number `0`.

    #/sbin/advmutil transport list
    clusterName: cluster1 (clusterGUID: f403401d0518ffcfff54324f2cc2f6d8)
    transportType sequenceNum
    -----------------------------------------------------------
    iSCSI                   0

Using the information in the output above, the sequence number (`0`) can be used on the member cluster to display information about a specific transport. Additionally, you can retrieve the full transport specification using the transport Id (`iSCSI.0`).

### advmutil transport remove

#### Purpose

Removes a transport.

#### Syntax and Description

    advmutil transport remove [-h]
    advmutil transport remove -c cluster_name -i transport_id

The following table contains the options available with the `advmutil` `transport` `remove` command.

Table 16-121 Options for the advmutil transport remove command

| Option              | Description                                                                 |
|:--------------------|:----------------------------------------------------------------------------|
| `-c` `cluster_name` | Specifies the member cluster name that the transport belongs to.            |
| `-i` `transport_id` | Specifies the transport Id in the format `transport_type``.``sequence_num`. |

`advmutil` `transport` `remove` removes a transport. This also removes any associated transport VIP resources if the transport is the last transport using this ID.

This command is only applicable on the Domain Services Cluster.

Example 16-116 Using advmutil transport remove

In the following example, the transport with transport Id `iSCSI.0` is removed from `cluster1`.

    #/sbin/advmutil transport remove -c cluster1 -I iSCSI.0
