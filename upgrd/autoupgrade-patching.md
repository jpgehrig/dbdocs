## AutoUpgrade Patching

AutoUpgrade has enhanced capability that enables it to automate all of the necessary steps in the database patching process, including optional downloading of patches.

- How AutoUpgrade Performs AutoUpgrade Patching
  AutoUpgrade Patching extends the AutoUpgrade upgrade process to patching, which enables you to perform out-of-place patching for multiple databases using a single command.
- AutoUpgrade Patching Stages and Workflows
  AutoUpgrade Patching supports three different job modes. Each mode runs a different set of stages.
- PDB Priority and AutoUpgrade
  For both AutoUpgrade patching and upgrades, AutoUpgrade honors how PDBs will be prioritized by setting the priority on specifuc PDBs.
- Configuration Parameters and Command-Line Options for AutoUprade Patching
  In addition to other configuration file parameters and command-line options, there are specific parameters and options for AutoUpgrade Patching.
- AutoUpgrade Patching Configuration Files and Log Files
  See examples of configuration files and log files for AutoUpgrade Patching.
- AutoUpgrade Patching Workflow Examples
  Use this example of an AutoUpgrade patching workflow to understand the AutoUpgrade patching procedure.

**Parent topic:** [Using AutoUpgrade for Oracle Database Upgrades](using-autoupgrade-oracle-database-upgrades.md)

### How AutoUpgrade Performs AutoUpgrade Patching

AutoUpgrade Patching extends the AutoUpgrade upgrade process to patching, which enables you to perform out-of-place patching for multiple databases using a single command.

**Note:**

Oracle recommends that you use Oracle Fleet Patching and Provisioning for Oracle Real Application Clusters environments.

With the latest release of AutoUpgrade the AutoUpgrade Patching procedure can be performed on Release Update (RU), Monthly Recommended Patches (MRPs), and one-off patches, using out-of-place patching. When you patch from an earlier RU or MRP with AutoUpgrade, the simplicity, reliability, and recoverability of AutoUpgrade is extended to the patching process. As a result, patching is easier to perform, and you also obtain simpler recovery from any issues that can arise during the patch deployment.

There are no additional parameters or options that you need to set in the configuration file for AutoUpgrade to perform patching. Just specify the source and target Oracle homes, and AutoUpgrade will apply changes to the databases. When the source and target Oracle homes are the same Oracle Database release (for example, from 19.11 to 19.13), AutoUpgrade identifies the operation as an RU or MRP patch operation. This capability also applies to one-off patches: If the RU or MRP applied to the target Oracle home is later than the RU or MRP of the source Oracle home, then you can apply one-off patches as needed to the target Oracle home using this method.

As AutoUpgrade performs the patch operation, it uses Datapatch to apply an RU or MRP to databases. The process of patching takes advantage of existing AutoUpgrade options and operations, as with a full release upgrade, including creating a Guarantee Restore Point. During the patching process, the database is shut down in the source Oracle home, and brought back up in the target Oracle home. RU or MRP updates are performed in upgrade mode, using Datapatch.

**Note:**

AutoUpgrade does not perform rolling upgrades of Oracle Database releases. Oracle recommends that you use Oracle Fleet Patching and Provisioning to be able to obtain rolling patch maintenance for Oracle Real Application Clusters (Oracle RAC) environments.

#### Benefits of AutoUpgrade Patching

- AutoUpgrade enables patching of all databases specified in the configuration file, in one operation.
- Resume capabilities are already included with AutoUpgrade.
- Restore capabilities are provided so that it is possible to roll back to the earlier release Oracle home:
  - Restore using the Guarantee Restore Point (GRP) generated during the patching process.
  - If a GRP is not present, then the Datapatch rollback functionality can also perform a restore. AutoUpgrade detects that a GRP does not exist, and automatically performs the restore using Datapatch. To enable a Datapatch rollback restore, set the restoration configuration option to `no`. For example: `sales1.restoration=no`.
- Oracle RAC management is provided automatically with AutoUpgrade.
- The error management reporting features of AutoUpgrade are extended to patching.
- The JSON status and progress reporting of AutoUpgrade are extended to patching.
- AutoUpgrade uses the Datapatch JSON status files to determine success or failure of each process, and reports those results to you at the completion of the process.

#### Features Supported for AutoUpgrade Patching

The following features are provided with AutoUpgrade Patching

