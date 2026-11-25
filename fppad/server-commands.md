## server Commands

Use commands with the `server` keyword to export, register, unregister, and query Oracle Fleet Patching and Provisioning Server.

- rhpctl export server
  Exports data from the repository to a Fleet Patching and Provisioning Server data file.
- rhpctl query server
  Displays the configuration of a server.
- rhpctl register server
  Registers the specific Fleet Patching and Provisioning Server as a peer server.
- rhpctl unregister server
  Unregisters a specific Fleet Patching and Provisioning Server as a peer server.

**Parent topic:** [RHPCTL Command Reference](rhpctl-command-reference.md)

### rhpctl export server

Exports data from the repository to a Fleet Patching and Provisioning Server data file.

#### Syntax

    rhpctl export server -server peer_server_name -serverdata file_path

#### Usage Notes

- Specify the name of a peer server cluster.

- Specify the path to the file containing the Fleet Patching and Provisioning Server data.

**Parent topic:** server Commands

### rhpctl query server

Displays the configuration of a server.

#### Syntax

    rhpctl query server

#### Usage Notes

This command has no parameters.

#### Example

This command displays output similar to the following:

    $ rhpctl query server

    Fleet Patching and Provisioning Server (RHPS): rhps-myserver
    Storage base path: /u01/app/RHPImages
    Disk Groups: RHPDATA
    Port number: 8896

**Parent topic:** server Commands

### rhpctl register server

Registers the specific Fleet Patching and Provisioning Server as a peer server.

#### Syntax

    rhpctl register server -server server_cluster_name -serverdata file
      {-root | -cred cred_name | -sudouser sudo_username -sudopath path_to_sudo_binary
       | -auth plugin_name [-arg1 name1:value1 [-arg2 name2:value2 ...]]}

#### Parameters

Table A-57 rhpctl register server Command Parameters

| Parameter                                                                                                                             | Description                                                                                                                                                                                                                                                                                                                                                                                   |
|:--------------------------------------------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-server ``server_cluster_name`                                                                                                       | Specify the name of the Fleet Patching and Provisioning Server cluster that you want to register.                                                                                                                                                                                                                                                                                             |
| `-serverdata ``file`                                                                                                                  | Specify the path to the file containing the Fleet Patching and Provisioning Server data.                                                                                                                                                                                                                                                                                                      |
| `-root | -cred ``cred_name`` | -sudouser ``sudo_user_name`` -sudopath ``sudo_binary_location`` | -auth ``plugin_name`` ``plugin_args` | Choose `-root` to perform super user operations as `root`. Alternatively, you can choose either to specify a credential name to associate the user name and password credentials to access a remote node, to perform super user operations as a `sudo` user by specifying a `sudo` user name and the path to the `sudo` binary, or to use an authentication plugin to access the remote node. |

**Parent topic:** server Commands

### rhpctl unregister server

Unregisters a specific Fleet Patching and Provisioning Server as a peer server.

#### Syntax

    rhpctl unregister server -server server_cluster_name [-force]

#### Usage Notes

- Specify the name of the Fleet Patching and Provisioning Server you want to unregister as a peer.
- Optionally, you can use the `-force` parameter to forcibly unregister the server.

**Parent topic:** server Commands
