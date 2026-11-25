Learn how to edit an instance to change such values as instance name, startup mode, shutdown mode, and shutdown type using ORADIM.

To use ORADIM to modify an instance, enter:

    oradim -EDIT -SID SID | -ASMSID SID [-SYSPWD password] [-STARTMODE auto |
    manual] [-SRVCSTART system | demand] [-PFILE filename | -SPFILE][SHUTMODE normal
    | immediate | abort] [SHUTTYPE srvc | inst | srvc,inst]

For this command, note the following:

- `-EDIT` indicates that you are modifying an instance. This is a mandatory parameter.

- `-SID` `SID` specifies the name of the instance to modify. This is a mandatory parameter.

- `-ASMSID ``SID` is the name of the Oracle Automatic Storage Management instance to modify.

- `-STARTMODE` indicates whether to start the instance when the Oracle Database service is started. The default is `manual`.

- `-SRVCSTART system | demand` indicates whether to start the Oracle Database service on computer restart. The default is `demand.`

- `-PFILE` `filename` specifies the initialization parameter file to be used with this instance. Ensure that you specify the complete path name of this file, including the drive letter.

- `-SPFILE` indicates that a server parameter file (SPFILE) be used during startup instead of a PFILE.

- `-SHUTMODE` specifies how to stop an instance. This is an optional parameter. If you do not specify how to stop an instance, then `immediate` is the default mode.

- `-SHUTTYPE` indicates whether to stop the service or the instance. One or both values can be specified. If it is not specified, then the registry is checked for the current setting.

To specify a new initialization parameter file for the instance `prod`, for example, enter:

    C:\> oradim -EDIT -SID prod -PFILE C:\app\username\product\12.2.0\admin\lynx\pfile\init.ora

**Parent topic:** [About Administering an Oracle Database Instance Using ORADIM](about-administering-an-oracle-database-instance-using-oradim.md)