- Patching of databases encrypted with Transparent Data Encryption (TDE).
- Hot Cloning/Relocate, which enables you to create PDBs from a Non-CDB, or from a PDB on a remote host.
- Proactive Fixups, which runs postfixups on the PDB as soon as the PDB is patched. Note that proactive fixups is currently not supported on Microsofts Windows.
- Multi-node patching and upgrades using Oracle Real Application Clusters (Oracle RAC), which enables AutoUpgrade to spread the workload across multiple nodes.
- Configuration management, by copying or merging the source Oracle home configuration files (`tnsnames.ora`, `sqlnet.ora`, and other files) to the target Oracle home.
- Analysis of the database before starting a patching procedure, to ensure patch readiness.
- Running fixups during production before patching, so that you reduce downtime. You can then use `-mode upgrade` to bypass running fixups and proceed directly to patching the database.
- Performing all patching tasks in Deploy mode, to achieve end-to-end patching.
- Enhanced reporting of the patching process, which enables you to diagnose errors more easily by using the `datapatch_summary.log` report.
- Datapatch log files found in the Datapatch summary JSON file are copied to the output file of the apply or rollback operational logs as follows:
  - Apply log format, where `dbname` is the name of the database: `applydatapatchlogfiles#``dbname``.log`
  - Rollback log format, where `dbname` is the name of the database: `rollbackdatapatchlogfiles#``dbname``.log`
- Datapatch output is logged to following operational logs:
  - Apply log format, where `dbname` is the name of the database: `applyautoupgrade#``dbname``.log`
  - Rollback log format, where `dbname` is the name of the database: `rollbackautoupgrade#``dbname``.log`
- Datapatch JSON output is logged to the following operational logs:
  - Apply log format, where `dbname` is the name of the database: `applydatapatchsummary#``dbname``.log`
  - Rollback log format, where `dbname` is the name of the database: `rollbackdatapatchsummary#``dbname``.log`
- Storage of all related patching log files produced by AutoUpgrade are stored in the `dbupgrade` directory.
- Standard Datapatch log files are stored in `Oracle-base``/cfgtoollogs/sqlpatch`.
- Starting with AutoUpgrade 23.1, Patching is supported for single-instance databases on Microsoft Windows. It is not supported with Oracle Real Application Clusters (Oracle RAC).

#### Requirements and Restrictions for using AutoUpgrade Patching

- Downtime is required to use AutoUpgrade Patching:
  - After the patch operation is completed, the database is restarted.
  - Patching in normal mode enables the database to be available in the target home while the patching is proceeding.
  - Patching in upgrade mode requires the patching to be completed before the database is restarted in the target home.
  - During the patch operation, the CDB and PDBs are opened in normal mode after drain operations complete, and patching proceeds. However, rolling patching for Oracle Real Application Clusters is not supported at this time.
  - To enable PDBs to become available as soon as they are successfully patched, then ensure that you set the `tune_settings` option `make_pdbs_avaliable` to `true` in your configuration file. For example: `sales3.tune_setting=proactive_fixups=true,make_pdbs_available=true`
  - Because downtime is required, rolling upgrades of Oracle RAC are not supported at this time.

- AutoUpgrade can support a target RU or MRP that has additional patches applied. However, the source Oracle Database must be on an earlier RU or MRP than the target Oracle Database RU or MRP.

- AutoUpgrade does not move the listener to the new Oracle home. If needed, you must manually move the listener to the new Oracle home before you start AutoUpgrade.

- Installation and configuration of the target Oracle Database home must be complete before you can run RUs and MRPs on the target home using AutoUpgrade Patching. If a target RU is patched after it has been applied to the database, then you can no longer use AutoUpgrade Patching. Instead, you must use Datapatch to apply the updates.

- Performing rolling patches of Oracle Database (single-instance or Oracle RAC) is not supported. When you use AutoUpgrade Patching on a single-instance or Oracle RAC Oracle Database, AutoUpgrade's Oracle RAC management will shut down the database on all nodes.

- The target Oracle Database RU must be at least Oracle Database 19c, RU 19.3, or later releases. You cannot use AutoUpgrade Patching to perform RUs or MRPs to earlier Oracle Database releases.

- The effect of AutoUpgrade Patching on databases using Oracle Data Guard Physical Standby or Oracle Data Guard Logical Standby and Rolling Upgrade is the same as with using Datapatch. AutoUpgrade patching can be a part of the procedures.
  **Note:**

  Oracle recommends that you use Oracle Fleet Patching and Provisioning for databases deployed with Oracle Data Guard

