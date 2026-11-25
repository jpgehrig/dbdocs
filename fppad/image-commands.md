## image Commands

Use commands with the `image` keyword to add, delete, import, and manage gold images.

- rhpctl add image
  Use the `rhpctl add image` command to create an image from an existing working copy and add it to the list of existing images on the Fleet Patching and Provisioning Server configuration.
- rhpctl allow image
  Allows access to an image by a user or a role.
- rhpctl delete image
  Deletes a specific image.
- rhpctl deploy image
  Deploys an image to a specific node in a client cluster.
- rhpctl disallow image
  Disallows access to an image by a user or a role.
- rhpctl import image
  Creates an image on the Fleet Patching and Provisioning Server.
- rhpctl instantiate image
  Requests copies of gold images from a peer Fleet Patching and Provisioning Server.
- rhpctl modify image
  Modifies the configuration details of an image.
- rhpctl query image
  Displays the configuration of an existing image.
- rhpctl promote image
  Promotes an image.
- rhpctl register image
  Registers an image metadata to the Oracle FPP repository.
- rhpctl uninstantiate image
  Stops updates for previously requested images from a peer Fleet Patching and Provisioning Server.

**Parent topic:** [RHPCTL Command Reference](rhpctl-command-reference.md)

### rhpctl add image

Use the `rhpctl add image` command to create an image from an existing working copy and add it to the list of existing images on the Fleet Patching and Provisioning Server configuration.

#### Syntax

    rhpctl add image -image image_name -workingcopy working_copy_name
       [-imagetype image_type] [-series series_name] [-state {TESTABLE | RESTRICTED | PUBLISHED}]

#### Parameters

Table A-25 rhpctl add image Command Parameters

| Command Option                               | Description                                                                                                                                                                                                                                                                                                                                                   |
|:---------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-image ``image_name`                        | Specify the name of the image that you want to add.                                                                                                                                                                                                                                                                                                           |
| `-workingcopy ``working_copy_name`           | Specify the name of the working copy from which to create the image.<br>**Note:**<br>The working copy must be stored on ACFS storage for this command to work. Oracle FPP returns an error if the working copy is stored on a local storage device.                                                                                                           |
| `-imagetype ``image_type`                    | Specify the software type. `ORACLEDBSOFTWARE` (default) for Oracle Database software, `ORACLEGISOFTWARE` for Oracle Grid Infrastructure software, `ORACLEGGSOFTWARE` for Oracle GoldenGate software, `LINUXOS` for Linux operating system ISO, or `SOFTWARE` for all other software. If you use custom image types, then specify the name of your image type. |
| `-series ``series_name`                      | If you want to add an image to an image series, then specify the name of an image series.                                                                                                                                                                                                                                                                     |
| `-state {TESTABLE | RESTRICTED | PUBLISHED}` | Specify the state of the image.                                                                                                                                                                                                                                                                                                                               |

#### Usage Notes

**See Also:**

[Patching Oracle Database](patching-oracle-database.md) for details about how to use this command in the workflow for creating patched Oracle Database software homes

#### Example

An example of this command is:

    $ rhpctl add image -image DB12201_PATCH -workingcopy temp_wcpy_db12201_patch

**Parent topic:** image Commands

### rhpctl allow image

Allows access to an image by a user or a role.

#### Syntax

    rhpctl allow image -image image_name {-user user_name [-client cluster_name]
        | -role role_name}

#### Parameters

Table A-26 rhpctl allow image Command Parameters

| Parameter                                                           | Description                                                                                                                                                                                                                            |
|:--------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-image ``image_name`                                               | Specify the name of the image to which you want to allow access.                                                                                                                                                                       |
| `-user ``user_name`` [-client ``cluster_name`` | -role ``role_name` | Specify the either of the following:<br>• A user for which you want to allow access to the image and, optionally, the cluster name of the client cluster with the user.<br>• The role for which you want to allow access to the image. |

#### Examples

To allow access to an image named PRODIMAGE:

    $ rhpctl allow image -image PRODIMAGE -user mjk -client GHC1

**Parent topic:** image Commands

### rhpctl delete image

Deletes a specific image.

#### Syntax

    rhpctl delete image -image image_name [-schedule timer_value]

