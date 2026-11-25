The following topics describe the parameters needed for a gateway featuring the TCP/IP for IMS Connect communication protocol. It also provides a sample output of the `pg4tcpmap` tool. In addition, the topics contain sample `listener.ora` and `tnsnames.ora` files for a ­gateway using TCP/IP. It contains the following sections:

- Gateway Initialization Parameter File Using TCP/IP

- Output for the pg4tcpmap Tool

### Gateway Initialization Parameter File Using TCP/IP

The parameter file for the Oracle Database Gateway for APPC using TCP/IP for IMS Connect is located in the `$ORACLE_HOME/dg4appc/admin` directory and is called `init``sid.``ora`.

**Note:**

The `init``sid.``ora` file contains both SNA and TCP/IP parameters. You will need to modify these files with the suitable parameters.

#### PGA Parameters

The PGA parameters control the TCP/IP interface portion of the gateway. PGA parameters are specified using the `SET` gateway initialization parameter. For example:

    SET pga_parm=value

where:

- `pga_parm `is one of the PGA parameter names in the list that follows

- `value` is a character string with contents that depend on `pga_parm`

Table B-1 provides a list of PGA parameters and their descriptions.

Table B-1 PGA Parameters for Oracle Database Gateway for APPC Using TCP/IP for IMS Connect

