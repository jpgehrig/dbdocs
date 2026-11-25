Use the `oclumon manage` command to view and change configuration information from the system monitor service.

### Syntax

    oclumon manage -repos {{changeretentiontime time} | {changerepossize memory_size}} | -get {key1 [key2 ...] | alllogger [-details] | mylogger [-details]}

### Parameters

Table B-14 oclumon manage Command Parameters

| Parameter                                                                     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|:------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-repos {{changeretentiontime ``time``} | {changerepossize ``memory_size``}}` | The `-repos` flag is required to specify the following Cluster Health Monitor repository-related options:<br>• `changeretentiontime ``time`: Use this option to confirm that there is sufficient tablespace to hold the amount of Cluster Health Monitor data that can be accumulated in a specific amount of time.<br>• Note: This option does not change retention time.<br>• `changerepossize ``memory_size`: Use this option to change the Cluster Health Monitor repository space limit to a specified number of MB<br>• Caution: If you decrease the space limit of the Cluster Health Monitor repository, then all data collected before the resizing operation is permanently deleted.                                        |
| `-get ``key1`` [``key2`` ...]`                                                | Use this option to obtain Cluster Health Monitor repository information using the following keywords:<br>• `repsize`: Size of the Cluster Health Monitor repository, in seconds<br>• `reppath`: Directory path to the Cluster Health Monitor repository<br>• `master`: Name of the master node<br>• `alllogger`: Special key to obtain a list of all nodes running Cluster Logger Service<br>• `mylogger`: Special key to obtain the node running the Cluster Logger Service which is serving the current node<br>• `-details`: Use this option with `alllogger` and `mylogger` for listing nodes served by the Cluster Logger Service<br>You can specify any number of keywords in a space-delimited list following the `-get` flag. |
| `-h`                                                                          | Displays online help for the `oclumon manage` command                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |

### Usage Notes

- The local system monitor service must be running to change the retention time of the Cluster Health Monitor repository.

- The Cluster Logger Service must be running to change the retention time of the Cluster Health Monitor repository.

Example B-6 oclumon manage

The following examples show commands and sample output:

    $ oclumon manage -get MASTER
    Master = node1

    $ oclumon manage -get alllogger -details
    Logger = node1
    Nodes = node1,node2

    $ oclumon manage -repos changeretentiontime 86400

    $ oclumon manage -repos changerepossize 6000

**Parent topic:** [OCLUMON Command Reference](oclumon-command-reference.md)