#### Usage Notes

- Specify the name of the image you want to delete

- Optionally, you can use the `-schedule` parameter to schedule a time to run this operation, in ISO-8601 format, as in the following example:
      2018-07-25T19:13:17+05

  If you choose to use this parameter, then you must run this command on the Fleet Patching and Provisioning Server.

- This command will fail if the image belongs to one or more series

- This command will fail if there are any provisioned working copies based on this image

#### Example

The following example deletes an image named PRODIMAGEV0:

    $ rhpctl delete image -image PRODIMAGEV0

**Parent topic:** image Commands

### rhpctl deploy image

Deploys an image to a specific node in a client cluster.

#### Syntax

    rhpctl deploy image -image image_name -path path_to_dir [-targetnode node_name {-root
        | -cred cred_name | -sudouser sudo_username -sudopath path_to_sudo_binary | -auth plugin_name
        [-arg1 name1:value1 [-arg2 name2:value2 ...]]}] [-client cluster_name]

#### Parameters

Table A-27 rhpctl deploy image Command Parameters

| Parameter                                                                                                                             | Description                                                                                                                                                                                                                                                                                                                                                                                   |
|:--------------------------------------------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-image ``image_name`                                                                                                                 | Specify the name of the image you want to deploy.                                                                                                                                                                                                                                                                                                                                             |
| `-path`                                                                                                                               | Specify the absolute location where you want to deploy the image.                                                                                                                                                                                                                                                                                                                             |
| `-targetnode ``node_name`                                                                                                             | Optionally, you can specify the name of a node to which you want to deploy the image. This parameter is required if the node hosting the home is not a Fleet Patching and Provisioning Client.                                                                                                                                                                                                |
| `-root | -cred ``cred_name`` | -sudouser ``sudo_user_name`` -sudopath ``sudo_binary_location`` | -auth ``plugin_name`` ``plugin_args` | Choose `-root` to perform super user operations as `root`. Alternatively, you can choose either to specify a credential name to associate the user name and password credentials to access a remote node, to perform super user operations as a `sudo` user by specifying a `sudo` user name and the path to the `sudo` binary, or to use an authentication plugin to access the remote node. |
| `-client`                                                                                                                             | Optionally, you can specify the name of the client cluster.                                                                                                                                                                                                                                                                                                                                   |

#### Usage Notes

You can only run this command from a Fleet Patching and Provisioning Server.

#### Example

The following example deploys an Oracle Database Appliance image to a node:

    $ rhpctl deploy image -image ODA1 -path /u01/app/dbusr/product/19.0.0/db19c -targetnode racgbox1 -root

**Parent topic:** image Commands

### rhpctl disallow image

Disallows access to an image by a user or a role.

#### Syntax

    rhpctl disallow image -image image_name {-user user_name [-client client_name]
        | -role role_name}

#### Parameters

Table A-28 rhpctl disallow image Command Parameters

| Parameter                                                          | Description                                                                                                                                                                                                                              |
|:-------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-image ``image_name`                                              | Specify the name of the image to which you want to disallow access.                                                                                                                                                                      |
| `-user ``user_name`` [-client ``client_name`` | -role ``role_name` | Specify either of the following:<br>• A user for which you want to disallow access to the image and, optionally, the cluster name of the client cluster with the user.<br>• The role for which you want to disallow access to the image. |

#### Examples

To disallow access to an image:

    $ rhpctl disallow image -image PRODIMAGE -user mjk -client GHC1

**Parent topic:** image Commands

### rhpctl import image

Creates an image on the Fleet Patching and Provisioning Server.

Use the `rhpctl import image` command to create an image by copying the entire software contents from the specified path to the Fleet Patching and Provisioning Server.

#### Syntax

    rhpctl import image -image image_name {-path path | -zip zipped_home_path |
       -location zipped_home_path} [-imagetype image_type] [-version software_version]
       [-pathowner user_name] [-state {TESTABLE | RESTRICTED | PUBLISHED}] [-client cluster_name]
       [-targetnode node_name [-sudouser sudo_user_name -sudopath sudo_binary_path | -root]]
       [-useractiondata user_action_data] [-schedule timer_value]

