## client Commands

Use commands with the `client` keyword to add, delete, and manage Oracle Fleet Patching and Provisioning clients.

- rhpctl add client
  Adds a Fleet Patching and Provisioning Client to the Fleet Patching and Provisioning Server configuration.
- rhpctl delete client
  Deletes a specific Fleet Patching and Provisioning Client from the configuration.
- rhpctl discover client
  Validates the input provided and discovers parameters on the given nodes, and generates a response file that you can use for configuring Oracle Clusterware.
- rhpctl export client
  Exports data from the repository on the Fleet Patching and Provisioning Server to a client data file.
- rhpctl modify client
  Modifies a Fleet Patching and Provisioning Client.
- rhpctl query client
  Displays the configuration information of a specific Fleet Patching and Provisioning Client cluster.
- rhpctl update client
  Updates an image on the Fleet Patching and Provisioning Client.
- rhpctl verify client
  Validates the input provided and creates or completes and verifies the values in a response file that you can use to configure Oracle Clusterware.

**Parent topic:** [RHPCTL Command Reference](rhpctl-command-reference.md)

### rhpctl add client

Adds a Fleet Patching and Provisioning Client to the Fleet Patching and Provisioning Server configuration.

#### Syntax

    rhpctl add client -client cluster_name [-toclientdata path] [-targetnode node_name
      {-sudouser sudo_user_name -sudopath sudo_binary_location | -root |
      -cred cred_name} | -auth plugin_name [-arg1 name1:value1...]]
      [-maproles role=user_name[,role=user_name[,...]]]
      [-version version]

#### Parameters

Table A-2 rhpctl add client Command Parameters

| Parameter                                                                                     | Description                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:----------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-client ``client_name`                                                                       | Specify the name of the cluster in which you want to create the client.                                                                                                                                                                                                                                                                                                                                                                  |
| `-toclientdata ``path`                                                                        | Optionally, you can specify the path to the XML file that is created by the Fleet Patching and Provisioning Server (specific to the client cluster), which contains the information the client needs to configure its connection to the server.                                                                                                                                                                                          |
| `-targetnode ``node_name`                                                                     | Optionally, you can specify the name of a node in a remote cluster that has no Fleet Patching and Provisioning Client.                                                                                                                                                                                                                                                                                                                   |
| `-sudouser ``sudo_user_name`` -sudopath ``sudo_binary_location`` | -root | -cred ``cred_name` | If you choose to use the `-targetnode` parameter, then you must choose either `sudo` or `root` to access the remote node.<br>If you choose `sudo`, then you must use the `–sudouser` parameter and specify a user name to run super-user operations, and a path to the location of the `sudo` binary.<br>Optionally, you can choose to specify a credential name to associate the user and password credentials to access a remote node. |
| `-auth ``plugin_name`` [-arg1 ``name1``:``value1``...]`                                       | Alternative to `–sudouser`, `–root`, or `–cred`, you can use `–auth` to specify an authentication plugin to access a remote node.                                                                                                                                                                                                                                                                                                        |
| `-maproles ``role``=``user_name``[,...]`                                                      | You can specify either built-in roles or roles that you have defined, and you can assign multiple uses to each role. Use commas to separate multiple roles and users.                                                                                                                                                                                                                                                                    |
| `-version ``version`                                                                          | Optionally, you can specify the Oracle FPP Client software version, such as `19.0`.<br>**Note:**<br>If the Oracle FPP Client version is lower than the Oracle FPP Server version, then you must specify this parameter. For example, if the client version is 12.2, then specify the -version parameter as -version 12.2.                                                                                                                |

#### Usage Notes

- Only clusters running Oracle Grid Infrastructure 12c release 2 (12.2) or later can be configured and added as Fleet Patching and Provisioning Clients. Clusters running earlier versions of Oracle Grid Infrastructure, and servers running no Oracle Grid Infrastructure, can be managed directly by the Fleet Patching and Provisioning Server.

- You can only run this command on the Fleet Patching and Provisioning Server.

#### Examples

To add a client to the Fleet Patching and Provisioning Server:

    $ rhpctl add client -client ClientCluster3 -toclientdata Grid_home/RHPserver/info

**Parent topic:** client Commands

### rhpctl delete client

Deletes a specific Fleet Patching and Provisioning Client from the configuration.

#### Syntax

    rhpctl delete client –client cluster_name [-force]

#### Usage Notes

- Specify the name of the client cluster that you want to delete from the configuration.

- You must stop the Fleet Patching and Provisioning Client before you run this command or use the `-force` option.

#### Example

To delete the Fleet Patching and Provisioning Client `ClientCluster3`:

    $ rhpctl delete client -client ClientCluster3

**Parent topic:** client Commands

### rhpctl discover client

Validates the input provided and discovers parameters on the given nodes, and generates a response file that you can use for configuring Oracle Clusterware.

After completing this command, use to validate the response file and prepare the destination nodes for Oracle Clusterware deployment.

#### Syntax

    rhpctl discover client -image image_name -generatepath response_file_path
      {-responsefile response_file_name | -clusternodes node_list -client cluster_name
       -oraclehome oracle_home_path} {-root | -sudouser sudo_username
       -sudopath sudo_binary_path | -cred cred_name | -auth plugin_name
      [-arg1 name1:value1...]} [-user gi_user_name]
      [-scan scan_name]

#### Parameters

Table A-3 rhpctl discover client Command Parameters

| Parameter                                                                                                                                          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|:---------------------------------------------------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-image ``image_name`                                                                                                                              | Specify the name of the Oracle Grid Infrastructure Gold Image which the resulting response file will support.                                                                                                                                                                                                                                                                                                                                                                         |
| `-generatepath ``response_file_path`                                                                                                               | Specify a file path where the response file that RHPCTL generates will be copied. The RHPCTL command generates name of the response file and displays it while the command is running.                                                                                                                                                                                                                                                                                                |
| `-responsefile ``response_file_name`                                                                                                               | If you have a partially complete response file and you want it to be completed with reference to the destination nodes, then specify the response file name using this parameter.<br>Note: The response file must include the node list, client name, and Oracle home path.                                                                                                                                                                                                           |
| `-clusternodes ``node_list`                                                                                                                        | Specify a comma-delimited list of nodes on which you plan to provision Oracle Clusterware (using the resulting response file) in the following format: `node_name``:``node_vip``[:``node_role``][,``node_name``:``node_vip``[:``node_role``]...]`                                                                                                                                                                                                                                     |
| `-client ``cluster_name`                                                                                                                           | Specify the name of the Oracle FPP Client cluster to be probed.                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `-oraclehome ``oracle_home_path`                                                                                                                   | Specify the location of the Oracle home.                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-root | -sudouser ``sudo_username`` -sudopath ``sudo_binary_path`` | -cred ``cred_name`` | -auth ``plugin_name`` [-arg1 ``name1``:``value1``...]` | You must choose either `sudo` or `root` to access the remote nodes.<br>If you choose `sudo`, then you must specify a user name to run super-user operations, and a path to the location of the `sudo` binary.<br>Optionally, you can choose to specify a credential name to associate the user and password credentials to access a remote node.<br>Alternative to `–sudouser`, `–root`, or `–cred`, you can use `–auth` to specify an authentication plugin to access a remote node. |
| `-user ``gi_user_name`                                                                                                                             | Specify the name of the Oracle Grid Infrastructure installation user.                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-scan ``scan_name`                                                                                                                                | Specify the SCAN name.                                                                                                                                                                                                                                                                                                                                                                                                                                                                |

