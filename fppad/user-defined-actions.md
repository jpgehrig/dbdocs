## User-Defined Actions

You can create actions for various Oracle Fleet Patching and Provisioning operations, such as import image, add and delete working copy, and add, delete, move, and upgrade a software home.

You can define different actions for each operation, which can be further differentiated by the type of image to which the operation applies. User-defined actions can be run before or after a given operation, and are run on the deployment on which the operation is run, whether it be an Oracle Fleet Patching and Provisioning Server, an Oracle Fleet Patching and Provisioning Client (12c release 2 (12.2), or later), or an `rhpclient`-less target.

User-defined actions are shell scripts which are stored on the Oracle Fleet Patching and Provisioning Server. When a script runs, it is given relevant information about the operation on the command line. Also, you can associate a file with the script. The Oracle Fleet Patching and Provisioning Server will copy that file to the same location on the Client or `rhpclient`-less target where the script is run.

For example, perhaps you want to create user-defined actions that are run after a database upgrade, and you want to define different actions for Oracle Database 11g and 12c. This requires you to define new image types, as in the following example procedure.

1.  Create a new image type, (`DB11IMAGE`, for example), based on the ORACLEDBSOFTWARE image type, as follows:

        $ rhpctl add imagetype -imagetype DB11IMAGE -basetype ORACLEDBSOFTWARE

    When you add or import an Oracle Database 11g gold image, you specify the image type as `DB11IMAGE`.

2.  Define a user action and associate it with the `DB11IMAGE` image type and the upgrade operation. You can have different actions that are run before or after upgrade.

3.  To define an action for Oracle Database 12c, create a new image type (`DB12IMAGE`, for example) that is based on the ORACLEDBSOFTWARE image type, as in the preceding step, but with the `DB12IMAGE` image type.
    **Note:**

    If you define user actions for the base type of a user-defined image type (in this case the base type is ORACLEDBSOFTWARE), then Oracle Fleet Patching and Provisioning performs those actions before the actions for the user-defined image type.

You can modify the image type of an image using the `rhpctl modify image` command. Additionally, you can modify, add, and delete other actions. The following two tables, Table 7-1 and Table 7-2, list the operations you can customize and the parameters you can use to define those operations, respectively.

Table 7-1 Oracle Fleet Patching and Provisioning User-Defined Operations

