This topic describes the gateway initialization file location and lists the gateway initialization parameters supported by the Oracle Database Gateway for APPC specifically for the SNA protocol. These parameters are fully documented in [Migrating an Existing Gateway Instance to New Release Using SNA Protocol](appc-gateway-migration.md)[Migrating an Existing Gateway Instance to New Release Using SNA Protocol](appc-gateway-migration.md). In addition, the following topic contains sample listener.ora and tnsnames files for a gateway using SNA.

The parameter file for the gateway is located in the `%ORACLE_HOME%\dg4appc\admin` directory and is called `init``sid``.ora`.

**Note:**

The `init``sid``.ora` file contains both SNA and TCP/IP parameters. You must modify these files with the suitable parameters.

### PGA Parameters

The PGA parameters control the APPC interface portion of the gateway.

PGA parameters are specified using the `SET` gateway initialization parameter. For example:

    SET pga_parm=value

where:

- `pga_parm `is one of the PGA parameter names in the list that follows; and

- `value `is a character string with contents that depend on `pga_parm`

Table A-1 provides a list of PGA parameters and their descriptions.

Table A-1 PGA Parameters for Oracle Database Gateway for APPC Using SNA

| Parameter                   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|:----------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `LOG_DESTINATION`=`logpath` | `logpath` specifies the destination at which `STDERR` is reopened. `LOG_DESTINATION` specifies a directory only and `STDERR` is reopened to `logpath\``sid_pid``.log`<br>where:<br>• `sid` is the sid name<br>• `pid` is the process ID assigned to the gateway                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `PGA_CAPABILITY`            | PGA transaction capability. This controls whether updates are allowed through the gateway. The following are valid values:<br>`READ_ONLY` or `RO`, read-only capabilities.<br>`SINGLE_SITE` or `SS`, single-site update only. This indicates that in a distributed environment, only the gateway can perform updates. No other database updates can occur within the Oracle transaction.<br>`COMMIT_CONFIRM` or `CC`, commit-confirm. This indicates that in a distributed environment, updates can be performed by both the gateway and other participants within the Oracle transaction. The gateway is always committed first in this mode, and no other commit-confirm sites are allowed to participate in the Oracle transaction.<br>The default is `SINGLE_SITE`. |
| `PGA_CONFIRM`               | Incoming `APPC` `CONFIRM` request handling option. This controls what the gateway does when an `APPC` `CONFIRM` request is received from the remote transaction program (RTP). This parameter has meaning only when the conversation is running with `SYNCLEVEL > 0`. The following are valid values:<br>`ACCEPT` - respond to incoming `APPC` `CONFIRM` requests with `APPC` `CONFIRMED` responses.<br>`REJECT` - treat incoming `APPC` `CONFIRM` requests as errors causing the conversation to be deallocated and an error message to be issued.<br>The default is `REJECT`.                                                                                                                                                                                         |
| `PGA_LOG_DB`                | The Oracle Net service name for the Oracle database in which the gateway maintains its transaction log. This parameter can be from `1` to `255` characters long. This parameter is required only when `PGA_CAPABILITY` parameter is set to ` COMMIT_CONFIRM`.<br>There is no default value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `PGA_LOG_PASS`              | The Oracle password to be used by the gateway when connecting to the Oracle database specified by the `PGA_LOG_DB` parameter. The password can be from `1` to `30` characters long. This parameter is required only when `PGA_CAPABILITY` parameter is set to `COMMIT_CONFIRM`. The password can be encrypted. For more information about encrypting the password, refer to [Passwords in the Gateway Initialization File](appc-gateway-security-requirements.md).<br>There is no default value.                                                                                                                                                                                                                                                                        |
| `PGA_LOG_USER`              | The Oracle user ID to be used by the gateway when connecting to the Oracle database specified by the `PGA_LOG_DB` parameter. The user ID can be from` 1` to `30` characters long. This parameter is required only when `PGA_CAPABILITY` parameter is set to `COMMIT_CONFIRM`.<br>There is no default value.                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `PGA_RECOVERY_PASS`         | The password to be used by the gateway when allocating an APPC conversation with the transaction specified by the ` PGA_RECOVERY_TPNAME` parameter. The password can be from `1` to `8 `characters long. This parameter is required only when `PGA_CAPABILITY` parameter is set to `COMMIT_CONFIRM` and `PGA_SECURITY_TYPE` parameter is set to `PROGRAM`. The password can be encrypted. For more information about encrypting the password, refer to [Passwords in the Gateway Initialization File](appc-gateway-security-requirements.md).<br>There is no default value.                                                                                                                                                                                             |
| `PGA_RECOVERY_TPNAME`       | The TP name of the transaction installed in the online transaction processor (OLTP) for commit-confirm `FORGET` and `RECOVERY` processing. The TP name can be from `1` to `64` characters long. For CICS Transaction Server for z/OS, the TP name is limited to four characters. For IMS/TM, the TP name is limited to eight characters. Other OLTPs might have other limits on the length of the TP name. This parameter is required only when `PGA_CAPABILITY` parameter is set to `COMMIT_CONFIRM`.<br>The default value is `RECO`.                                                                                                                                                                                                                                  |
| `PGA_RECOVERY_USER`         | The user ID to be used by the gateway when allocating an APPC conversation with the transaction specified by the `PGA_RECOVERY_TPNAME` parameter. The user ID can be from `1` to `8` characters long. This parameter is required only when `PGA_CAPABILITY` parameter is set to `COMMIT_CONFIRM` and `PGA_SECURITY_TYPE` parameter is set to `PROGRAM` or `SAME`.<br>There is no default value.                                                                                                                                                                                                                                                                                                                                                                         |
| `PGA_SECURITY_TYPE`         | APPC conversation security option. This controls what security parameters are sent to the OLTP in the FMH-5 at conversation allocation. The following are valid values:<br>`NONE`, which sends no security parameters<br>`SAME`, which sends only a user ID<br>`PROGRAM`, which sends a user ID and password<br>The default is `NONE`.<br>For further information about these options, refer to [Security Requirements](appc-gateway-security-requirements.md) .                                                                                                                                                                                                                                                                                                        |
| `TRACE_LEVEL`               | PGA trace level. This controls tracing output written to `STDERR` (the target of the `LOG_DESTINATION` parameter. The value must be an integer from `0` to `255`.<br>The default is `0`, indicating no tracing.<br>Any value between `1` and `255` will turn on tracing.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |

### PGA_CAPABILITY Parameter Considerations

When choosing a setting for the `PGA_CAPABILITY` parameter, take care to ensure that the correct setting is used based on what the RTPs will be doing.

The `READ_ONLY` setting should always be used when the RTPs are read-only, that is, when the RTPs perform no database updates. `READ_ONLY` should never be used when the RTPs perform database updates. For example, if the `READ_ONLY` setting is chosen, and if a RTP called by the gateway performs updates to a foreign database, then the Oracle database does not provide any integrity protection for those updates. Further, `READ_ONLY` mode allows a gateway transaction to be part of a distributed transaction that might update several other databases. If the gateway calls a RTP that performs updates in this situation and if a failure occurs, then the database updated by the RTP is out of sync with the other databases.

In cases where the RTPs perform updates to foreign databases, there are two options for `PGA_CAPABILITY`:

- `SINGLE_SITE`

- `COMMIT_CONFIRM`

Each of these options provides protection against data integrity problems by permitting `COMMIT` and `ROLLBACK` requests to be forwarded to the RTP and by informing the Oracle database about the distributed update and recovery capabilities of the gateway. The particular option chosen depends on the design of the RTPs and upon the capabilities of the OLTP where they execute.

If the OLTP has LU6.2 `SYNCLEVEL 1 `or `2` support, then the `COMMIT_CONFIRM` capability provides limited two-phase commit between the Oracle database and the OLTP, with the restriction that no other commit-confirm site (gateway or Oracle) can be part of the distributed transaction. If it is not possible to use `COMMIT_CONFIRM`, then the `SINGLE_SITE` capability provides update capability between the Oracle database and the OLTP, with the restriction that only the OLTP can perform updates, and no updates can occur on the Oracle side.

Each of the `PGA_CAPABILITY` options for update control imposes specific requirements on the RTP and on the OLTP. For `COMMIT_CONFIRM` capability, these requirements are discussed in detail in Chapter 5, "Implementing Commit-Confirm," of the [Oracle Database Gateway for APPC User's Guide](../appug/implement-appc-commit-confirm-sna-only.md). Also refer to [Configuring the OLTP for Commit-Confirm](configure-appc-gateway-using-sna.md)[Configuring the OLTP for Commit-Confirm](configure-appc-gateway-using-sna.md) in this guide. For `SINGLE_SITE` capability, the RTP is responsible for performing the suitable tasks in response to `COMMIT` and `ROLLBACK` requests received from the gateway on behalf of the Oracle database . The gateway uses the `APPC` `CONFIRM` and `SEND_ERR` requests to implement `COMMIT` and `ROLLBACK`, respectively. On receipt of a `CONFIRM` command, the RTP must perform `COMMIT` processing and then respond to the gateway with an `APPC` `CONFIRMED` response. On receipt of a `SEND_ERR` command, the RTP must perform `ROLLBACK` processing.

Because the distributed transaction capability of the Oracle database is affected by the `PGA_CAPABILITY` option used by the gateway, it is desirable to separate inquiry and update applications by using different gateway instances for each. One gateway can be defined with `PGA_CAPABILITY` set to `READ_ONLY` and others with `PGA_CAPABILITY` set to `SINGLE_SITE` or `COMMIT_CONFIRM`.

This allows read-only transaction programs to participate in distributed transactions under the control of the Oracle database . For example, data from DB2 can be retrieved through the `READ_ONLY` gateway by an inquiry-only RTP, and can then be used as input to database updates on the Oracle database , all in one Oracle transaction. A `SINGLE_SITE` gateway can be used only for accessing RTPs which perform updates to foreign databases outside the scope of control of the Oracle database . Data can be read from any databases accessible to the Oracle database , and that data can be used to perform updates through the gateway.

When it is necessary to update resources on both the Oracle side and the OLTP side, a `COMMIT_CONFIRM` gateway can be used, provided that the OLTP and the RTPs are set up to implement `COMMIT_CONFIRM`.

All that is necessary to set up multiple gateway instances is to set up the following for each instance:

- an entry in the `listener.ora `file defining the `sid` of the gateway instance

- an entry in the `tnsnames.ora` file defining an alias to be used to connect to the gateway instance defined in `listener.ora`

- a database link in the Oracle database that specifies the alias defined in the `tnsnames.ora` file in its `USING` parameter.

Note that the gateway instances can share one common directory structure and use the same executables.

For example, to set up two gateways, `PGAI` and `PGAU` (for inquiry and update use, respectively), the following steps are required:

1.  Define entries in `listener.ora` for two `sid`s, `PGAI` and `PGAU`.

2.  Define two aliases in `tnsnames.ora` that connect to the two new `sid`s, `PGAI` and `PGAU`.

3.  Define two database links in the Oracle database , one connecting to `PGAI` and the other connecting to `PGAU`.

4.  Finally, create the initialization files `initPGAI.ora` and` initPGAU.ora`.

    In `initPGAI.ora`, set `PGA_CAPABILITY` to `READ_ONLY`, and in `initPGAU.ora`, set `PGA_CAPABILITY` to `SINGLE_SITE` or `COMMIT_CONFIRM`. Then, use the `PGAI` gateway for inquiry-only transactions, and use the `PGAU` gateway for update transactions.

    The same steps can be used to set up additional gateway instances.

### PGA_CONFIRM Parameter Considerations

When deciding upon the setting for the `PGA_CONFIRM` parameter, it is important to understand the effects of each setting. First, keep in mind that this parameter affects only those conversations running at `SYNCLEVEL 1`. The default setting, `PGA_CONFIRM=REJECT`, is suitable for most applications. With this setting, the gateway generates an error if a `CONFIRM` request is received from the remote transaction program. If you have a remote transaction that uses `CONFIRM` to verify that data was received by the gateway, then you must use `PGA_CONFIRM=ACCEPT` to allow the gateway to respond to those incoming `CONFIRM` requests with `CONFIRMED` responses. You must be aware that the gateway sends `CONFIRM` requests to the remote transaction when the Oracle application has issued a `COMMIT` request. In order for the `COMMIT` processing to work correctly, the remote transaction must be written to perform its local commit processing whenever a `CONFIRM` request is received from the gateway, and respond to the gateway with `CONFIRMED` after the commit processing has successfully completed. If an error occurs during commit processing, then the remote transaction must respond to the gateway with `SEND_ERR` to indicate that the commit failed.

One special case for the use of `PGA_CONFIRM=ACCEPT` is with IMS/TM version 7. When using the implied APPC support that is provided by IMS/TM version 7, conversations that run at `SYNCLEVEL 1 `are handled differently than conversations that run at `SYNCLEVEL 0.` IMS/TM automatically generates `CONFIRM` requests after each `APPC` `SEND` when the conversation is at `SYNCLEVEL 1`. On the gateway side, if `PGA_CONFIRM=ACCEPT` is not specified, then the `CONFIRM` requests sent by IMS/TM result in errors generated by the gateway. Using `PGA_CONFIRM=ACCEPT` alleviates this problem, allowing the gateway to respond to incoming `CONFIRM` requests with `CONFIRMED` responses. The only limitation with running this way is that the implied APPC support provided by IMS does not notify the application when a `CONFIRM` request is received from the gateway. This means that the gateway cannot use `CONFIRM` to implement `COMMIT`, thereby disabling the use of `COMMIT/ROLLBACK` to control updates on the IMS side of the conversation.

### Sample listener.ora File for a Gateway Using SNA

    LISTENER =
      (ADDRESS_LIST =
            (ADDRESS=
              (COMMUNITY= TCP.world)
              (Host = bay)
              (PROTOCOL= TCP)
              (Port= 2621)
            )
            (ADDRESS=
              (COMMUNITY= TCP.world)
              (Host = bay)
              (PROTOCOL= TCP)
              (Port= 2623)
            )
      )

    SID_LIST_LISTENER =
      (SID_LIST =
        (SID_DESC =
          (SID_NAME = PGA)
          (ORACLE_HOME = C:\oracle\pga\12.2)
          (PROGRAM = pg4asrv)
        )
      )

### Sample tnsnames.ora File for a Gateway Using SNA

    ORA920 =
      (DESCRIPTION =
        (ADDRESS_LIST =
          (ADDRESS = (PROTOCOL = TCP)(HOST = bay.us.example.com)(PORT = 1521))
        )
        (CONNECT_DATA =
          (SERVER = DEDICATED)
          (SERVICE_NAME = ORA920.bay)
        )
      )

    PGA =
      (DESCRIPTION =
        (ADDRESS_LIST =
          (ADDRESS = (PROTOCOL = TCP)(HOST = bay)(PORT = 2621))
        )
        (CONNECT_DATA =
          (SID = PGA)
        )
        (HS = OK)
      )
