The table below is a worksheet that lists all of the parameter names and the reasons that you will need them for configuring the gateway and TCP/IP. Use the worksheet to gather the specific information that you need before you begin the configuration process.

Table D-1 List of Parameters Needed to Configure Oracle Database Gateway for DRDA

| Reason                              | Name of Parameter(s) Needed                                                                                                                                                | Your Specific Parameters Here |
|:------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:------------------------------|
| Oracle home of the gateway          | `ORACLE_HOME`                                                                                                                                                              | \-                            |
| System ID of the gateway            | `ORACLE_SID`                                                                                                                                                               | \-                            |
| Configuring TCP/IP                  | • Local Host name, Domain Name<br>• IP Address<br>• Network Mask<br>• Name Server IP Address<br>• DRDA server Host name or IP Address<br>• DRDA server Service Port Number | \-                            |
| Recovery user ID                    | `HS_FDS_RECOVERY_ACCOUNT`                                                                                                                                                  | \-                            |
| Recovery Password                   | `HS_FDS_RECOVERY_PWD`                                                                                                                                                      | \-                            |
| Remote Database Name                | `DRDA_REMOTE_DB_NAME`                                                                                                                                                      | \-                            |
| Connection Parameter                | `DRDA_CONNECT_PARM`                                                                                                                                                        | \-                            |
| Remote collection ID                | `HS_FDS_PACKAGE_COLLID`                                                                                                                                                    | \-                            |
| Remote package name                 | `DRDA_PACKAGE_NAME `                                                                                                                                                       | \-                            |
| Owner ID of DRDA package            | `DRDA_PACKAGE_OWNER`                                                                                                                                                       | \-                            |
| DB Name used with Oracle database   | `HS_DB_NAME`                                                                                                                                                               | \-                            |
| DB Domain used with Oracle database | `HS_DB_DOMAIN`                                                                                                                                                             | \-                            |

**Note:**

The user ID that is used to bind or rebind the DRDA package must have the following privileges on the remote database; your database administrator will need to provide these.

- package privileges of `BIND`, `COPY`, and `EXECUTE`

- collection privilege of `CREATE` `IN`

- system privileges of `BINDADD` and `BINDAGENT`
