Learn how to create an Oracle Database instance using ORADIM.

To use ORADIM to create an instance, enter:

    oradim [-NEW -SID SID] | -SRVC service_name | -ASMSID SID | -ASMSRVC service_name
    [-SYSPWD password][-MAXUSERS number][-STARTMODE auto | manual] [-SRVCSTART system | demand]
    [-PFILE filename | -SPFILE] [-SHUTMODE normal | immediate | abort] [-TIMEOUT
    secs] [-RUNAS osusr[/ospass]]

For this command, note the following:

- `-NEW` indicates that you are creating a new instance. This is a mandatory parameter.

- `-SID` `SID` is the name of the instance to create.

- `-SRVC` `service_name` is the name of the service to create (`OracleService``SID`).

- `-ASMSID ``SID` is the name of the Oracle Automatic Storage Management instance to create.

- `-ASMSRVC ``service_name` is the name of the Oracle Automatic Storage Management service to create.

- `-SYSPWD` `password` is the system password.

- `-MAXUSERS` `number` is the number of users defined in the password file. The default is `5`.

- `-STARTMODE` `auto` \| `manual` indicates whether to start the instance when the Oracle Database service is started. The default is `manual`.

- `-SRVCSTART system | demand` indicates whether to start the Oracle Database service upon computer restart. Default is `demand.` Here, `system` specifies that the service be configured to automatically start when the system boots or reboots. `Demand` specifies that the user has to explicitly start the service.

- `-PFILE` `filename` is the initialization parameter file to be used with this instance. Ensure that you specify the complete path name of this file, including the drive letter.

- `-SPFILE` indicates that a server parameter file (SPFILE) be used during startup instead of a PFILE.

- `-SHUTMODE` specifies how to stop an instance. It requires an argument and the default is `immediate.` If `SHUTMODE` is omitted, then there is no attempt made to shutdown the instance when the service is shut down.

- `-TIMEOUT` `secs` sets the maximum time to wait (in seconds) before the service for a particular `SID` stops. The default is 90 seconds. It cannot be used without the `SHUTDOWN` argument.

- `-RUNAS osusr[/ospass`\] ("run as") makes it possible to specify both the Oracle Home User and its password. If the given `osusr` is different from the Oracle Home User, then the Oracle Home User is used instead of the `osusr` along with the given `ospass`.

  Though the `ospass` can be specified on the command line, Oracle recommends accepting `ospass` through `stdin.`

  ORADIM creates Oracle Database service, Oracle VSS Writer service, and Oracle Scheduler service to run under the Oracle Home User account. If this account is a Windows Local User Account or Windows Domain User Account, then ORADIM prompts for the password for that account and accepts the same through `stdin`.

**Note:**

For simplicity in demonstrating this feature, this example does not perform the password management techniques that a deployed system typically uses. In a production environment, follow the Oracle Database password management guidelines, and disable any sample accounts.

To create an instance called `PROD`, for example, enter:

    C:\> oradim -NEW -SID prod -STARTMODE auto -PFILE C:\app\username\admin\prod\pfile\init.ora

**See Also:**

[Oracle Database Security Guide](../dbseg/managing-security-for-application-developers.md) for password management guidelines and other security recommendations.

**Parent topic:** [About Administering an Oracle Database Instance Using ORADIM](about-administering-an-oracle-database-instance-using-oradim.md)