**Parent topic:** client Commands

### rhpctl export client

Exports data from the repository on the Fleet Patching and Provisioning Server to a client data file.

#### Syntax

    rhpctl export client -client cluster_name -clientdata file_path

#### Parameters

Table A-4 rhpctl export client Command Parameters

| Parameter                 | Description                                                     |
|:--------------------------|:----------------------------------------------------------------|
| `-client ``cluster_name`  | Specify the name of the client cluster that you want to export. |
| `-clientdata ``file_path` | Specify the path to the location of the client data file.       |

#### Usage Notes

You can only run this command on the Fleet Patching and Provisioning Server.

#### Example

To export repository data from a Fleet Patching and Provisioning Client named `mjk9394` to a client data file, `/tmp/mjk9394.xml`:

    $ rhpctl export client -client mjk9394 -clientdata /tmp/mjk9394.xml

**Parent topic:** client Commands

### rhpctl modify client

Modifies a Fleet Patching and Provisioning Client.

#### Syntax

    rhpctl modify client –client cluster_name [-enabled {TRUE | FALSE}]
      [-maproles role=user_name[+user_name...][,role=user_name[+user_name...],...]]] [-password]]

#### Parameters

Table A-5 rhpctl modify client Command Parameters

| Parameter                                                   | Description                                                                                                                                                                                                                                                                         |
|:------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-client cluster_name`                                      | Specify the name of the client cluster that you want to modify.                                                                                                                                                                                                                     |
| `-enabled {TRUE | FALSE}`                                   | Specify whether the client is enabled.                                                                                                                                                                                                                                              |
| `-maproles ``role``=``user_name``[+``user_name``...][,...]` | You can modify either built-in roles or roles that you have defined, and you can assign multiple uses to each role.<br>When you use the `-maproles` parameter, use a plus sign (`+`) to map more than one user to a specific role. Separate additional role/user pairs with commas. |
| `-password`                                                 | Optionally, you can specify a password to recreate the Fleet Patching and Provisioning Client credentials.                                                                                                                                                                          |

#### Example

To disable a Fleet Patching and Provisioning Client named `RHPClient001`:

    $ rhpctl modify client -client RHPClient001 -enabled FALSE

**Parent topic:** client Commands

### rhpctl query client

Displays the configuration information of a specific Fleet Patching and Provisioning Client cluster.

#### Syntax

    rhpctl query client [–client cluster_name]

#### Usage Notes

Specify the name of the client cluster in which the Fleet Patching and Provisioning Client resides for which you want to display the configuration information

#### Example

This command displays output similar to the following:

    /rhpctl query client -client mbcluster-13
    Site: mbcluster-13
    Fleet Patching and Provisioning Client Version: 12.2.0.1.0
    Enabled: true
    Host from which RHPC last registered: rhpserver01.example.com
    Port number last registered by RHPC: 8896
    RHP Enabled: true
    Standalone: false
    Managed: true

**Parent topic:** client Commands

### rhpctl update client

Updates an image on the Fleet Patching and Provisioning Client.

#### Syntax

    rhpctl update client -image image_name {-targetnode node_name
      | -batches '(node_name)'} -root

#### Parameters

Table A-6 rhpctl update client Command Parameters

| Parameter                    | Description                                                                                                                                                                                                                                                                                                                     |
|:-----------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-image ``image_name`        | Specify the name of the image that you want to update.                                                                                                                                                                                                                                                                          |
| `-targetnode ``node_name`    | Specify the name of the node on which you want to update the Fleet Patching and Provisioning Client.                                                                                                                                                                                                                            |
| `-batches '(``node_name``)'` | Alternative to specifying a node name, you can specify batches of nodes.<br>Note: If you use this parameter for Oracle Database Appliance nodes, then run the command twice, in succession, specifying any one Oracle Database Appliance node for the first run, and another Oracle Database Appliance node for the second run. |
| `–root`                      | You must specify this parameter if you use either the `–targetnode` or `–batches` parameters.                                                                                                                                                                                                                                   |