| Parameter                     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|:------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `LOG_DESTINATION``=``logpath` | `logpath` specifies the destination at which `STDERR` is reopened. `LOG_DESTINATION` specifies a directory only and `STDERR` is reopened to `logpath/``sid_pid``.log`<br>where:<br>• `sid` is the sid name<br>• `pid` is the process ID assigned to the gateway<br>NOTE: This parameter will be used for the `pg4tcpmap` tool when you set the Trace Level to `255`. The log file for this tool will reside in the same place as the gateway log file, in `pg4tcpmap_``sid``.log`.                                                                                                                                                                                                                                                                                                                                                                 |
| `PGA_CAPABILITY`              | PGA transaction capability. The following are valid values:<br>`READ_ONLY` or `RO`: Read-only capabilities.<br>`SINGLE_SITE` or `SS`: Single-site update only. This indicates that in a distributed environment, only the gateway can perform updates. No other database updates can occur within the Oracle transaction.<br>The default is `SINGLE_SITE`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `PGA_SECURITY_TYPE`           | TCP/IP conversation security option. This controls what security parameters are sent to the OLTP. The following are valid values:<br>`NONE`: Sends no security parameters<br>`PROGRAM`: Sends a user ID and password<br>The default is `NONE`.<br>For further information on these options, refer to [Security Requirements](appc-gateway-security-requirements.md) .<br>Important: You must specify your RACF group name through the `pg4tcpmap` tool if you have set your PGA security option to `SECURITY=PROGRAM`. For more information about this issue, refer to the [Oracle Database Gateway for APPC User's Guide](../appug/pg4tcpmap-commands-tcpip.md).<br>If you have already loaded the table `pga_tcp_imsc` and you did not first specify the RACF group name, delete the row and reinsert it with the value for the RACF group name. |
| `PGA_TCP_DB`                  | The Oracle Net service name for the Oracle database in which the gateway receives its TCP/IP for IMS Connect information, such as host name and port number. This parameter can be from `1` to `255` characters long. This parameter is required.<br>There is no default value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `PGA_TCP_PASS`                | The Oracle password to be used by the gateway when connecting to the Oracle database specified by the `PGA_TCP_DB` parameter. The password can be from `1` to `30` characters long. This parameter is required. The password can be encrypted. For more information about encrypting the password, refer to [Passwords in the Gateway Initialization File](appc-gateway-security-requirements.md).<br>There is no default value.                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `PGA_TCP_USER`                | The Oracle user ID to be used by the gateway when connecting to the Oracle database specified by the `PGA_TCP_DB` parameter. The user ID can be from `1` to `30` characters long. This parameter is required.<br>There is no default value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `TRACE_LEVEL`                 | PGA trace level. This controls tracing output written to `STDERR` (the target of the `LOG_DESTINATION` parameter). The value must be an integer from `0` to `255`.<br>The default is `0`, indicating no tracing.<br>NOTE: This parameter is used in the `pg4tcpmap` tool as well as the gateway.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |

### Output for the pg4tcpmap Tool

The following output illustrates the results from executing the `pg4tcpmap` tool when running TCP/IP for IMS Connect on the gateway. Refer to [Loading the PGA_TCP_IMSC Table](config-appc-gateway-using-tcp-ip.md) of this guide and to Chapter 6, of the [Oracle Database Gateway for APPC User's Guide](../appug/pg4tcpmap-commands-tcpip.md) for detailed information about the function and parameters of the `pg4tcpmap` tool.

Note that input in this sample is shown within angle brackets (`<>`).

    $ pg4tcpmap

    PG4TCPMAP: Release 12.2.0.1.0 - Production on Wed Aug 24 15:09:00 2016

    This tool takes the IMS Connect TCP/IP information, such as host name
    and port number and maps them to your TIPs.

    You may use this tool to insert or delete IMS Connect TCP/IP information.
    If you want to insert a row, type I
    If you want to delete a row, type D
    i
    Enter the Unique Side Profile.
    IMSPGA
    Enter either the remote hostname or its TCP/IP address.
    mvs09
    Enter the IMS CONNECT port number.
    9900
    Do you want to select a CONVERSATIONAL PROTOCOL?(Y|N)
    The default is NO, 'no request for acknowledgment or deallocation'
    n
    Enter one of the following letters for Timer.
    For .25 second, enter 'D'.
    For .01 to .25 second, enter 'S'.
    For 'does not set the timer, no wait occurs', enter 'N'.
    For Receive waits indefinitely, enter 'I'.
    The default is 'D'.
    D
    Enter one of the following letters for 'socket connection type'.
    For transaction socket, enter 'T'.
    For persistent socket, enter 'P'.
    For non-persistent socket, enter 'N'.
    The default is 'T'.
    T
    Do you want to enter the CLIENT ID name? (Y|N)
    If NO, IMS CONNECT (USER EXIT) will generate it.
    n
    Enter one of the following letters for 'COMMIT MODE'.
    For Commit Mode set to 0, enter '0'.
    For Commit Mode set to 1, enter '1'.
    The default is '1'.
    1
    Enter the DATASTORE name (IMS DESTINATION ID).
    The maximum string length is 8 and the Datastore name must be specified.
    IMSE
    Do you want to enter the LTERM? (Y|N)
    If NO, the default is blank.
    n
    Do you want to enter the RACF GROUP name? (Y|N)
    If NO, the default is blank.
    n
    Do you want to enter the IRM_ID? (Y|N)
    If NO, the default is *IRMREQ*.
    n
    Does your exit return the LLLL prefix field? (Y|N)
    The default is 'N'.
    n
    Requested to INSERT a row.
    'Side Profile name' is 'IMSPGA'
    'remote host name' is 'MVS09'
    'IMS Connect port number' is '9900'
    'conversational protocol' is ' '
    'Timer' is 'D'
    'socket connection type' is 'T'
    'client ID' is '        '
    'commit mode' is '1'
    'Datastore name (IMS destination ID)' is 'IMSE    '
    'IMS LTERM override' is '        '
    'RACF group name' is '        '
    'IRM ID' is '*IRMREQ*'
    'LLLL prefix present' is 'N'
    PG4TCPMAP is complete.

#### Sample listener.ora File for a Gateway Using TCP/IP

The following is an example of a `listener.ora` file for a gateway using TCP/IP:

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
          (ORACLE_HOME = /oracle/pga/12.2)
          (PROGRAM = pg4t4ic)
        )
      )

#### Sample tnsnames.ora File for a Gateway Using TCP/IP

The following is an example of a `tnsnames.ora` file for a gateway using TCP/IP:

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
          (ADDRESS = (PROTOCOL = TCP)(HOST = bay)(PORT = 2623))
        )
        (CONNECT_DATA =
          (SID = PGA)
        )
        (HS = OK)
      )
