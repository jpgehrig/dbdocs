## useraction Commands

Use commands with the `useraction` keyword to add, delete, and modify user actions.

- rhpctl add useraction
  Configures a user action and its associated script and action file.
- rhpctl delete useraction
  Deletes an existing user action configuration.
- rhpctl modify useraction
  Modifies the configuration of the specified user action name.
- rhpctl query useraction
  Displays the configuration of a user action.

**Parent topic:** [RHPCTL Command Reference](rhpctl-command-reference.md)

### rhpctl add useraction

Configures a user action and its associated script and action file.

#### Syntax

    rhpctl add useraction -useraction user_action_name -actionscript script_name
      [-actionfile file_name] [-pre | -post] [-optype option]
      [-onerror {ABORT | CONTINUE}] [-runscope {ONENODE | ALLNODES | AUTO}]

#### Parameters

Table A-62 rhpctl add useraction Command Parameters

| Parameter                               | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|:----------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-useraction ``user_action_name`        | Specify the name of the user action you want to add.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `-actionscript ``script_name`           | Associate a specific action script to run with the user action.                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `-actionfile ``file_name`               | Optionally, you can specify an action file that is required by the user action.                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `-pre | -post`                          | Use the `-pre` parameter to run the user action before the add operation or the `-post` parameter to run the user action after.                                                                                                                                                                                                                                                                                                                                                                                                       |
| `-optype ``option`                      | Optionally, you can specify the operation for which the user action is configured. Options include:<br>• IMPORT_IMAGE<br>• ADD_WORKINGCOPY<br>• DELETE_WORKINGCOPY<br>• ADD_DATABASE<br>• DELETE_DATABASE<br>• MOVE_DATABASE<br>• MOVE_GIHOME<br>• UPGRADE_DATABASE<br>• UPGRADE_GIHOME<br>• ADDNODE_GIHOME<br>• DELETENODE_GIHOME<br>• ADDNODE_DATABASE<br>• DELETENODE_DATABASE<br>• ADDNODE_WORKINGCOPY<br>• ZDTUPGRADE_DATABASE<br>• ZDTUPGRADE_DATABASE_SNAPDB<br>• ZDTUPGRADE_DATABASE_DBUA<br>• ZDTUPGRADE_DATABASE_SWITCHBACK |
| `-onerror {ABORT | CONTINUE}`           | Optionally, you can choose whether to abort or continue the operation if the user action encounters an error while it is running.                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-runscope {ONENODE | ALLNODES | AUTO}` | Optionally, you can specify the nodes where the user action is run. Choose `ONENODE` to run the user action for each database on the node on which a patch was applied to the database. Choose `ALLNODES` to run the user action for each database on every cluster node. Choose `AUTO` for a run scope based on the other command options.                                                                                                                                                                                           |

**Parent topic:** useraction Commands

### rhpctl delete useraction

Deletes an existing user action configuration.

#### Syntax

    rhpctl delete useraction -useraction user_action_name

#### Usage Notes

Specify the name of a user action you want to delete.

**Parent topic:** useraction Commands

### rhpctl modify useraction

Modifies the configuration of the specified user action name.

#### Syntax

    rhpctl modify useraction -useraction user_action_name [-actionscript script_name]
      [-actionfile file_name] [-pre | -post] [-optype option]
      [-onerror {ABORT | CONTINUE}] [-runscope {ONENODE | ALLNODES | AUTO}]

#### Parameters

Table A-63 rhpctl modify useraction Command Parameters

| Parameter                               | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|:----------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-useraction ``user_action_name`        | Specify the name of the user action you want to modify.                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `-actionscript ``script_name`           | Optionally, you can specify an action script to run.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `-pre | -post`                          | Use the `-pre` parameter to run the user action before the modify operation or the `-post` parameter to run the user action after.                                                                                                                                                                                                                                                                                                                                                                                                    |
| `-optype ``option`                      | Optionally, you can specify the operation for which the user action is configured. Options include:<br>• IMPORT_IMAGE<br>• ADD_WORKINGCOPY<br>• DELETE_WORKINGCOPY<br>• ADD_DATABASE<br>• DELETE_DATABASE<br>• MOVE_DATABASE<br>• MOVE_GIHOME<br>• UPGRADE_DATABASE<br>• UPGRADE_GIHOME<br>• ADDNODE_GIHOME<br>• DELETENODE_GIHOME<br>• ADDNODE_DATABASE<br>• DELETENODE_DATABASE<br>• ADDNODE_WORKINGCOPY<br>• ZDTUPGRADE_DATABASE<br>• ZDTUPGRADE_DATABASE_SNAPDB<br>• ZDTUPGRADE_DATABASE_DBUA<br>• ZDTUPGRADE_DATABASE_SWITCHBACK |
| `-onerror {ABORT | CONTINUE}`           | Optionally, you can choose whether to abort or continue the operation if the user action encounters an error while it is running.                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-runscope {ONENODE | ALLNODES | AUTO}` | Optionally, you can specify the nodes where the user action is run. Optionally, you can specify the nodes where the user action is run. Choose `ONENODE` to run the user action for each database on the node on which a patch was applied to the database. Choose `ALLNODES` to run the user action for each database on every cluster node. Choose `AUTO` for a run scope based on the other command options.                                                                                                                       |

**Parent topic:** useraction Commands

### rhpctl query useraction

Displays the configuration of a user action.

#### Syntax

    rhpctl query useraction [-useraction user_action_name | -imagetype image_type]
      [-optype option]

#### Parameters

Table A-64 rhpctl query useraction Command Parameters

| Parameter                        | Description                                                                                                                                                                                                                                                                                                                                                                                                         |
|:---------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-useraction ``user_action_name` | Specify the name of the user action you want to query.                                                                                                                                                                                                                                                                                                                                                              |
| `-imagetype ``image_type`        | Specify the software type. Use `ORACLEDBSOFTWARE` (default) for Oracle database software, `ORACLEGISOFTWARE` for Oracle Grid Infrastructure software, `ORACLEGGSOFTWARE` for Oracle GoldenGate software, `ODAPATCHSOFTWARE` for engineered systems (Oracle Data Appliance), `EXAPATCHSOFTWARE` for Oracle Exadata software, or `SOFTWARE` for all other software. For a custom image type, use the image type name. |
| `-optype ``option`               | Optionally, you can specify the operation for which to run the query. Options include:<br>• IMPORT_IMAGE<br>• ADD_WORKINGCOPY<br>• DELETE_WORKINGCOPY<br>• ADD_DATABASE<br>• DELETE_DATABASE<br>• MOVE_DATABASE<br>• MOVE_GIHOME<br>• UPGRADE_DATABASE<br>• UPGRADE_GIHOME<br>• ADDNODE_GIHOME<br>• DELETENODE_GIHOME<br>• ADDNODE_DATABASE<br>• DELETENODE_DATABASE<br>• ADDNODE_WORKINGCOPY                       |

**Parent topic:** useraction Commands