| Operation                                                                                                                                                                                                                                                                                                                                              | Parameter List                                                                                                                                                                                                                                                                                                              |
|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `IMPORT_IMAGE`                                                                                                                                                                                                                                                                                                                                         | `RHP_OPTYPE`, `RHP_PHASE`, `RHP_PATH`, `RHP_PATHOWNER`, `RHP_PROGRESSLISTENERHOST`, `RHP_PROGRESSLISTENERPORT`, `RHP_IMAGE`, `RHP_IMAGETYPE`, `RHP_VERSION`, `RHP_CLI`, `RHP_USERACTIONDATA`                                                                                                                                |
| `ADD_WORKINGCOPY`                                                                                                                                                                                                                                                                                                                                      | `RHP_OPTYPE`, `RHP_PHASE`, `RHP_WORKINGCOPY`, `RHP_PATH`, `RHP_STORAGETYPE`, `RHP_USER`, `RHP_NODES`, `RHP_ORACLEBASE`, `RHP_DBNAME`, `RHP_PROGRESSLISTENERHOST`, `RHP_PROGRESSLISTENERPORT`, `RHP_IMAGE`, `RHP_IMAGETYPE`, `RHP_VERSION`, `RHP_CLI`, `RHP_USERACTIONDATA`                                                  |
| `ADD_DATABASE`                                                                                                                                                                                                                                                                                                                                         | `RHP_OPTYPE`, `RHP_PHASE`, `RHP_WORKINGCOPY`, `RHP_CLIENT`, `RHP_DBNAME`, `RHP_PROGRESSLISTENERHOST`, `RHP_PROGRESSLISTENERPORT`, `RHP_IMAGE`, `RHP_IMAGETYPE`, `RHP_VERSION`, `RHP_CLI`, `RHP_USERACTIONDATA`                                                                                                              |
| `DELETE_WORKINGCOPY`                                                                                                                                                                                                                                                                                                                                   | `RHP_OPTYPE`, `RHP_PHASE`, `RHP_WORKINGCOPY`, `RHP_CLIENT`, `RHP_PATH`, `RHP_PROGRESSLISTENERHOS`, `RHP_PROGRESSLISTENERPORT`, `RHP_IMAGE`, `RHP_IMAGETYPE`, `RHP_VERSION`, `RHP_CLI`, `RHP_USERACTIONDATA`                                                                                                                 |
| `DELETE_DATABASE`                                                                                                                                                                                                                                                                                                                                      | `RHP_OPTYPE`, `RHP_PHASE`, `RHP_WORKINGCOPY`, `RHP_CLIENT`, `RHP_DBNAME`, `RHP_PROGRESSLISTENERHOST`, `RHP_PROGRESSLISTENERPORT`, `RHP_IMAGE`, `RHP_IMAGETYPE`, `RHP_VERSION`, `RHP_CLI`, `RHP_USERACTIONDATA`                                                                                                              |
| `MOVE_GIHOME`                                                                                                                                                                                                                                                                                                                                          | `RHP_OPTYPE`, `RHP_PHASE`, `RHP_SOURCEWC`, `RHP_SOURCEPATH`, `RHP_DESTINATIONWC`, `RHP_DESTINATIONPATH`, `RHP_IMAGE`, `RHP_IMAGETYPE`, `RHP_PROGRESSLISTENERHOS`, `RHP_PROGRESSLISTENERPORT`, `RHP_VERSION`, `RHP_CL`, `RHP_USERACTIONDATA`                                                                                 |
| `MOVE_DATABASE`<br>This user action is run for each database involved in a patching operation.<br>If the run scope is set to `ALLNODES`, then the script is run for each database on every cluster node.<br>If the run scope is set to `ONENODE`, then the script is run for each database on the node on which the patch was applied to the database. | `RHP_OPTYPE`, `RHP_PHASE`, `RHP_SOURCEWC`, `RHP_SOURCEPATH`, `RHP_DESTINATIONWC`, `RHP_DESTINATIONPATH`, `RHP_DBNAME`, `RHP_IMAGE`, `RHP_IMAGETYPE`, `RHP_PROGRESSLISTENERHOST`, `RHP_PROGRESSLISTENERPORT`, `RHP_VERSION`, `RHP_CLI`, `RHP_DATAPATCH`, `RHP_USERACTIONDATA`                                                |
| `UPGRADE_GIHOME`                                                                                                                                                                                                                                                                                                                                       | `RHP_OPTYPE`, `RHP_PHASE`, `RHP_SOURCEWC`, `RHP_SOURCEPATH`, `RHP_DESTINATIONWC`, `RHP_DESTINATIONPATH`, `RHP_IMAGE`, `RHP_IMAGETYPE`, `RHP_PROGRESSLISTENERHOST`, `RHP_PROGRESSLISTENERPORT`, `RHP_VERSION`, `RHP_CLI`, `RHP_USERACTIONDATA`                                                                               |
| `UPGRADE_DATABASE`                                                                                                                                                                                                                                                                                                                                     | `RHP_OPTYPE`, `RHP_PHASE`, `RHP_SOURCEWC`, `RHP_SOURCEPATH`, `RHP_DESTINATIONWC`, `RHP_DESTINATIONPATH`, `RHP_DBNAME`, `RHP_IMAGE`, `RHP_IMAGETYPE`, `RHP_PROGRESSLISTENERHOST`, `RHP_PROGRESSLISTENERPORT`, `RHP_VERSION`, `RHP_CLI`, `RHP_USERACTIONDATA`                                                                 |
| `ADDNODE_DATABASE`                                                                                                                                                                                                                                                                                                                                     | `RHP_OPTYPE`, `RHP_PHASE`, `RHP_WORKINGCOPY`, `RHP_CLIENT`, `RHP_DBNAME`, `RHP_PROGRESSLISTENERHOST`, `RHP_PROGRESSLISTENERPORT`, `RHP_IMAGE`, `RHP_IMAGETYPE`, `RHP_VERSION`, `RHP_CLI`, `RHP_USERACTIONDATA`                                                                                                              |
| `DELETENODE_DATABASE`                                                                                                                                                                                                                                                                                                                                  | `RHP_OPTYPE`, `RHP_PHASE`, `RHP_WORKINGCOPY`, `RHP_CLIENT`, `RHP_DBNAME`, `RHP_PROGRESSLISTENERHOST`, `RHP_PROGRESSLISTENERPORT`, `RHP_IMAGE`, `RHP_IMAGETYPE`, `RHP_VERSION`, `RHP_CLI`, `RHP_USERACTIONDATA`                                                                                                              |
| `ADDNODE_GIHOME`                                                                                                                                                                                                                                                                                                                                       | `RHP_OPTYPE`, `RHP_PHASE`, `RHP_WORKINGCOPY`, `RHP_CLIENT`, `RHP_PATH`, `RHP_PROGRESSLISTENERHOST`, `RHP_PROGRESSLISTENERPORT`, `RHP_IMAGE`, `RHP_IMAGETYPE`, `RHP_VERSION`, `RHP_CLI`, `RHP_USERACTIONDATA`                                                                                                                |
| `DELETENODE_GIHOME`                                                                                                                                                                                                                                                                                                                                    | `RHP_OPTYPE`, `RHP_PHASE`, `RHP_WORKINGCOPY`, `RHP_CLIENT`, `RHP_PATH`, `RHP_PROGRESSLISTENERHOST`, `RHP_PROGRESSLISTENERPORT`, `RHP_IMAGE`, `RHP_IMAGETYPE`, `RHP_VERSION`, `RHP_CLI`, `RHP_USERACTIONDATA`                                                                                                                |
| `ADDNODE_WORKINGCOPY`                                                                                                                                                                                                                                                                                                                                  | `RHP_OPTYPE`, `RHP_PHASE`, `RHP_WORKINGCOPY`, `RHP_CLIENT`, `RHP_PATH`, `RHP_PROGRESSLISTENERHOST`, `RHP_PROGRESSLISTENERPORT`, `RHP_IMAGE`, `RHP_IMAGETYPE`, `RHP_VERSION`, `RHP_CLI`, `RHP_USERACTIONDATA`                                                                                                                |
| `ZDTUPGRADE_DATABASE`                                                                                                                                                                                                                                                                                                                                  | `RHP_OPTYPE`, `RHP_PHASE`, `RHP_SOURCEWC`, `RHP_SOURCEPATH`, `RHP_DESTINATIONWC`, `RHP_DESTINATIONPATH`, `RHP_SRCGGWC`, `RHP_SRCGGPATH`, `RHP_DSTGGWC`, `RHP_DSTGGPATH`, `RHP_DBNAME`, `RHP_IMAGE`, `RHP_IMAGETYPE`, `RHP_PROGRESSLISTENERHOST`, `RHP_PROGRESSLISTENERPORT`, `RHP_VERSION`, `RHP_CLI`, `RHP_USERACTIONDATA` |
| `ZDTUPGRADE_DATABASE_SNAPDB`                                                                                                                                                                                                                                                                                                                           | `RHP_OPTYPE`, `RHP_PHASE`, `RHP_SOURCEWC`, `RHP_SOURCEPATH`, `RHP_DESTINATIONWC`, `RHP_DESTINATIONPATH`, `RHP_SRCGGWC`, `RHP_SRCGGPATH`, `RHP_DSTGGWC`, `RHP_DSTGGPATH`, `RHP_DBNAME`, `RHP_IMAGE`, `RHP_IMAGETYPE`, `RHP_PROGRESSLISTENERHOST`, `RHP_PROGRESSLISTENERPORT`, `RHP_VERSION`, `RHP_CLI`, `RHP_USERACTIONDATA` |
| `ZDTUPGRADE_DATABASE_DBUA`                                                                                                                                                                                                                                                                                                                             | `RHP_OPTYPE`, `RHP_PHASE`, `RHP_SOURCEWC`, `RHP_SOURCEPATH`, `RHP_DESTINATIONWC`, `RHP_DESTINATIONPATH`, `RHP_SRCGGWC`, `RHP_SRCGGPATH`, `RHP_DSTGGWC`, `RHP_DSTGGPATH`, `RHP_DBNAME`, `RHP_IMAGE`, `RHP_IMAGETYPE`, `RHP_PROGRESSLISTENERHOST`, `RHP_PROGRESSLISTENERPORT`, `RHP_VERSION`, `RHP_CLI`, `RHP_USERACTIONDATA` |
| `ZDTUPGRADE_DATABASE_SWITCHBACK`                                                                                                                                                                                                                                                                                                                       | `RHP_OPTYPE`, `RHP_PHASE`, `RHP_SOURCEWC`, `RHP_SOURCEPATH`, `RHP_DESTINATIONWC`, `RHP_DESTINATIONPATH`, `RHP_SRCGGWC`, `RHP_SRCGGPATH`, `RHP_DSTGGWC`, `RHP_DSTGGPATH`, `RHP_DBNAME`, `RHP_IMAGE`, `RHP_IMAGETYPE`, `RHP_PROGRESSLISTENERHOST`, `RHP_PROGRESSLISTENERPORT`, `RHP_VERSION`, `RHP_CLI`, `RHP_USERACTIONDATA` |