#### Parameters

Table A-29 rhpctl import image Command Parameters

| Parameter                                                              | Description                                                                                                                                                                                                                                                                                                                                                          |
|:-----------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-image ``image_name`                                                  | Specify the name of the image that you want to add.                                                                                                                                                                                                                                                                                                                  |
| `-path ``path`                                                         | Specify the absolute path location of the software home that you want to import (for Oracle Database images, this is the `ORACLE_HOME`).                                                                                                                                                                                                                             |
| `-zip ``zipped_home_path`                                              | Specify the absolute path of the compressed software home to be imported (a ZIP or TAR file).<br>**Note:**<br>Do not use this option when importing an image from another platform. This option works only on the same platform, for example, if you are on a Linux platform, then you can use the `-zip` option to import an image only from another Linux system.  |
| `-location ``zipped_home_path`                                         | Specify the location of the compressed image file on the target.                                                                                                                                                                                                                                                                                                     |
| `-imagetype ``image_type`                                              | Specify the software type. Use `ORACLEDBSOFTWARE` (default) for Oracle database software, `ORACLEGGSOFTWARE` for Oracle GoldenGate software, `ORACLEGISOFTWARE` for Oracle Grid Infrastructure software, `ODAPATCHSOFTWARE`, for engineered systems (Oracle Data Appliance), or `SOFTWARE` for all other software. For a custom image type, use the image type name. |
| `-version ``software_version`                                          | Optionally, you can specify the version of the software you are importing.                                                                                                                                                                                                                                                                                           |
| `-pathowner ``user_name`                                               | Specify the user with read access to the files and directories under the specified path.<br>Note: This parameter is applicable only for non-Oracle database software homes.                                                                                                                                                                                          |
| `-state {TESTABLE | RESTRICTED | PUBLISHED`                            | Specify whether the state of the image is testable, restricted, or published.                                                                                                                                                                                                                                                                                        |
| `-client ``cluster_name`                                               | Specify the name of the client cluster.                                                                                                                                                                                                                                                                                                                              |
| `-targetnode ``node_name`                                              | Specify the name of the node from which you want to import the image. This parameter is required if the node hosting the home is not an Fleet Patching and Provisioning Client.                                                                                                                                                                                      |
| `-sudouser ``sudo_user_name`` -sudopath ``sudo_binary_path`` | -root]` | If you use the `-targetnode` parameter, then you must specify either sudo or `root` to perform super user operations.                                                                                                                                                                                                                                                |
| `-useractiondata ``user_action_data`                                   | Optionally, you can pass a value to the `useractiondata` parameter of the user action script.                                                                                                                                                                                                                                                                        |
| `-schedule ``timer_value`                                              | Optionally, you can use this parameter to schedule a time to run this operation, in ISO-8601 format, as in the following example:<br>`2018-07-25T19:13:17+05`                                                                                                                                                                                                        |

#### Usage Notes

- You can only run this command on a Fleet Patching and Provisioning Server.

- When you import an Oracle Database or Oracle Grid Infrastructure software home, the version of the home must be one of the versions that Fleet Patching and Provisioning supports for provisioning and patching.

#### Examples

The following example imports an image:

    $ rhpctl import image -image PRODIMAGEV1 -path /u01/app/product/12.1.0/dbhome -pathowner orcl

The following example imports an engineered system image:

    $ rhpctl import image -image ODA1 -imagetype ODAPATCHSOFTWARE -path /tmp/ODAPatchBundle -version 12.1.2.8.0

**Parent topic:** image Commands

### rhpctl instantiate image

Requests copies of gold images from a peer Fleet Patching and Provisioning Server.

#### Syntax

    rhpctl instantiate image -server server_cluster_name {-image image_name
      | -series series_name | -imagetype image_type | -all}

#### Parameters

Table A-30 rhpctl instantiate image Command Parameters

| Parameter                                                                            | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|:-------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-server ``server_cluster_name`                                                      | Specify a Fleet Patching and Provisioning Server cluster from which you want to request images.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-image ``image_name`` | -series ``series_name`` | -imagetype ``image_type`` | -all` | You can request copies of gold images from a peer Fleet Patching and Provisioning Server, specifically, by image name, series name, or image type. Alternatively, you can use the `-all` parameter to request copies of all gold images from the peer Fleet Patching and Provisioning server.<br>If you choose to request images by image type, then specify `ORACLEDBSOFTWARE` (default) for Oracle Database software, `ORACLEGISOFTWARE` for Oracle Grid Infrastructure software, `ORACLEGGSOFTWARE` for Oracle GoldenGate software, and `SOFTWARE` for all other software. For a custom image type, use the image type name. |

#### Usage Notes

- User actions associated with an image being copied are not themselves copied.

- Groups configuration of a gold image is replicated in copies sent to peers.

- Copies of gold images are in the PUBLISHED state.

**Parent topic:** image Commands

### rhpctl modify image

Modifies the configuration details of an image.

#### Syntax

    rhpctl modify image -image image_name -imagetype image_type

#### Parameters

Table A-31 rhpctl modify image Command Parameters

| Parameter                 | Description                                                                                                                                                                                                                                                                                             |
|:--------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-image ``image_name`     | Specify the name of the image that you want to modify.                                                                                                                                                                                                                                                  |
| `-imagetype ``image_type` | You can modify the software type. Use `ORACLEDBSOFTWARE` (default) for Oracle database software, `ORACLEGISOFTWARE` for Oracle Grid Infrastructure software, `ORACLEGGSOFTWARE` for Oracle GoldenGate software, or `SOFTWARE` for all other software. For a custom image type, use the image type name. |

