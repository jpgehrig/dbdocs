The table below is a worksheet that lists all of the parameter names and the reasons that you will need them for configuring the gateway and TCP/IP. Use the worksheet to gather the specific information that you need before you begin the configuration process.

Table D-1 List of Parameters Needed to Configure Oracle Database Gateway for DRDA

| Reason                              | Name of Parameter Needed           | Your Specific Parameters Here |
|:------------------------------------|:-----------------------------------|:------------------------------|
| Oracle home of the gateway          | `ORACLE_HOME`                      |                               |
| System ID of the gateway            | `ORACLE_SID`                       |                               |
| Remote collection ID                | `HS_FDS_PACKAGE_COLLID`            |                               |
| Configuring TCP/IP                  | Local Hostname, Domain Name        |                               |
| Configuring TCP/IP                  | IP Address                         |                               |
| Configuring TCP/IP                  | Network Mask                       |                               |
| Configuring TCP/IP                  | Name Server IP Address             |                               |
| Configuring TCP/IP                  | DRDA Server Hostname or IP Address |                               |
| Configuring TCP/IP                  | DRDA Server Service Port Number    |                               |
| Recovery user ID                    | `HS_FDS_RECOVERY_ACCOUNT`          |                               |
| Recovery Password                   | `HS_FDS_RECOVERY_PWD`              |                               |
| Remote Database Name                | `HS_FDS_CONNECT_INFO`              |                               |
| Owner ID of DRDA package            | `HS_FDS_PACKAGE_OWNER`             |                               |
| DB Name used with Oracle database   | `HS_DB_NAME`                       |                               |
| DB Domain used with Oracle database | `HS_DB_DOMAIN`                     |                               |

**Note:**

The user ID that is used to bind or rebind the DRDA package must have the appropriate privileges on the remote database as described in [Configuring the DRDA Server](config-drda-server.md). Your database administrator will need to provide these privileges.