Table 7-2 User-Defined Operations Parameters

| Parameter                  | Description                                                                                                                                                                                                                                                                             |
|:---------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `RHP_OPTYPE`               | The operation type for which the user action is being processed, as listed in the previous table.                                                                                                                                                                                       |
| `RHP_PHASE`                | This parameter indicates whether the user action is processed before or after the operation (is either PRE or POST).                                                                                                                                                                    |
| `RHP_SOURCEWC`             | The source working copy name for a patch of upgrade operation.                                                                                                                                                                                                                          |
| `RHP_SOURCEPATH`           | The path of the source working copy home.                                                                                                                                                                                                                                               |
| `RHP_DESTINATIONWC`        | The destination working copy name for a patch or upgrade operation.                                                                                                                                                                                                                     |
| `RHP_DESTINATIONPATH`      | The path of the destination working copy home.                                                                                                                                                                                                                                          |
| `RHP_SRCGGWC`              | The name of the version of the Oracle GoldenGate working copy from which you want to upgrade.                                                                                                                                                                                           |
| `RHP_SRCGGPATH`            | The absolute path of the version of the Oracle GoldenGate software home from which you want to upgrade.                                                                                                                                                                                 |
| `RHP_DESTGGWC`             | The name of the version of the Oracle GoldenGate working copy to which you want to upgrade.                                                                                                                                                                                             |
| `RHP_DESTGGPATH`           | The absolute path of the version of the Oracle GoldenGate software home to which you want to upgrade.                                                                                                                                                                                   |
| `RHP_PATH`                 | This is the path to the location of the software home. This parameter represents the path on the local node from where the RHPCTL command is being run for an `IMPORT_IMAGE` operation. For all other operations, this path is present on the site where the operation is taking place. |
| `RHP_PATHOWNER`            | The owner of the path for the gold image that is being imported.                                                                                                                                                                                                                        |
| `RHP_PROGRESSLISTENERHOST` | The host on which the progress listener is listening. You can use this parameter, together with a progress listener port, to create a TCP connection to print output to the console on which the RHPCTL command is being run.                                                           |
| `RHP_PROGRESSLISTENERPORT` | The port on which the progress listener host is listening. You can use this parameter, together with a progress listener host name, to create a TCP connection to print output to the console on which the RHPCTL command is being run.                                                 |
| `RHP_IMAGE`                | The image associated with the operation. In the case of a move operation, it will reflect the name of the destination image.                                                                                                                                                            |
| `RHP_IMAGETYPE`            | The image type of the image associated with the operation. In the case of a move operation, it will reflect the name of the destination image.                                                                                                                                          |
| `RHP_VERSION`              | The version of the Oracle Grid Infrastructure software running on the Oracle Fleet Patching and Provisioning Server.                                                                                                                                                                    |
| `RHP_CLI`                  | The exact command that was run to invoke the operation.                                                                                                                                                                                                                                 |
| `RHP_STORAGETYPE`          | The type of storage for the home (either `LOCAL` or `RHP_MANAGED`)                                                                                                                                                                                                                      |
| `RHP_USER`                 | The user for whom the operation is being performed.                                                                                                                                                                                                                                     |
| `RHP_NODES`                | The nodes on which a database will be created.                                                                                                                                                                                                                                          |
| `RHP_ORACLEBASE`           | The Oracle base location for the provisioned home.                                                                                                                                                                                                                                      |
| `RHP_DBNAME`               | The name of the database to be created.                                                                                                                                                                                                                                                 |
| `RHP_CLIENT`               | The name of the client cluster.                                                                                                                                                                                                                                                         |
| `RHP_DATAPATCH`            | This parameter is set to TRUE at the conclusion of the user action on the node where the SQL patch will be run after the move database operation is complete.                                                                                                                           |
| `RHP_USERACTIONDATA`       | This parameter is present in all of the operations and is used to pass user-defined items to the user action as an argument during runtime.                                                                                                                                             |