**Parent topic:** image Commands

### rhpctl query image

Displays the configuration of an existing image.

#### Syntax

    rhpctl query image {[[-image image_name [-dbtemplate]] | [[-imagetype image_type]
      [-version version] [-platform platform] [-drift] ]]}

#### Parameters

Table A-32 rhpctl query image Command Parameters

| Parameter                             | Description                                                                                                                                                                                                                                                                                     |
|:--------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-image ``image_name`` [-dbtemplate]` | Specify the name of the image you want to query.<br>Optionally, you can use the `-dbtemplate` parameter to display template file names in the default template directory.                                                                                                                       |
| `-imagetype ``image_type`             | Specify the software type. Use `ORACLEDBSOFTWARE` (default) for Oracle database software, `ORACLEGISOFTWARE` for Oracle Grid Infrastructure software, `ORACLEGGSOFTWARE` for Oracle GoldenGate software,or `SOFTWARE` for all other software. For a custom image type, use the image type name. |
| `–version ``version`                  | Use this parameter to specify the version of the image software you are querying.                                                                                                                                                                                                               |
| `-platform ``platform`                | Use this parameter to specify the operating system platform to which the image corresponds.                                                                                                                                                                                                     |
| `-drift`                              | List the the bug fixes not included in the golden image.                                                                                                                                                                                                                                        |

#### Usage Notes

- If you use the `-version` parameter, then the version must have five fields, such as 12.1.0.2.4.

- If you use the -platform parameter, then you can use `Linux_AMD64`, `Linux_S390`, `Linux_PPC`, `IBM_AIX_PPC64`, `HP_IA64`, `Linux_Itanium`, `Solaris_SPARC64`, `Linux_LOP`, and `Intel_Solaris_AMD64`

**Parent topic:** image Commands

### rhpctl promote image

Promotes an image.

#### Syntax

    rhpctl promote image -image image_name -state {TESTABLE | RESTRICTED | PUBLISHED}

#### Parameters

Table A-33 rhpctl promote image Command Parameters

| Parameter                                    | Description                                                                                                               |
|:---------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------|
| `-image ``image_name`                        | Specify the name of the image that you want to promote.                                                                   |
| `-state {TESTABLE | RESTRICTED | PUBLISHED}` | Specify one of the following as the name of the state of the image:<br>• `TESTABLE`:<br>• `RESTRICTED`:<br>• `PUBLISHED`: |

#### Example

To promote an image named PRODIMAGE:

    $ rhpctl promote image -image PRODIMAGE -state RESTRICTED

**Parent topic:** image Commands

### rhpctl register image

Registers an image metadata to the Oracle FPP repository.

#### Syntax

    rhpctl register image -image image_name
       {-path home_path | -zip zipped_home_path} [-imagetype image_type] [-pathowner username]
       [-state {TESTABLE| RESTRICTED|PUBLISHED}] [-client cluster_name] [-targetnode target_node_name [-sudouser sudo_username
       -sudopath path_to_sudo_binary | -root | -cred cred_name]] [-useractiondata user_action_data]

#### Parameters

Table A-34 rhpctl register image Command Parameters

| Parameter                                                                                 | Description                                                                                                                                                                                                                                                                                                                                                                                                         |
|:------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-image ``image_name`                                                                     | Specify the name of a configured image from which to register a working copy or the name of an image series from which RHPCTL takes the latest image when adding a working copy.                                                                                                                                                                                                                                    |
| `-path ``home_path`                                                                       | Specify the absolute path for provisioning the software home. For Oracle Database images, this becomes the `ORACLE_HOME`.                                                                                                                                                                                                                                                                                           |
| `-zip ``zipped_home_path`                                                                 | Specify the absolute path of the compressed software home to be imported (a ZIP or TAR file).                                                                                                                                                                                                                                                                                                                       |
| `-imagetype ``image_type`                                                                 | Specify the software type. Use `ORACLEDBSOFTWARE` (default) for Oracle database software, `ORACLEGISOFTWARE` for Oracle Grid Infrastructure software, `ORACLEGGSOFTWARE` for Oracle GoldenGate software, `ODAPATCHSOFTWARE` for engineered systems (Oracle Data Appliance), `EXAPATCHSOFTWARE` for Oracle Exadata software, or `SOFTWARE` for all other software. For a custom image type, use the image type name. |
| `-pathowner ``user_name`                                                                  | Specify the user with read access to the files and directories under the specified path.<br>Note: This parameter is applicable only for non-Oracle database software homes.                                                                                                                                                                                                                                         |
| `-state {TESTABLE | RESTRICTED | PUBLISHED}`                                              | Specify whether the state of the image is testable, restricted, or published.                                                                                                                                                                                                                                                                                                                                       |
| `-client ``cluster_name`                                                                  | Specify the name of the client cluster.                                                                                                                                                                                                                                                                                                                                                                             |
| `-targetnode ``target_node_name`                                                          | Specify the name of an `rhpclient`-less target.                                                                                                                                                                                                                                                                                                                                                                     |
| `-sudouser ``sudo_user_name`` -sudopath ``sudo_binary_path`` | -root | -cred ``cred_name` | If you use the `-targetnode` parameter, then you must specify either sudo or `root` to perform super user operations.                                                                                                                                                                                                                                                                                               |
| `-useractiondata ``user_action_data`                                                      | Optionally, you can pass a value to the `useractiondata` parameter of the user action script.                                                                                                                                                                                                                                                                                                                       |