#### Usage Notes

You can only run this command from a Fleet Patching and Provisioning Server.

#### Examples

The following example uses the `–targetnode` parameter:

    $ rhpctl update client -image ODA1 -targetnode rac07box1 -root

The two following examples use the `–batches` parameter:

    $ rhpctl update client -image ODA1 -batches '(rac07box1)' -root
    $ rhpctl update client -image ODA1 -batches '(rac07box2)' -root

**Parent topic:** client Commands

### rhpctl verify client

Validates the input provided and creates or completes and verifies the values in a response file that you can use to configure Oracle Clusterware.

#### Syntax

    rhpctl verify client -image image_name -responsefile response_file_name
      [-clusternodes node_list] {-root | -sudouser sudo_username -sudopath
       sudo_binary_path | -cred cred_name} | -auth plugin_name [-arg1 name1:value1...]
      [-user gi_user_name] [-client cluster_name] [-scan scan_name]
      [-oraclehome oracle_home_path] [-ignorewarn] [-fixup [-setupSSH]]

#### Parameters

Table A-7 rhpctl verify client Command Parameters

| Parameter                                                                                                                                          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|:---------------------------------------------------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-image ``image_name`                                                                                                                              | Specify the name of the image.                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `-responsefile ``response_file_name`                                                                                                               | Specify a response file to be used to provision Oracle Grid Infrastructure.                                                                                                                                                                                                                                                                                                                                                                                                           |
| `-clusternodes ``node_list`                                                                                                                        | Specify a comma-delimited list of nodes on which Oracle Clusterware will be provisioned in the following format: `node_name``:``node_vip``[:``node_role``][,``node_name``:``node_vip``[:``node_role``]...]`                                                                                                                                                                                                                                                                           |
| `-root | -sudouser ``sudo_username`` -sudopath ``sudo_binary_path`` | -cred ``cred_name`` | -auth ``plugin_name`` [-arg1 ``name1``:``value1``...]` | You must choose either `sudo` or `root` to access the remote nodes.<br>If you choose `sudo`, then you must specify a user name to run super-user operations, and a path to the location of the `sudo` binary.<br>Optionally, you can choose to specify a credential name to associate the user and password credentials to access a remote node.<br>Alternative to `–sudouser`, `–root`, or `–cred`, you can use `–auth` to specify an authentication plugin to access a remote node. |
| `-user ``gi_user_name`                                                                                                                             | Specify the name of the Oracle Grid Infrastructure installation user.                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-client ``cluster_name`                                                                                                                           | Specify the name of the cluster you want to verify.                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `-scan ``scan_name`                                                                                                                                | Specify the SCAN name.                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `-oraclehome ``oracle_home_path`                                                                                                                   | Specify the location of the Oracle home.                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-ignorewarn`                                                                                                                                      | Use this parameter to ignore warnings during validation.                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `–fixup [-setupSSH]`                                                                                                                               | Use this parameter to run a fixup script, which automatically applies changes to the nodes to satisfy changes that CVU recommends.<br>Optionally, you can use the `-setupSSH` parameter to set up passwordless SSH user equivalence on the remote nodes for the provisioning user.                                                                                                                                                                                                    |

**Parent topic:** client Commands