### Example of User-Defined Action

Suppose there is an image type, `APACHESW`, to use for provisioning and managing Apache deployments. Suppose, too, that there is a Gold Image of Apache named `apacheinstall`. The following example shows how to create a user action that will run prior to provisioning any copy of our Apache Gold Image.

The following is a sample user action script named `addapache_useraction.sh`:

    $ cat /scratch/apacheadmin/addapache_useraction.sh
    #!/bin/sh

    #refer to arguments using argument names
    touch /tmp/SAMPLEOUT.txt;
    for i in "$@"
    do
        export $i
    done

    echo "OPTYPE = $RHP_OPTYPE" >> /tmp/SAMPLEOUT.txt;
    echo "PHASE = $RHP_PHASE" >> /tmp/SAMPLEOUT.txt;
    echo "WORKINGCOPY = $RHP_WORKINGCOPY" >> /tmp/SAMPLEOUT.txt;
    echo "PATH = $RHP_PATH" >> /tmp/SAMPLEOUT.txt;
    echo "STORAGETYPE = $RHP_STORAGETYPE" >> /tmp/SAMPLEOUT.txt;
    echo "USER = $RHP_USER" >> /tmp/SAMPLEOUT.txt;
    echo "NODES = $RHP_NODES" >> /tmp/SAMPLEOUT.txt;
    echo "ORACLEBASE = $RHP_ORACLEBASE" >> /tmp/SAMPLEOUT.txt;
    echo "DBNAME = $RHP_DBNAME" >> /tmp/SAMPLEOUT.txt;
    echo "PROGRESSLISTENERHOST = $RHP_PROGRESSLISTENERHOST" >> /tmp/SAMPLEOUT.txt;
    echo "PROGRESSLISTENERPORT = $RHP_PROGRESSLISTENERPORT" >> /tmp/SAMPLEOUT.txt;
    echo "IMAGE = $RHP_IMAGE" >> /tmp/SAMPLEOUT.txt;
    echo "IMAGETYPE = $RHP_IMAGETYPE" >> /tmp/SAMPLEOUT.txt;
    echo "RHPVERSION = $RHP_VERSION" >> /tmp/SAMPLEOUT.txt;
    echo "CLI = $RHP_CLI" >> /tmp/SAMPLEOUT.txt;
    echo "USERACTIONDATA = $RHP_USERACTIONDATA" >> /tmp/SAMPLEOUT.txt;
    $