#### Examples

- To register an Oracle Database image:

      $ rhpctl register image -image PRODIMAGEV1 -path /u01/app/product/23.5.0/dbhome_1 -pathowner orcl

**Parent topic:** image Commands

### rhpctl uninstantiate image

Stops updates for previously requested images from a peer Fleet Patching and Provisioning Server.

#### Syntax

    rhpctl uninstantiate image -server server_cluster_name {-image image_name
      | -series series_name | -imagetype image_type | -all}

#### Parameters

Table A-35 rhpctl uninstantiate image Command Parameters

| Parameter                                                                            | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:-------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-server ``server_cluster_name`                                                      | Specify a Fleet Patching and Provisioning Server cluster from which you want to stop updates.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `-image ``image_name`` | -series ``series_name`` | -imagetype ``image_type`` | -all` | You can get updates from a peer Fleet Patching and Provisioning Server, specifically, by image name, series name, or image type. Alternatively, you can use the `-all` parameter to stop updates from the peer Fleet Patching and Provisioning server.<br>If you choose to stop updates by image type, then specify `ORACLEDBSOFTWARE` (default) for Oracle Database software, `ORACLEGISOFTWARE` for Oracle Grid Infrastructure software, `ORACLEGGSOFTWARE` for Oracle GoldenGate software, and `SOFTWARE` for all other software. For a custom image type, use the image type name. |

**Parent topic:** image Commands