- AutoUpgrade supports physically moving a database to different hardware. When the database is moved to a different target system, AutoUpgrade Patching can be used with the `-mode upgrade` option. However, when the database is moved to a different system, AutoUpgrade is unable to perform a restore of the database. In that case, the upgrade options for patching follow the same rules that apply for upgrading your database.

- In describing AutoUpgrade, this documentation generally refers to AutoUpgrade performing upgrades. When AutoUpgrade performs patching, patching is functionally similar to upgrades. Accordingly, references to upgrades in this guide or in diagrams are applicable to both upgrade and patching with AutoUpgrade Patching.

- Performing patching with AutoUpgrade Patching supports all AutoUpgrade `-mode` options except the `preupgrade` mode, which is only supported for upgrades.

- When patching or upgrading relocatable PDBs the configuration file cannot contain a mixture of patch clone PDBs and upgraded clone PDBs. The configuration for the clone PDBs must be either all upgrade clones, or all patched clones.

- AutoUpgrade patching supports only one `catctl_options` setting, `-n ``number`, where `number` is the number of processes to use for parallel operations. The `catctl_options=-n` setting enables you to control the total number of PDBs that you want to run concurrently during the patching process. The default is `CPU_COUNT` divided by 2. For example if `CPU_COUNT` is set to 24 then by default, 12 PDBs (Datapatch instances) can run concurrently during the patching process.

  To overwrite the default, add `prefix``.catctl_options` to your configuration file with a value for the number of concurrent Datapatch instances you want to run. For example, to configure AutoUpgrade to run 6 PDBs (Datapatch instances) for the patch operations specified with the prefix `sales`, overriding the default, add the following line to your configuration file:

      sales.catctl_options=-n 6

  **Caution:**

  For 19.13 and earlier release updates (RUs), Oracle strongly recommends that you set the `catctl_options` parameter for patching operations.

  With 19.13 and earlier RUs, the default value of SQL\*Plus processors allocated to each Datapatch instance is `CPU_COUNT` multiplied by two (CPU_COUNT\*2) processors for each Datapatch instance that AutoUpgrade starts. This default SQL\*Plus processor allocation can quickly overload your system. To restrict system resources allocated to the patch operation, restricting how many Datapatch instances running simultaneously is the only option. For RU 19.13 and later, only one SQL\*Plus process is started for each instance of Datapatch. This change enables AutoUpgrade to run more PDBs in parallel without consuming a large amount of system resources.

#### Security Characteristics of AutoUpgrade Patching

- The user running AutoUpgrade Patching must have the `SYSDBA` system privilege to log into the database, and run the patching operation. For an Oracle Real Application Clusters database, the user must be the owner of the source and target Oracle Database Oracle homes.
- The same security rules that apply for upgrades also apply with AutoUpgrade Patching.

#### Performance Characteristics of AutoUpgrade Patching

- The speed of deploying an RU or MRP depends on the number of PDBs in a CDB, and on changes in the release update or release update revision. If the number of changes from the source RU or MRP patches are relatively few, then deployment of patches should be quick. If the patches have many changes, then applying the patches requires more time.
- Because AutoUpgrade Patching includes a number of additional automated procedures, release update deployment is slightly slower than running Datapatch manually. For example, AutoUpgrade Patching automatically includes recompiling invalid objects, and configuring Oracle RAC management on the target system.

#### What Happens If AutoUpgrade Patching Rolls Back a Release Update

- AutoUpgrade uses the Guarantee Restore Point (GRP) generated during the patch process to roll back to the earlier release Oracle home.
- If no GRP is created, then AutoUpgrade automatically calls Datapatch to rollback the changes.

**Related Topics**