The script is registered to run at the start of `rhpctl add workingcopy` commands. The add working copy operation stops if the script fails.

The following command creates a user action called addapachepre:

    $ rhpctl add useraction -optype ADD_WORKINGCOPY -pre -onerror ABORT -useraction
      addapachepre -actionscript /scratch/apacheadmin/addapache_useraction.sh
      -runscope ONENODE

The following command registers the user action for the `APACHESW` image type:

    $ rhpctl modify imagetype -imagetype APACHESW -useractions addapachepre

The registered user action is invoked automatically at the start of commands that deploy a working copy of any image of the APACHESW type, such as the following:

    $ rhpctl add workingcopy -workingcopy apachecopy001 -image apacheinstall
      -path /scratch/apacheadmin/apacheinstallloc -sudouser apacheadmin -sudopath
      /usr/local/bin/sudo -node targetnode003 -user apacheadmin -useractiondata "sample"

The sample script creates the `/tmp/SAMPLEOUT.txt` output file. Based on the example command, the output file contains:

    $ cat /tmp/SAMPLEOUT.txt
    OPTYPE = ADD_WORKINGCOPY
    PHASE = PRE
    WORKINGCOPY = apachecopy001
    PATH = /scratch/apacheadmin/apacheinstallloc
    STORAGETYPE =
    USER = apacheadmin
    NODES = targetnode003
    ORACLEBASE =
    DBNAME =
    PROGRESSLISTENERHOST = mds11042003.my.example.com
    PROGRESSLISTENERPORT = 58068
    IMAGE = apacheinstall
    IMAGETYPE = APACHESW
    RHPVERSION = 12.2.0.1.0
    CLI = rhpctl__add__workingcopy__-image__apacheinstall__-path__/scratch/apacheadmin
     /apacheinstallloc__-node__targetnode003__-useractiondata__sample__
     -sudopath__/usr/local/bin/sudo__-workingcopy__apachecopy__-user__apacheadmin__
     -sudouser__apacheadmin__USERACTIONDATA = sample
    $

**Notes:**

- In the preceding output example empty values terminate with an equals sign (`=`).

- The spaces in the command-line value of the `RHP_CLI` parameter are replaced by two underscore characters (`__`) to differentiate this from other parameters.

**Parent topic:** [Advanced Oracle Fleet Patching and Provisioning Configurations](advanced-oracle-fpp-configurations.md)