- [Mike Dietrich Upgrade Your Database Now: AutoUpgrade's Patching: the feature you waited for](https://mikedietrichde.com/2024/10/28/autoupgrades-patching-the-feature-you-waited-for/)
- [Daniel Overby Hansen Databases are Fun: How To Roll Back After Patching](https://dohdatabase.com/2025/01/13/how-to-roll-back-after-patching/)

**Parent topic:** AutoUpgrade Patching

### AutoUpgrade Patching Stages and Workflows

AutoUpgrade Patching supports three different job modes. Each mode runs a different set of stages.

AutoUpgrade Patching supports four different job modes. Each mode runs a different set of stages. In AutoUpgrade Patching operations, there are four job modes, with AutoUpgrade stages that are completed in these modes:

- Analyze: In this mode, the PRECHECKS stage is run.
- Fixups: In this mode, the PRECHECKS and PREFIXUPS stages are run.
- Deploy: In this mode, the following stages are run: GRP, PREACTIONS, PRECHECKS, PREFIXUPS, EXTRACT, DBTOOLS, INSTALL, ROOH (Optional), OH_PATCHING, OPTIONS, ROOTSH (Optional), DB_PATCHING, POSTCHECKS, POSTFIXUPS, UPGRMAN (Optional), POSTACTIONS, and DROPGRP.
- create_home: In this mode, the following stages are run: EXTRACT, DBTOOLS, INSTALL, ROOH (Optional), OH_PATCHING, OPTIONS, ROOTSH (Optional).

The stages performed during AutoUpgrade Patching are consistent with stages performed in other AutoUpgrade operations,but the descriptions that follow provide you with further information in a patching context.

#### Processes Performed During AutoUpgrade Patching Stages

**Note:**

Actual step labels can vary depending on your patching choices and version of AutoUpgrade.

- GRP When `restoration=YES` is set in the AutoUpgrade configuration file, creates a Guaranteed Restore Point (GRP) in the database before applying the patches.
- PREACTIONS Runs any actions defined by the `before_action` parameter in the AutoUpgrade configuration file.
- PRECHECKS Runs the patching prechecks.
- PREFIXUPS Runs the fixups for any failing prechecks that have an automated fixup.
- EXTRACT Extracts the base image that will be used to create the new target Oracle home.
- DBTOOLS Installs a newer version of OPatch into the target Oracle home, if necessary.
- INSTALL Installs the new target Oracle home by running `runInstaller` in silent mode.
- ROOH (Optional) Installs the read-only Oracle home.
- OH_PATCHING Installs each of the necessary patches into the Oracle home.
- OPTIONS Synchronizes the binary options from the source `ORACLE_HOME` with the newly created target `ORACLE_HOME`. The supported options include the following:
  - `ASM` (Oracle Automatic Storage Management)
  - `OLAP` (Online Analytic Processing)
  - `PART` (Partitioning)
  - `RAT` (Oracle Real Application Testing)
  - `UNIAUD` (Unified Auditing)
- ROOTSH (Optional) Uses `sudo` to run the `root.sh` script from the target ORACLE_HOME as well as the `orainstRoot.sh` script when needed. If `sudo` requires a password, then running this script will fail, and reminders are given to the user to run these scripts after patching is complete.
- DB_PATCHING Runs a second copy of AutoUpgrade without the `-patch` option to move the database from the source Oracle home to the target Oracle home.
- POSTCHECKS Runs the patching postchecks.
- POSTFIXUPS Runs the fixups for any failing postchecks that have an automated fixup.
- UPGRMAN (Optional): Perform manual upgrades.
- POSTACTIONS Runs any actions defined by the `after_action` parameter in the AutoUpgrade configuration file.
- DROPGRP Drops the guaranteed restore point (GRP) if one was created by AutoUpgrade Patching, and if `drop_grp_after_patching=YES` is set in the AutoUpgrade configuration file.

#### AutoUpgrade Patching Status and Progress Files

Status and progress files are available in the directory that you specify in the AutoUpgrade configuration file with the configuration parameter `global.global_log_dir`. The location of these files are placed as follows, where `global-log` is the directory path specified by `global.global_log_dir`:

    global_log/cfgtoollogs/patch/auto/status/

#### AutoUpgrade with the -patch parameter

**Note:**

Oracle recommends that you use Oracle Fleet Patching and Provisioning (FPP) for Oracle Real Application Clusters and deployments with Oracle Data Guard.

AutoUpgrade patching using the `-patch` parameter performs out-of-place patch maintenance, which is Oracle's recommended method of patching. In out-of-place patching, AutoUpgrade creates a new target Oracle home using a base image of the database's initial release. It installs the patches that you specify, and then moves the source database to the new target Oracle home. In addition, you can use AutoUpgrade for patch maintenance for database releases where you are unable to use FPP or DBCA.

To use AutoUpgrade patching, your system should be consistent with the following requirements:

- Single-Instance Oracle Database
- Oracle Release 19c (19.3) or later release

**Parent topic:** AutoUpgrade Patching

### PDB Priority and AutoUpgrade

For both AutoUpgrade patching and upgrades, AutoUpgrade honors how PDBs will be prioritized by setting the priority on specifuc PDBs.

The priority set on each of the PDBs is used to determine which PDBs will be patched or upgraded first. For both patching and upgrades, the control structure `CDB$ROOT` and the template structure `PDB$SEED` will always be updated first. All other PDBs will be updated after CDB\$ROOT is updated. PDB\$SEED will always be processed in the first batch. When priority is set on PDBs, the PDBs are updated in priority order. For example, PDBs with priority 3 will be processed before PDBs with priority 4. PDBs with no priority will be processed last.

This AutoUpgrade feature is supported for Oracle Database 12c release 2 and later releases.

**Related Topics**

- [To Set the Priority of a PDB](../multi/index.md)

**Parent topic:** AutoUpgrade Patching

### Configuration Parameters and Command-Line Options for AutoUprade Patching

In addition to other configuration file parameters and command-line options, there are specific parameters and options for AutoUpgrade Patching.

To specify the AutoUpgrade Patching process options, you use configuration parameters that apply specifically patching.

**Note:**

AutoUpgrade Patching requires the Oracle Database 19.3 base image to be available in the directory specified by the `folder` configuration parameter. The base image can not be automatically downloaded by AutoUpgrade Patching, but can be done manually from this link:

<https://www.oracle.com/database/technologies/oracle19c-linux-downloads.html>

Downloading the Oracle Database 19.3 base image is a one-time operation. The same base image can be reused for all out-of-place patching options that are performed by AutoUpgrade Patching.

Table 3-1 AutoUpgrade Patching Configuration File Parameters

| Parameter  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|:-----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `folder`   | Specifies the directory that contains the patch zip files as well as the required base image. There is no default value. You must provide the directory path.<br>When `download=YES`, this is the directory to which the patches will be downloaded<br>When `download=NO`, this is the directory that must contain the patches that have been manually downloaded.<br>The directory that you specify with the `folder` parameter must contain the base image of the source database's release (for example, Oracle Database Release 19.3).                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `patch`    | A comma-delimited list of the patches that you want to install.<br>Note: When `method=outofplace` is set, then the patch list must include `RU`,`OPATCH`<br>The default value is `RECOMMENDED`.<br>Supported value:<br>`RECOMMENDED`: Alias for all of the following options: `RU`, `OPATCH`, `OJVM`, `DPBP`.<br>`RU`: Latest release update<br>`RU:x.y`: A release update (RU) of the specified release version, where `x` is the major release number, and `y` is the RU. For example: `RU:19:24`<br>`OPATCH`: Use latest version of OPatch<br>`OJVM`: Apply the Oracle Java VM patch that applies to the specified RU.<br>`OJVM:x.y`: Apply the Oracle Java VM patch of the specified release version, where `x` is the major release number, and `y` is the RU. For example: `RU:19.24`<br>`DPBP`: Apply the Oracle Data Pump patch for the specified RU<br>`patch-number`: Provide a specific one-off patch number. For example: `upg1.patch=p12345678` |
| `download` | Specifies whether to automatically download patches from My Oracle Support. The default is YES.<br>When set to YES, you must also load the My Oracle Support (MOS) credentials into AutoUpgrade Patching using the `-load_password` command-line option.<br>The patches that are downloaded are placed into the directory folder specified by the `folder` parameter.<br>If proxy information is required to connect to My Oracle Support, then set proxy values using the Linux operating system environment variables `https_proxy`, `http_proxy`, and `no_proxy`. The supported format of the proxy definition is as follows, where `user_info` is a user account, `site` is a URL, and `port` is a designated port for the proxy listener:<br>`[https|http|socks5|socks]://(``user_info``@)``site``:``port`<br>Adding `user_info `to the proxy definition is optional, and has a format of username:password for the credentials of the proxy.           |
| `method `  | Specifies whether to create a new target Oracle home, and if so, how it will be created. The default value is `OUTOFPLACE`.<br>`OUTOFPLACE`: Creates a new target Oracle home using the base image contained in the directory specified by the `folder` parameter.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |

For AutoUpgrade Patching, you must specify the following command-line options:

Table 3-2 AutoUpgrade Patching Command-Line Options

| Command-Line Option | Description                                                                                                                                                                                                                                                                                                   |
|:--------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `target_home`       | Specifies the directory that will be used to create the new target Oracle home.<br>This directory will be created by AutoUpgrade Patching and should not exist or be empty. Ensure that the location you specify on the filesystem contains sufficient free disk space for the creation of a new Oracle home. |
| `sid`               | Specifies the ORACLE_SID value of the source database.<br>If you specify `-config_values` and the `ORACLE_SID` Linux environment variable is defined, then this parameter becomes optional.                                                                                                                   |
| `source_home`       | Specifies the Oracle home value of the source database.<br>If you specify `-config_values` and the `ORACLE_HOME` Linux environment variable is defined, then this parameter becomes optional.                                                                                                                 |
| `keystore`          | Specifies the secure directory (keystore) that will contain the keystore files.<br>If you specify `DOWNLOAD=NO`, then this parameter becomes optional.                                                                                                                                                        |

**Parent topic:** AutoUpgrade Patching

### AutoUpgrade Patching Configuration Files and Log Files

See examples of configuration files and log files for AutoUpgrade Patching.

An AutoUpgrade Patching configuration file is essentially the same as an AutoUpgrade configuration file for upgrades. However, instead of AutoUpgrade using the parameters you specify to perform an upgrade, AutoUpgrade performs a patch operation from a source Oracle Database patch release to a target Oracle Database patch release, and AutoUpgrade runs Datapatch as part of the procedure.

Example 3-10 AutoUpgrade Configuration Files for Different Patching Scenarios

In the following configuration file examples, the following Oracle Databases are patched from Oracle Database 19c patched to Release Update (RU) 11 to 19c RU 13:

- A non-CDB database patched from 19.11.0 to 19.13.0, designated with the prefix `patch1`
- An Oracle Database 19c CDB patched from 19.11 to 19.13, designated with the prefix `patch2`
- An encrypted PDB patched by unplug-plug, designated with the prefix `patch3`
- A non-CDB, which is patched and converted to a CDB, designated with the prefix `patch4`
- A CDB with a PDB that is relocated during the patching operation, designated with the prefix `patch5`
- An Oracle Real Application Clusters (Oracle RAC) database, designated with the prefix `patch6`
- An Oracle RAC database in a distributed cluster configuration, designated with the prefix `patch7`

<!-- -->

    #
    # Global log directory for patch logs
    #
    global.autoupg_log_dir=/databases/patchlogs
    #
    # Non-CDB patch to Non-CDB patch, source and target home
    #
    patch1.sid=db19
    patch1.source_home=/databases/ee/product/1911/dbhome_1
    patch1.target_home=/databases/ee/product/1913/dbhome_2
    #
    #
    # CDB patch, Source and Target home
    #
    patch2.sid=cdb19
    patch2.source_home=/databases/ee/product/1911/dbhome_1
    patch2.target_home=/databases/ee/product/1913/dbhome_2
    #
    # Unplug-Plug with KeyStore
    #
    global.keystore=/databases/tde
    patch3.sid=cdb19
    patch3.source_home=/databases/ee/product/1911/dbhome_1
    patch3.target_home=/databases/ee/product/1913/dbhome_2
    patch3.target_cdb=cdb1913
    patch3.target_pdb_name=sales
    patch3.target_pdb_copy_option=file_name_convert=('/databases/ee/oradata/CDB19/sales', '/databases/ee/oradata/CDB1913/sales')
    #
    # Non-CDB to CDB, Source and Target home
    #
    patch4.sid=db19
    patch4.source_home=/databases/ee/product/1911/dbhome_1
    patch4.target_home=/databases/ee/product/1913/dbhome_2
    patch4.target_cdb=cdb1913
    patch4.target_pdb_name=emp
    patch4.target_pdb_copy_option=file_name_convert=('/databases/ee/oradata/DB19', '/databases/ee/oradata/CDB1913/emp')
    #
    # Patch relocate DB
    #
    patch5.sid=cdb19
    patch5.source_home=/databases/ee/product/1911/dbhome_1
    patch5.target_home=/databases/ee/product/1913/dbhome_2
    patch5.target_cdb=cdb1913
    patch5.pdbs=cars
    patch5.target_pdb_copy_option.cars=file_name_convert=('/databases/ee/oradata/CDB19/cars', '/databases/ee/oradata/CDB1913/cars')
    patch5.source_dblink.cars=db19_link
    #
    # Oracle RAC
    #
    patch6.sid=rac1
    patch6.source_home=/databases/ee/product/1911/dbhome_1
    patch6.target_home=/databases/ee/product/1913/dbhome_2
    #
    # Distributed Oracle RAC with proactive fixups
    #
    patch7.sid=rac2
    patch7.source_home=/databases/ee/product/1911/dbhome_1
    patch7.target_home=/databases/ee/product/1913/dbhome_2
    patch7.tune_setting=distributed_upgrade=true

Example 3-11 A Summary Log File for AutoUpgrade Patching

In this patching summary report file, you can see how AutoUpgrade applies patches to the CDB and PDBs.

    ********************************************************************************
            Datapatch Apply Summary Report for CDB$ROOT

        Return code        = 0 SUCCESS
        Failure reason     = null
        Total time         = 161.721805095673
        Install patches    = 1
        Database Open      = SUCCESS
        Invocation Log     = /databases/cfgtoollogs/sqlpatch/sqlpatch_17781_2022_05_18_10_57_58/sqlpatch_invocation.log
        Bootstrap Required = 1
        Bootstrap Status   = SUCCESS
        Bootstrap Log      = /databases/cfgtoollogs/sqlpatch/sqlpatch_17781_2022_05_18_10_57_58/bootstrap1_CDB19X_CDBROOT.log
        Total patches      = 1

        Patch Key          = 33192793-24462514
        Mode               = apply
        Status             = SUCCESS
        Patch Log File     = /databases/cfgtoollogs/sqlpatch/33192793/24462514/33192793_apply_CDB19X_CDBROOT_2022May18_10_58_06.log
        RU Log File        = /databases/cfgtoollogs/sqlpatch/33192793/24462514/33192793_ru_apply_CDB19X_CDBROOT_2022May18_10_58_05.log
        RU Errors          = N/A

    ********************************************************************************
            Datapatch Apply Summary Report for PDBX

        Return code        = 0 SUCCESS
        Failure reason     = null
        Total time         = 123.969398021698
        Install patches    = 1
        Database Open      = SUCCESS
        Invocation Log     = /databases/cfgtoollogs/sqlpatch/sqlpatch_18416_2022_05_18_11_01_40/sqlpatch_invocation.log
        Bootstrap Required = 1
        Bootstrap Status   = SUCCESS
        Bootstrap Log      = /databases/cfgtoollogs/sqlpatch/sqlpatch_18416_2022_05_18_11_01_40/bootstrap1_CDB19X_PDBX.log
        Total patches      = 1

        Patch Key          = 33192793-24462514
        Mode               = apply
        Status             = SUCCESS
        Patch Log File     = /databases/cfgtoollogs/sqlpatch/33192793/24462514/33192793_apply_CDB19X_PDBX_2022May18_11_01_55.log
        RU Log File        = /databases/cfgtoollogs/sqlpatch/33192793/24462514/33192793_ru_apply_CDB19X_PDBX_2022May18_11_01_55.log
        RU Errors          = N/A

    ********************************************************************************
            Datapatch Apply Summary Report for PDB$SEED

        Return code        = 0 SUCCESS
        Failure reason     = null
        Total time         = 124.234117984772
        Install patches    = 1
        Database Open      = SUCCESS
        Invocation Log     = /databases/cfgtoollogs/sqlpatch/sqlpatch_18406_2022_05_18_11_01_40/sqlpatch_invocation.log
        Bootstrap Required = 1
        Bootstrap Status   = SUCCESS
        Bootstrap Log      = /databases/cfgtoollogs/sqlpatch/sqlpatch_18406_2022_05_18_11_01_40/bootstrap1_CDB19X_PDBSEED.log
        Total patches      = 1

        Patch Key          = 33192793-24462514
        Mode               = apply
        Status             = SUCCESS
        Patch Log File     = /databases/cfgtoollogs/sqlpatch/33192793/24462514/33192793_apply_CDB19X_PDBSEED_2022May18_11_01_55.log
        RU Log File        = /databases/cfgtoollogs/sqlpatch/33192793/24462514/33192793_ru_apply_CDB19X_PDBSEED_2022May18_11_01_55.log
        RU Errors          = N/A

**Parent topic:** AutoUpgrade Patching

### AutoUpgrade Patching Workflow Examples

Use this example of an AutoUpgrade patching workflow to understand the AutoUpgrade patching procedure.

In this scenario, you use AutoUpgrade Patching to download the patch, deploy the patch, and start the patching operation.

Example 3-12 Configuration files for AutoUpgrade Patching

You can choose to have AutoUpgrade patching to download patches, or you can first download patches manually and then run AutoUpgrade patching.

In the following configuration file example, we set the download option for job `upg1` to `YES`:

    global.global_log_dir=/logs/patching
    global.keystore=/secure/keystore
    upg1.sid=DB19X
    upg1.source_home=/databases/19x/dbhome_1
    upg1.target_home=/databases/19x/dbhome_2
    upg1.folder=/storage/patches
    upg1.download=YES

In the following configuration file example, we set the download option for job `upg1` to `NO`:

    global.global_log_dir=/logs/patching
    upg1.sid=DB19X
    upg1.source_home=/databases/19x/dbhome_1
    upg1.target_home=/databases/19x/dbhome_2
    upg1.folder=/storage/patches
    upg1.patch=RU,OPATCH
    upg1.download=NO

Example 3-13 AutoUpgrade Patching Download Option

To enable AutoUpgrade patching to automatically download patches, you have to set the download parameter in the configuration file for the job running the patch. As AutoUpgrade runs, all identified patches will be automatically downloaded and verified. If a patch is already in the directory that you defined in the configuration file using the `folder` configuration parameter, then download of that patch will be skipped. If a proxy is needed to connect to My Oracle Support, then you can set the Linux environment variables `https_proxy`, `http_proxy` and `no_proxy` so that AutoUpgrade can connect to Oracle Support.

Complete this procedure:

1.  Ensure that the configuration file uses the `download=YES` option, or leave this option unspecified; the default value will include it. The global keystore parameter will also be required.

    For example:

        global.global_log_dir=/logs/patching
        global.keystore=/secure/keystore
        . . .
        upg1.sid=DB19X
        upg1.source_home=/databases/19x/dbhome_1
        upg1.target_home=/databases/19x/dbhome_2
        upg1.folder=/patches
        upg1.patch=RECOMMENDED
        upg1.download=YES

2.  Load the My Oracle Support credentials into the keystore by using the `-load_password` command line option:

        java -jar autoupgrade.jar -patch -config config.cfg -load_password

    When the password console loads, add the necessary My Oracle Support credentials by using the `add` option.

    For example:

        MOS> group MOS
        MOS> add -user user@company.com
            Enter your secret/Password:
            Re-enter your secret/Password:
        MOS> list
            MOS Credentials Loaded - Connection Successful

3.  Run AutoUpgrade Patching in any of the supported modes: ANALYZE, FIXUPS, DEPLOY, DOWNLOAD, CREATE_HOME.

    For example, run the analyze mode:

        java -jar autoupgrade.jar -patch -config config.cfg -mode analyze

Example 3-14 AutoUpgrade Patching Deploy Option

After you have loaded My Oracle Support credentials into the keystore, you can patch the source database using the DEPLOY option.

In the following example, using the same configuration file (`config.cfg`) for the 19X database shown in the previous example, we deploy the patches with AutoUpgrade:

    java -jar autoupgrade.jar -patch -config config.cfg -mode deploy

The console output for this example operation is as follows:

       AutoUpgrade Patching 24.1.240816 launched with default internal options
       Processing config file ...
       Loading AutoUpgrade Patching keystore

       -----------------------------
       Downloading files to /patches
       -----------------------------
       DATABASE RELEASE UPDATE 19.24.0.0.0
           File: p36582781_190000_Linux-x86-64.zip - VALIDATED

       DATAPUMP BUNDLE PATCH 19.24.0.0.0
           File: p36682332_1924000DBRU_Generic.zip - VALIDATED

       OJVM RELEASE UPDATE 19.24.0.0.0
           File: p36414915_190000_Linux-x86-64.zip - VALIDATED

       OPatch 12.2.0.1.43 for DB 19.0.0.0.0 (Jul 2024)
           File: p6880880_190000_Linux-x86-64.zip - VALIDATED
       -----------------------------

       +-----------------------------------------+
       | Starting AutoUpgrade Patching execution |
       +-----------------------------------------+
       1 Non-CDB(s) will be processed
       Type 'help' to list console commands
       patch> Job 100 completed
       ------------------- Final Summary --------------------
       Number of databases            [ 1 ]

       Jobs finished                  [1]
       Jobs failed                    [0]
       Jobs restored                  [0]
       Jobs pending                   [0]

       ---- Drop GRP at your convenience once you consider it is no longer needed ----
       Drop GRP from DB19X: drop restore point AU_PATCHING_9212_DB19X1919000

       Please check the summary report at:
       /logs/patching/cfgtoollogs/patch/auto/status/status.html
       /logs/patching/cfgtoollogs/patch/auto/status/status.log


**Parent topic:** AutoUpgrade Patching
