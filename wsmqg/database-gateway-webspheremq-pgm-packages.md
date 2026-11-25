Use the Visual Workbench when developing applications that access WebSphere MQ through the gateway. The Visual Workbench defines an interface for accessing WebSphere MQ and automatically generates the PL/SQL code (the MIP) for Oracle applications to interface with the gateway. Refer to the Oracle Procedural Gateway Visual Workbench for WebSphere MQ Installation and User's Guide for Microsoft Windows (32-Bit) for more information about Visual Workbench.

The MIP uses definitions from the `PGM`, `PGM_UTL8`, and `PGM_SUP` packages. When necessary, you can alter the MIP to include WebSphere MQ functions that are not supported by Visual Workbench. This is done with the definitions and procedures from the `PGM`, and `PGM_UTL8`, and `PGM_SUP` packages.

The `PGM`, `PGM_UTL8`, and `PGM_SUP` packages are installed when the Visual Workbench repository or the DG4MQ deployment environment is created.

The following topics discuss the `PGM`, `PGM_UTL8`, and `PGM_SUP` packages:

**Related Topics**

- [Installing the Oracle Visual Workbench Repository](configuring-database-gateway-webspheremq.md)
- [Preparing the Production Oracle Database](configuring-database-gateway-webspheremq.md)

### PGM Package, DG4MQ Gateway Procedures, and Data Type Definitions

The gateway procedures and type definitions of the `PGM` package are modeled after the WebSphere MQ MQI calls.

For all the relevant calls and structures found in MQI, a corresponding counterpart exists in `PGM` and the associated data type definitions exist in `pgmobj.sql`. The gateway procedures and `PGM` type definitions are named the same as their MQI counterparts. However, the data types of arguments or structure fields are changed into corresponding PL/SQL data types.

Using these procedures and type definitions in an Oracle application is very similar to writing a WebSphere MQ application. The fields of all `PGM` type definitions are initialized. These initialization values are based on default values defined by MQI.

The use of gateway procedures and `PGM` type definitions requires extensive knowledge of MQI and WebSphere MQ programming in general. These procedures and records follow the MQI flowchart, semantics, and syntax rules.

The `PGM` package is installed when the Visual Workbench repository or the DG4MQ deployment environment is created and is granted public access. It has no schema because the gateway omits all schema names when describing or running a procedure. No schema qualifiers need to be prefixed to the names of the procedures and type definitions.

**See Also:**

Refer to IBM MQSeries Application Programming Reference for complete information about writing WebSphere MQ applications and using MQI calls.

#### Summary of Procedures and Type Definitions

The gateway procedures and PGM provide the following procedures and type definitions.

Table A-1 Procedures and Type Definitions

| Procedure | Procedure Purpose                                                       | Type Definitions Used by the Procedure                               |
|:----------|:------------------------------------------------------------------------|:---------------------------------------------------------------------|
| `MQOPEN`  | Opens a queue.                                                          | `PGM`.`MQOD` and `PGM`.`MQOH`                                        |
| `MQPUT`   | Sends a message to the queue that was opened by `MQOPEN`                | `PGM`.`MQMD`<br>`PGM`.`MQOH`<br>`PGM`.`MQPMO`                        |
| `MQPUT`   | Sends a message longer than 32767 bytes to the queue                    | `PGM`.`MQMD`<br>`PGM`.`MQOH`<br>`PGM`.`MQPMO`<br>`PGM`.`MQPUT_BFFER` |
| `MQGET`   | Retrieves or scans a message from the queue that was opened by `MQOPEN` | `PGM`.`MQMD`<br>`PGM`.`MQOH`<br>`PGM`.`MQGMO`                        |
| `MQGET`   | Sends a message longer than 32767 bytes to the queue                    | `PGM`.`MQMD`<br>`PGM`.`MQOH`<br>`PGM`.`MQGMO`<br>`PGM`.`MQGET_BFFER` |
| `MQCLOSE` | Closes the queue that was opened by `MQOPEN`                            | Does not use a type definition.                                      |

#### Procedure Conventions

The gateway procedures are described in alphabetic order in this appendix.

The type definitions are described with the procedures that use them. Only type definition fields that can be changed are described. Other fields equivalent to MQI fields are left out because they are reserved for WebSphere MQ, are not supported by the gateway, or contain values that should not be changed.

A procedure's definition is shown using the IBM argument names associated with the equivalent MQI call. For example:

    MQGET(hobj, mqmd, mqgmo, msg)

The syntax of the `MQGET` call is as follows:

    MQGET(handle, descript, get_options, message);

where:

- `handle` is your name for the first argument specified in the definition as `hobj`.

- `descript` is your name for the second argument specified in the definition as `mqmd`.

- `get_options` is your name for the third argument specified in the definition as `mqgmo`.

- `message` is your name for the fourth argument specified in the definition as `msg`.

  You can use your own names for these arguments if you code the arguments in the order shown in the definition.

**See Also:**

[Oracle Database PL/SQL Language Reference](../lnpls/index.md)

#### MQI Calls Performed by the Gateway

These MQI calls have no equivalent procedures in the gateway.

The following MQI calls have no equivalent procedures in the gateway because the Oracle database and the gateway automatically perform the functions of these MQI calls:

- `MQBACK`

  Transaction control is handled by the Oracle transaction coordinator. The Oracle application does not need to invoke a separate `MQBACK` call to undo the changes sent to WebSphere MQ.

- `MQCONN`

  A connection to a queue manager is established by the Oracle database and the gateway whenever an Oracle application refers to a gateway procedure. The database link name that is used when calling the gateway procedure determines which queue manager the gateway connects to.

- `MQCMIT`

  Transaction control is handled by the Oracle transaction coordinator. An Oracle application does not need to invoke a separate `MQCMIT` call to commit the changes sent to WebSphere MQ.

- `MQDISC`

  Connections to a queue manager are closed by the Oracle database and gateway. An Oracle application does not need to close the connection with the queue manager. Ending the current Oracle session or dropping the database link causes the queue manager connection to end.

#### Unsupported MQI Calls

These MQI calls are not supported by the gateway.

They are:

- `MQINQ`

- `MQPUT1`

- `MQSET`

#### Migration Tips

This section provides information about how to upgrade Oracle9i DG4MQ and existing customized PL/SQL application programs to use Oracle Database Gateway for WebSphere MQ features.

DG4MQ data types and RPC API prototypes are changed to meet the requirements of the gateway infrastructure.

When upgrading DG4MQ to Oracle 10g release 2 or higher, Oracle recommends that you install the newer version of DG4MQ on a separate development Oracle system. After you have finished with system configuration and testing, transfer all of the COBOL copy books and regenerate and recompile MIPs using the Oracle Visual Workbench. For customized codes, make necessary changes and recompile.

##### Migrating DG4MQ Releases 8 and 9 PL/SQL Applications

To migrate DG4MQ releases 8 and 9 PL/SQL applications:

1.  In the PL/SQL declarative section, remove `dblink` references from the following DG4MQ data types:

    - `PGM8`.`MQOD`

    - `PGM8`.`MQMD`

    - `PGM8`.`MQPMO`

    - `PGM8`.`MQGMO`

    Then remove the following `PGM8`.`MQ`\*`RAW` data types:

    - `PGM8`.`MQODRAW`

    - `PGM8`.`MQMDRAW`

    - `PGM8`.`MQPMORAW`

    - `PGM8`.`MQGMORAW`

2.  In the PL/SQL declarative section, change the data type of the handle of the queue, the third argument of `PGM`.`MQOPEN`, from `BINARY_INTEGER` to `PGM`.`MQOH` and replace the package name `PGM8` with `PGM`.

    Change the data type of the handles of the queue, the third argument of `PGM`.`MQOPEN,` from `BINARY_INTEGER` to `PGM`.`MQOH`.

    For example, for version 8 and 9 change the following data types to those listed for Oracle 10g:

        objdesc    PGM8.MQOD;
        msgdesc    PGM8.MQMD;
        putmsgopts PGM8.MQPMO;
        getmsgopts PGM8.MQGMO;
        hobj       BINARY_INTEGER;
        mqodRaw    PGM8.MQODRAW;
        mqmdRaw    PGM8.MQMDRAW;
        mqpmoRaw   PGM8.MQPMORAW;
        mqgmoRaw   PGM8.MQGMORAW;

    The data types for Oracle 10g release 2 and higher:

        objdesc     PGM.MQOD;
        msgdesc     PGM.MQMD;
        putmsgopts  PGM.MQPMO;
        getmsgopts  PGM.MQGMO;
        hobj        PGM.MQOH;

3.  In the PL/SQL executable section, remove `dblink` references from the following DG4MQ procedures:

        PGM8.MQOPEN@dblink()
        PGM8.MQPUT@dblink()
        PGM8.MQGET@dblink()
        PGM8.MQCLOSE@dblink()

    Then define the `dblink` in the new `PGM.MQOD` type where the object queue name is defined.

    For example, for version 8 and 9:

        objdesc.objectname := 'QUEUE1';

    For Oracle 10g release 2 and higher:

        objdesc.objectname := 'QUEUE1';
        objdesc.dblinkname := 'dblink';

4.  If necessary, change the package name `PGM8` of all DG4MQ procedures to `PGM`.

    For example, for version 8 and 9:

        PGM8.MQOPEN@dblink();
        PGM8.MQPUT@dblink();
        PGM8.MQGET@dblink();
        PGM8.MQCLOSE@dblink();

    For Oracle 10g release 2 and higher:

        PGM.MQOPEN;
        PGM.MQPUT;
        PGM.MQGET;
        PGM.MQCLOSE;

5.  In the PL/SQL executable section, remove all statements starting with `PGM_UTL8`.`RAW_TO_`\*, remove all `PGM_UTL8`.`TO_RAW` statements, and replace all references to the `MQ`\*`RAW` data types with their matching `MQ`\* data types in the following DG4MQ procedures:

    - `PGM`.`MQOPEN`;

    - `PGM`.`MQPU`;

    - `PGM`.`MQGET`;

    - `PGM`.`MQCLOSE`;

    For example, for versions 8 and 9:

        mqodRaw := PGM_UTL8.TO_RAW(objdesc);
        PGM8.MQOPEN@dblink(mqodRaw, options, hobj);
        objdesc := PGM_UTL8.RAW_TO_MQMD(mqodRaw);
        mqmdRaw := PGM_UTL8.TO_RAW(msgdesc);
        mqpmoRaw := PGM_UTL8.TO_RAW(putmsgopts);
        PGM8.MQPUT@dblink(hobj, mqmdRaw, mqpmoRaw, putbuffer);
        putmsgopts := PGM_UTL8.RAW_TO_MQPMO(mqpmoRaw);
        msgdesc := PGM_UTL8.RAW_TO_MQMD(mqmdRaw);

        mqmdRaw := PGM_UTL8.TO_RAW(msgdesc);
        mqgmoRaw := PGM_UTL8.TO_RAW(getmsgopts);
        PGM8.MQGET@dblink(hobj, mqmdRaw, mqgmoRaw, putbuffer);
        getmsgopts := PGM_UTL8.RAW_TO_MQGMO(mqgmoRaw);
        msgdesc := PGM_UTL8.RAW_TO_MQMD(mqmdRaw);

    For Oracle 10g release 2 and higher:

        PGM.MQOPEN(objdesc, options, hobj);
        PGM.MQPUT(hobj, msgdesc, putmsgopts, putbuffer);
        PGM.MQGET(hobj, msgdesc, getmsgopts, getbuffer);

6.  In PL/SQL executable section, remove all statements that reference the old `MQ`\*`RAW` data types.

##### Migrating DG4MQ Release 4.0.1.\*.\* PL/SQL Applications

To migrate applications:

1.  In the PL/SQL declarative section, remove `dblink` references from the following DG4MQ data types:
    - `PGM`.`MQOD`

    - `PGM`.`MQMD`

    - `PGM`.`MQPMO`

    - `PGM`.`MQGMO`
2.  In the PL/SQL executable section, remove `dblink` references from the following DG4MQ procedures and define the `dblink` in the new `PGM`.`MQOD` object where the object queue name is defined:
    - `PGM`.`MQOPEN``@``dblink`()

    - `PGM`.`MQPUT``@``dblink`()

    - `PGM`.`MQGET``@``dblink`()

    - `PGM`.`MQCLOSE``@``dblink`()

    For example, for version 4:

        PGM.MQOPEN@dblink(objdesc, options, hobj);
        objdesc.objectname :='QUEUE1';
        PGM.MQPUT@dblink(hobj, msgdesc, putmsgopts, putbuffer);
        PGM.MQGET@dblink(hobj, msgdesc, getmsgopts, putbuffer);
        PGM.MQCLOSE@dblink(hobj, options);

### MQCLOSE Procedure

`MQCLOSE` closes a queue.

On return, the queue handle is invalid and your application must reopen the queue with another call to `MQOPEN` before issuing another `MQPUT`, `MQGET`, or `MQCLOSE` call to the queue.

`MQCLOSE` differs from MQI calls in the following ways:

- The connection handle argument is omitted from `MQCLOSE` because the gateway automatically takes care of managing queue manager connections.

- The MQI completion code is not included in the procedure argument list. When a gateway procedure fails because the corresponding MQI call failed, then an Oracle error message is returned to the caller.

- The MQI reason code is not included in the procedure argument list. When the corresponding MQI call for a gateway procedure returns a reason code, then the reason code is included in the Oracle error message returned to the caller.

#### Definition

    MQCLOSE(hobj, options)

where:

- `hobj` contains the handle for the queue to close. The handle is returned by a previous call to `MQOPEN`. This input argument is a new `PGM`.`MQOH` object in Oracle 10g release 2.

- `options` specifies the close action. Use `PGM_SUP`.`MQCO_NONE` or the other `PGM_SUP` constants for a close option. This input argument is of the `BINARY_INTEGER` PL/SQL data type.

You can use your own variable names when arguments are in the required order as follows:

    MQCLOSE(handle, close_options);

**Related Topics**

- MQCLOSE Values

### MQGET Procedure

The `MQGET` procedure retrieves a message from a queue.

The queue must already be open from a previous call to `MQOPEN` with the `PGM_SUP`.`MQOO_INPUT_AS_Q_DEF` (or an equivalent option) option set. Retrieved messages for this form of `MQGET` must be shorter than 32767 bytes.

`MQGET` differs from MQI calls in the following ways:

- The connection handle argument is omitted from `MQGET` because the gateway automatically takes care of managing queue manager connections.

- The MQI completion code is not included in the procedure's argument list. When a gateway procedure fails because the corresponding MQI call failed, then an Oracle error message is returned to the caller.

- The MQI reason code is not included in the procedure's argument list. When the corresponding MQI call for a gateway procedure returns a reason code, then the reason code is included in the Oracle error message that was returned to the caller.

- The `msg` length argument is not included in the procedure's argument list because the Oracle database and the gateway automatically keep track of the message data length.

#### Definition

    MQGET(hobj, mqmd, mqgmo, msg)

where:

- `hobj` contains the handle for the queue to open. The handle is returned by a previous call to `MQOPEN`. This input argument is a new `PGM`.`MQOH` object in Oracle 10g release 2.

- `mqmd` is used on input to describe the attributes of the message being retrieved. Use the fields of the `PGM`.`MQMD` object type definition to describe these attributes.

  On output, `mqmd` contains information about how the request was processed. The queue manager sets some of the `PGM`.`MQMD` object fields on return.

  This input and output argument is PL/SQL `PGM`.`MQMD` data type.

- `mqgmo`is used on input to describe the option values that control the retrieve request. Use the fields of the `PGM`.`MQGMO` object type definition to describe these options.

  On output, the queue manager sets some of the `PGM`.`MQGMO` object fields on return.

  This input and output argument is PL/SQL `PGM`.`MQGMO` data type.

- `msg` contains the retrieved message. This output argument is PL/SQL data type `RAW` or `PGM`.`MQGET_BUFFER`.

#### Examples

1.  Using your own variable names when arguments are in the required order:

        MQGET(handle, descript, opts, message);

2.  The following example, which is provided as a sample with the gateway (`ORACLE_HOME\dg4mq\getsample.sql on Microsoft Windows and ``ORACLE_HOME``/dg4mq/sample/getsample.sql` on UNIX based systems), reads all messages from a WebSphere MQ queue. For more information, refer to the IBM publication on WebSphere MQ Application Programming.

Example A-1 getsample.sql

    ---- Copyright Oracle, 2007 All Rights Reserved.
    --
    -- NAME
    --   getsample.sql
    --
    -- DESCRIPTION
    --
    --   Specify the database link name you created for the gateway. To do this,
    --   replace the database link name 'YOUR_DBLINK_NAME' with the dblink name
    --   you chose when the database link was created.
    --
    --   This script performs a test run for the MQSeries gateway. In this
    --   script the queuename is 'YOUR_QUEUE_NAME', replace it with a valid
    --   queue name at the queue manager the gateway is configured for.
    --
    -- NOTES
    --   Run the script from the SQL*Plus command line.
    --
    --   Make the sure the user is granted 'EXECUTE' on package dbms_output
    --

    SET SERVEROUTPUT ON
    DECLARE

        objdesc      PGM.MQOD;
        msgDesc      PGM.MQMD;
        getOptions   PGM.MQGMO;
        objectHandle PGM.MQOH;
        message      raw(32767);

    BEGIN

        objdesc.OBJECTNAME := 'QUEUE1';
        objdesc.DBLINKNAME := 'dg4mqdepdblink';
                      -- Open the queue 'YOUR_QUEUE_NAME' for reading.

        PGM.MQOPEN(objdesc, PGM_SUP.MQOO_INPUT_AS_Q_DEF, objectHandle);

        -- Get all messages from the queue.

        WHILE TRUE LOOP

            -- Reset msgid and correlid to get the next message.

            msgDesc.MSGID := PGM_SUP.MQMI_NONE;
            msgDesc.CORRELID := PGM_SUP.MQCI_NONE;

            PGM.MQGET(objectHandle, msgDesc, getOptions, message);

            -- Process the message....
            DBMS_OUTPUT.PUT_LINE('message read back = ' || rawtohex(message));

         END LOOP;

    EXCEPTION

          WHEN PGM_SUP.NO_MORE_MESSAGES THEN

              DBMS_OUTPUT.PUT_LINE('Warning: No more message found on the queue');

              -- Close the queue again.

              PGM.MQCLOSE(objectHandle, PGM_SUP.MQCO_NONE);

          WHEN OTHERS THEN

              -- Re-raise the error;

              DBMS_OUTPUT.PUT_LINE('Error: Oracle Database Gateway for WebSphere MQ
     verification script failed.');
              DBMS_OUTPUT.PUT_LINE(SQLERRM);
                 raise;

    END;
    /

Notes:

**Note:**

The PL/SQL block fails if the exception clause is left out. In that case, the `PGM_SUP.NO_MORE_MESSAGES` error code is raised. The `MSGID` and `CORRELID` fields that are used for `MQGET` are set after each call to `MQGET`. If they are not reset at each cycle, then `MQGET` checks for the next message that has the same identifiers as the last read operation, which usually do not exist. The PL/SQL block would only read one message.

#### PGM.MQMD Type Definition

`PGM`.`MQMD` specifies the control information that accompanies a message when it travels between the sending and receiving applications.

It also contains information about how the message is handled by the queue manager or by the receiving application. `PGM`.`MQMD` describes the attributes of the message being retrieved.

You can use the default values for `PGM`.`MQMD` fields or change the fields for your application requirements. For example, to change a field value, do the following:

    mqmd.field_name := field_value;

where:

- `mqmd` is the `PGM`.`MQMD` object data type and it describes the attributes of the message being retrieved

- `field_name` is a field name of the `PGM`.`MQMD` object type definition. You can set as many fields as necessary. Refer to Table A-2 for field names and descriptions.

- `field_value` is the value to assign to `field_name`. You can specify a value or use a `PGM_SUP` constant to assign a value.

Table A-2 PGM.MQMD Object Fields

| Field Name         | Description                                                                                                                                                                                                                                                                                            | PL/SQL Data Type | Initial Value                          |
|:-------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------|:---------------------------------------|
| `REPORT`           | Allows the application that sends a message to specify which report message (or messages) should be created by the queue manager when an expected or unexpected event occurs. Use a `PGM_SUP` constant to assign a value. Refer to REPORT Field.                                                       | `RAW`(`4`)       | `PGM_SUP.MQRO_ NONE`                   |
| `MSGTYPE`          | Specifies the message type: reply message, report message, or normal message (datagram). Use a PGM_SUP constant to assign a value. Refer to MSGTYPE Field.                                                                                                                                             | `BINARY_INTEGER` | `PGM_SUP.MQMT_ DATAGRAM`               |
| `EXPIRY`           | Specifies the amount of time that a message stays in a queue. The expiration period is in tenths of a second, and is set by the sending application. Use a `PGM_SUP` constant to assign a value. Refer to EXPIRY Field.                                                                                | `BINARY_INTEGER` | `PGM_SUP.QMEI_ UNLIMITED`              |
| `FEEDBACK`         | Used with the `REPORT` field to indicate the kind of report. Use a `PGM_SUP` constant to assign a value. Refer to FEEDBACK Field.                                                                                                                                                                      | `BINARY_INTEGER` | `PGM_SUP.MQFB_ NONE`                   |
| `ENCODING`         | Used for numeric values in the message data. Use a `PGM_SUP` constant to assign a value. Refer to ENCODING Field.                                                                                                                                                                                      | `RAW`(`4`)       | `PGM_SUP.MQENC_ NATIVE`                |
| `CODEDCHARSETID`   | Specifies the coded character set identifier of the characters in the message. Use a `PGM_SUP` constant to assign a value. Refer to CODEDCHARSETID Field.                                                                                                                                              | `BINARY_INTEGER` | `PGM_SUP.MQCCSI_DEFAULT`               |
| `FORMAT`           | A free format name used to inform the receiver about the contents of the message. Specify a format or use a `PGM_SUP` constant. Refer to FORMAT Field.                                                                                                                                                 | `CHAR`(`8`)      | `PGM_SUP.MQFMT_ NONE`                  |
| `PRIORITY`         | Specifies message priority. Specify a value greater than or equal to `0` (zero is the lowest priority), or use a `PGM_SUP` constant. Refer to PRIORITY Field.                                                                                                                                          | `BINARY_INTEGER` | `PGM_SUP.MQPRI_ PRIORITY_AS_Q_ DEF`    |
| `PERSISTENCE`      | An input field for the sending application. Persistent messages survive when a queue manager is restarted. Non persistent messages and messages in temporary queues are lost when a queue manager is restarted. Specify the desired persistence with a `PGM_SUP` constant. Refer to PERSISTENCE Field. | `BINARY_INTEGER` | `PGM_SUP.MQPER_ PERSISTENCE_AS_ Q_DEF` |
| `MSGID`            | Specifies the message identifier of the message to be retrieved (when receiving a message). If no value is specified when a sending a message (`PGM_SUP`.`MQMI_NONE`), then the queue manager assigns a unique value.                                                                                  | `RAW`(`24`)      | `PGM_SUP`.`MQMI_NONE`                  |
| `CORRELID`         | Specifies the correlation identifier for the message to retrieve when receiving a message (refer to the `MSGID` field). When sending a message, specify any value, or use `PGM_SUP`.`MQCI_NONE` if the message does not require a correlation ID.                                                      | `RAW`(`24`)      | `PGM_SUP`.`MQCI_NONE`                  |
| `BACKOUTCOUNT`     | An output field for the `MQGET` procedure. It indicates the number of times a message was placed back on a queue because of a rollback operation.                                                                                                                                                      | `BINARY_INTEGER` | `Zero`                                 |
| `REPLYTOQ`         | Specifies the name of the reply-to queue. This is an input field for `MQPUT` and allows the sending application to indicate where reply messages should be sent.<br>It is also an output field for `MQGET` and tells the receiving application where to send a reply.                                  | `CHAR`(`48`)     | `NULL`                                 |
| `REPLYTOQMGR`      | Specifies the queue manager to which the reply message or report should be sent. This is an input field for `MQPUT` and an output field for `MQGET`.                                                                                                                                                   | `CHAR`(`48`)     | `NULL`                                 |
| `USERIDENTIFIER`   | An output field for receiving applications. It identifies the user that sent the message. Sending applications can specify a user on input if the `CONTEXT` field for the `mqpmo` argument of `MQPUT` was set to `PGM_SUP`.`MQPMO_SET_IDENTITY_CONTEXT` or to `PGM_SUP`.`MQPMO_SET_ALL_CONTEXT`.       | `CHAR`(`12`)     | `NULL`                                 |
| `ACCOUNTINGTOKEN`  | Used to transfer accounting information between applications. Sending applications provide accounting information or use `PGM_SUP`.`MQACT_NONE` to specify that no accounting information is included.                                                                                                 | `CHAR`(`32`)     | `PGM_SUP.MQACT_ NONE`                  |
| `APPLIDENTITYDATA` | Specifies more information to send along with the message to help the receiving application provide more information about the message or its sender.                                                                                                                                                  | `CHAR`(`32`)     | `NULL`                                 |
| `PUTAPPLTYPE`      | Describes the kind of application that placed the message on the queue.  Use a `PGM_SUP` constant to assign a value. Refer to PUTAPPLTYPE Field.                                                                                                                                                       | `BINARY_INTEGER` | `PGM.MQAT_NO_ CONTEXT`                 |
| `PUTAPPLNAME`      | Specifies the name of the application that placed the message on the queue. Sending applications specify a name or let the queue manager fill in this field. This is an output field for receiving applications.                                                                                       | `CHAR`(`28`)     | `NULL`                                 |
| `PUTDATE`          | Specifies the date on which a message was placed on the queue.  Sending applications can set a date or let the queue manager take care of it.  The date format used by the queue manager is `YYYYMMDD`. This is an output field for receiving applications.                                            | `CHAR`(`8`)      | `NULL`                                 |
| `PUTTIME`          | Specifies the time that a message was placed on the queue. Sending applications can set a time or let the queue manager take care of it. The time format that is used by the queue manager is `HHMMSSTH`. This is an output field for receiving applications.                                          | `CHAR`(`8`)      | `NULL`                                 |
| `APPLORIGINDATA`   | Used by the sending application to add information to the message about the message origin. This is an output field for receiving applications.                                                                                                                                                        | `CHAR`(`4`)      | `NULL`                                 |

#### PGM.MQGMO Type Definition

Use `PGM`.`MQGMO` to specify option and control information about how the message is retrieved from a queue.

Use `PGM`.`MQGMO` to specify option and control information about how the message is retrieved from a queue. You can use the default values for `PGM.MQGMO` fields or change the fields for your application requirements. For example, to change a field value:

    mqgmo.field_name := field_value

where:

- `mqgmo` is the `PGM`.`MQGMO` object data type, and it specifies option and control information about how the message is retrieved from a queue.

- `field_name` is a field name of the `PGM`.`MQGMO` type definition. You can set as many fields as necessary. Refer to Table A-3 for names and field descriptions.

- `field_value` is the value to assign to `field_name`.  You can specify a value or use a `PGM_SUP` constant to assign a value.

Table A-3 PGM.MQGMO Fields

| Field Name      | Description                                                                                                                                                                                                                              | PL/SQL Data Type | Initial Value                                                                                                                  |
|:----------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `OPTIONS`       | Specifies options to control the `MQGET` procedure. Add one or more `PGM_SUP` constants to set it. Refer to OPTIONS Field.                                                                                                               | `BINARY_INTEGER` | `PGM.MQGMO_ SYNCPOINT `<br>(Messages that are retrieved from the queue are coordinated by the Oracle transaction coordinator.) |
| `WAITINTERVAL`  | Specifies the maximum time in milliseconds that `MQGET` waits for a message to arrive in the queue.`  WAITINTERVAL` should be equal to or greater than `0`, or set to the value of `PGM_SUP`.`MQWI_UNLIMITED` (unlimited wait interval). | `BINARY_INTEGER` | `Zero`                                                                                                                         |
| `RESOLVEDQNAME` | Contains the resolved name of the destination queue from which the message was retrieved. This is an output field set by the queue manager upon return from the call.                                                                    | `CHAR`(48)       | `NULL`                                                                                                                         |

### MQOPEN Procedure

`MQOPEN` establishes access to a queue.

Depending on the mode selected to open the queue, an application can issue subsequent `MQPUT`, `MQGET`, or `MQCLOSE` calls.

`MQOPEN` differs from MQI calls in the following ways:

- The connection handle argument is omitted from `MQOPEN` because the gateway automatically takes care of managing queue manager connections. 

- The MQI completion code is not included in the procedure argument list. When a gateway procedure fails because the corresponding MQI call failed, then an Oracle error message is returned to the caller.

- The MQI reason code is not included in the procedure argument list. If the corresponding MQI call for a gateway procedure returns a reason code, then the reason code is included in the Oracle error message that is returned to the caller.

#### Definition

    MQOPEN(mqod, options, hobj)

where:

- `mqod` specifies the queue to open. Use the fields of the `PGM`.`MQOD` type definition to describe these attributes. On output, the queue manager sets some of the `PGM`.`MQOD` object fields on return.

  This input and output argument is PL/SQL `PGM`.`MQOD` data type. For details of `PGM`.`MQOD`, refer to PGM.MQOD Type Definition.

- `options` specifies the kind of open. Refer to MQOPEN Values. This input argument is of the PL/SQL `BINARY_INTEGER` data type.

- `hobj` contains the handle of the queue after the queue is opened and becomes an input argument for subsequent PGM calls. The queue handle remains valid until one of the following conditions occur:

  - The queue is closed by a call to `MQCLOSE`

  - The current transaction is made permanent by a `COMMIT` or `ROLLBACK` command

  - The Oracle user session is ended by a `DISCONNECT` command. This output argument is of the `PGM`.`MQOH` data type.

You can use your own variable names when arguments are in the required order as follows:

    MQOPEN and(descript, open_options, handle);

#### PGM.MQOD Type Definition

`PGM`.`MQOD` is used to define the object to open.

You can use the default values for `PGM`.`MQOD` fields or change the fields for your application requirements. For example, you can change a field value as follows:

    mqod.field_name := field_value

where:

- `mqod` is the `PGM`.`MQOD` data type and specifies the object to open.

- `field_name` is a field name of the `PGM`.`MQOD` type definition. You can set as many fields as necessary. Refer to Table A-4 for field names and descriptions.

- `field_value` is the value to assign to `field_name`.  You can specify a value or use a `PGM_SUP` constant to assign a value.

Table A-4 PGM.MQOD Object Fields

| Field Name        | Description                                                                                                                                                                                                                                  | PL/SQL Data Type | Initial Value            |
|:------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------|:-------------------------|
| `OBJECTTYPE`      | Specifies the object to open. Use a `PGM_SUP` constant to assign a value. Refer to OBJECTTYPE Field.                                                                                                                                         | `BINARY_INTEGER` | `PGM_SUP.MQOT_ Q(queue)` |
| `DBLINKNAME`      | Specifies the database link name.                                                                                                                                                                                                            | `CHAR`(64)       | `NULL`                   |
| `OBJECTNAME`      | Specifies the local name of the object as defined by the queue manager.                                                                                                                                                                      | `CHAR`(48)       | `NULL`                   |
| `OBJECTQMGRNAME`  | Specifies the name of the queue manager for the object defined by `OBJECTNAME`. Leave `OBJECTQMGRNAME` set to null values because the gateway supports only the opening of objects at the connected queue.                                   | `CHAR`(48)       | `NULL`                   |
| `DYNAMICQNAME`    | Is ignored unless the `OBJECTNAME` field specifies the name of a model queue.  When a model queue is involved, then this field specifies the name of the dynamic queue to be created at the queue manager to which the gateway is connected. | `CHAR`(48)       | `AMQ.*`                  |
| `ALTERNATEUSERID` | If the `options` argument of `MQOPEN` is set to the value of `PGM_SUP`.`MQOO_ALTERNATE_USER_AUTHORITY`, then this field specifies the alternate user ID which the queue manager uses to check the authorization for the queue being opened.  | `CHAR`(12)       | `NULL`                   |

### MQPUT Procedure

`MQPUT` sends a message to a queue.

The queue must already be open by a previous call to `MQOPEN` with its `options` argument set to the value of `PGM_SUP`.`MQOO_OUTPUT`.

`MQPUT` differs from MQI calls as follows:

- The connection handle argument is omitted from `MQPUT` because the gateway automatically takes care of managing queue manager connections.

- The MQI completion code is not included in the procedure argument list. When a gateway procedure fails because the corresponding MQI call failed, then an Oracle error message is returned to the caller.

- The MQI reason code is not included in the procedure argument list. When the corresponding MQI call for a gateway procedure returns a reason code, then the reason code is included in the Oracle error message returned to the caller.

- The `msg` length argument is not included in the procedure argument list because the Oracle database and the gateway automatically keep track of the message data length.

#### Definition

    MQPUT(hobj, mqmd, mqpmo, msg)

where:

- `hobj` contains the handle for the queue to send the message to. The handle is returned by a previous call to `MQOPEN`. This input argument is a new `PGM.MQOH` in Oracle10g release 2.

- `mqmd` is used on input to describe the attributes of the message being retrieved. Use the fields of the `PGM`.`MQMD` type definition to describe these attributes. On output, `mqmd` contains information about how the request was processed. The queue manager sets some of the `PGM`.`MQMD` fields on return.

  This input and output argument is a `PGM`.`MQMD`. For details of `PGM`.`MQMD`, refer to PGM.MQMD Type Definition.

- `mqpmo` is used on input to describe the option values that control the put request. Use the fields of the `PGM`.`MQPMO` type definition to describe these options. On output, the queue manager sets some of the `PGM`.`MQPMO` fields on return.

  This input and output argument is `PGM`.`MQPMO`. For details of `PGM`.`MQPMO`, refer to PGM.MQPMO Type Definition.

- `msg` contains the message to send. This input argument is PL/SQL data type `RAW` or `PGM`.`MQPUT_BUFFER`.

#### Example

1.  You can use your own variable names when arguments are in the required order:

        MQPUT(handle, descript, options, message);

2.  The following sample, which is provided as a sample with the gateway (`ORACLE_HOME\dg4mq\sample\putsample.sql` on Microsoft Windows and `ORACLE_HOME``/dg4mq/sample/putsample.sql` on UNIX based systems), sends a message shorter than 32767 bytes:

Example A-2 putsample.sql

    --
    -- Copyright Oracle, 2005 All Rights Reserved.
    --
    -- NAME
    --   putsample.sql
    --
    -- DESCRIPTION
    --
    --   Specify the database link name you created for the gateway. To do this,
    --   replace the database link name 'YOUR_DBLINK_NAME' with the dblink name
    --   you chose when the database link was created.
    --
    --   This script performs a test run for the MQSeries gateway. In this
    --   script the queuename is 'YOUR_QUEUE_NAME', replace it with a valid
    --   queue name at the queue manager the gateway is configured for.
    --
    -- NOTES
    --   Run the script from the SQL*Plus command line.
    --
    --   Make the sure the user is granted 'EXECUTE' on package dbms_output
    --

    SET SERVEROUTPUT ON

    DECLARE
        objdesc      PGM.MQOD;
        msgDesc      PGM.MQMD;
        putOptions   PGM.MQPMO;
        objectHandle PGM.MQOH;
        message      raw(255);

    BEGIN

        objdesc.OBJECTNAME := 'QUEUE1';
        objdesc.DBLINKNAME := 'dg4mqdepdblink';
                      -- Open the queue 'YOUR_QUEUE_NAME' for sending.

        PGM.MQOPEN(objdesc, PGM_SUP.MQOO_OUTPUT, objectHandle);
                      -- Put the message buffer on the queue.

        message := '01020304050607080900';

        PGM.MQPUT(objectHandle, msgDesc, putOptions, message);
         -- Print the message we are putting on the queue

        dbms_output.put_line('message put on queue = ' || rawtohex(message));

        -- Close the queue again.

        PGM.MQCLOSE(objectHandle, PGM_SUP.MQCO_NONE);

    EXCEPTION

        -- something else went wrong.. tell the user.

        WHEN OTHERS THEN
            DBMS_OUTPUT.PUT_LINE('Error: Procedural Gateway for IBM MQSeries
     verification script failed.');
            DBMS_OUTPUT.PUT_LINE(SQLERRM);
            PGM.MQCLOSE(objectHandle, PGM_SUP.MQCO_NONE);

    END;
    /

#### PGM.MQPMO Type Definition

`PGM`.`MQPMO` is used to define the `mqpmo` argument of `MQPUT`.

It specifies option and control information for processing a message.

You can use the default values for `PGM`.`MQPMO` fields or change the fields for the application requirements. For example, to change a field value:

    mqpmo.field_name := field_value

where:

- `mqpmo` is the `PGM`.`MQPMO` data type and specifies option and control information about how the message is processed and put into a queue.

- `field_name` is a field name of the `PGM`.`MQPMO` type definition. You can set as many fields as necessary. Refer to Table A-5 for field names and descriptions.

- `field_value` is the value to assign to `field_name`. You can specify a value or use a `PGM_SUP` constant to assign a value.

Table A-5 PGM.MQPMO Fields

| Field Name         | Description                                                                                                                                                                                  | PL/SQL Data Type | Initial Value                                                                                                   |
|:-------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------|:----------------------------------------------------------------------------------------------------------------|
| `OPTIONS`          | Specifies options to control the `MQPUT` procedure. The field is set by adding one or more of the `PGM_SUP` definitions.  Refer to "OPTIONS Field".                                          | `BINARY_INTEGER` | `PGM.MQPMO_ SYNCPOINT`<br>(Messages placed on the queue are coordinated by the Oracle transaction coordinator.) |
| `CONTEXT`          | Specifies the object handle of the input queue. It is only used when the `OPTIONS` field has the bit `PGM_SUP.MQPMO_PASS_IDENTITY_ CONTEXT` or the bit `PGM_SUP.MQPMO_PASS_ALL_CONTEXT` set. | `BINARY_INTEGER` | `Zero`                                                                                                          |
| `RESOLVEDQNA``ME`  | Contains the resolved name of the destination queue. This is an output field set by the queue manager on return.                                                                             | `CHAR`(48)       | `NULL`                                                                                                          |
| `RESOLVEDQMGRNAME` | Contains the resolved name of the queue manager for the queue name returned in the `RESOLVEDQNAME` field. This is an output field set by the queue manager on return.                        | `CHAR`(48)       | `NULL`                                                                                                          |

### PGM_SUP Package

`PGM_SUP` contains constant and exception definitions to use with the gateway procedures and `PGM` type definitions.

Using these values requires extensive knowledge of MQI and WebSphere MQ programming in general. These definitions follow the MQI definition rules. For complete information about writing WebSphere MQ applications, refer to the IBM MQSeries Application Programming Reference.

#### PGM.MQGMO Values

These topics provide information about `PGM`.`MQGMO` values.

##### OPTIONS Field

    MQGMO_NO_WAIT                 constant binary_integer := 0;
    MQGMO_NONE                    constant binary_integer := 0;
    MQGMO_WAIT                    constant binary_integer := 1;
    MQGMO_SYNCPOINT               constant binary_integer := 2;
    MQGMO_NO_SYNCPOINT            constant binary_integer := 4;
    MQGMO_SET_SIGNAL              constant binary_integer := 8;
    MQGMO_BROWSE_FIRST            constant binary_integer := 16;
    MQGMO_BROWSE_NEXT             constant binary_integer := 32;
    MQGMO_ACCEPT_TRUNCATED_MSG    constant binary_integer := 64;
    MQGMO_MARK_SKIP_BACKOUT       constant binary_integer := 128;
    MQGMO_MSG_UNDER_CURSOR        constant binary_integer := 256;
    MQGMO_LOCK                    constant binary_integer := 512;
    MQGMO_UNLOCK                  constant binary_integer := 1024;
    MQGMO_BROWSE_MSG_UNDER_CURSOR constant binary_integer := 2048;
    MQGMO_SYNCPOINT_IF_PERSISTENT constant binary_integer := 4096;
    MQGMO_FAIL_IF_QUIESCING       constant binary_integer := 8192;
    MQGMO_CONVERT                 constant binary_integer := 16384;
    MQGMO_LOGICAL_ORDER           constant binary_integer := 32768;
    MQGMO_COMPLETE_MSG            constant binary_integer := 65536;
    MQGMO_ALL_MSGS_AVAILABLE      constant binary_integer := 131072;
    MQGMO_ALL_SEGMENTS_AVAILABLE  constant binary_integer := 262144;

##### VERSION Field

    MQGMO_VERSION_1                constant binary_integer := 1;
    MQGMO_CURRENT_VERSION          constant binary_integer := 1;
    MQGMO_VERSION_2                constant binary_integer := 2;
    MQGMO_VERSION_3                constant binary_integer := 3;

##### MATCHOPTIONS Field

    MQMO_DEFAULT                   constant binary_integer := 3;
    MQMO_NONE                      constant binary_integer := 0;
    MQMO_MATCH_MSG_ID              constant binary_integer := 1;
    MQMO_MATCH_CORREL_ID           constant binary_integer := 2;
    MQMO_MATCH_GROUP_ID            constant binary_integer := 4;
    MQMO_MATCH_MSG_SEQ_NUMBER      constant binary_integer := 8;
    MQMO_MATCH_OFFSET              constant binary_integer := 16;
    MQMO_MATCH_MSG_TOKEN           constant binary_integer := 32;

##### WAITINTERVAL

    PGM_SUP.MQWI_UNLIMITED CONSTANT BINARY_INTEGER := -1;
    PGM_SUP.MQWI_UNITS     CONSTANT BINARY_INTEGER := 1000;

#### PGM.MQMD Values

These topics provide information about `PGM`.`MQOD` values.

##### CODEDCHARSETID Field

    PGM_SUP.MQCCSI_DEFAULT  CONSTANT BINARY_INTEGER := 0;
    PGM_SUP.MQCCSI_Q_MGR    CONSTANT BINARY_INTEGER := 0;
    PGM_SUP.MQCCSI_EMBEDDED CONSTANT BINARY_INTEGER := -1;

##### ENCODING Field

    PGM_SUP.MQENC_NATIVE  CONSTANT RAW(4) := '00000111';

##### ENCODING Field, Values for Binary Integers

    PGM_SUP.MQENC_INTEGER_UNDEFINED CONSTANT RAW(4) := '00000000';
    PGM_SUP.MQENC_INTEGER_NORMAL    CONSTANT RAW(4) := '00000001';
    PGM_SUP.MQENC_INTEGER_REVERSED  CONSTANT RAW(4) := '00000002';

##### ENCODING Field, Values for Floating Point Numbers

    PGM_SUP.MQENC_FLOAT_UNDEFINED     CONSTANT RAW(4) := '00000000';
    PGM_SUP.MQENC_FLOAT_IEEE_NORMAL   CONSTANT RAW(4) := '00000100';
    PGM_SUP.MQENC_FLOAT_IEEE_REVERSED CONSTANT RAW(4) := '00000200';
    PGM_SUP.MQENC_FLOAT_S390          CONSTANT RAW(4) := '00000300';

##### ENCODING Field, Mask Values

    PGM_SUP.MQENC_INTEGER_MASK  CONSTANT RAW(4) := '0000000f';
    PGM_SUP.MQENC_DECIMAL_MASK  CONSTANT RAW(4) := '000000f0';
    PGM_SUP.MQENC_FLOAT_MASK    CONSTANT RAW(4) := '00000f00';
    PGM_SUP.MQENC_RESERVED_MASK CONSTANT RAW(4) := 'fffff000';

##### ENCODING Field, Values for Packed Decimal Integers

    PGM_SUP.MQENC_DECIMAL_UNDEFINED CONSTANT RAW(4) := '00000000';
    PGM_SUP.MQENC_DECIMAL_NORMAL    CONSTANT RAW(4) := '00000010';
    PGM_SUP.MQENC_DECIMAL_REVERSED  CONSTANT RAW(4) := '00000020';

##### EXPIRY Field

    PGM_SUP.MQEI_UNLIMITED   CONSTANT BINARY_INTEGER := -1;
    PGM_SUP.MQEI_MIN_EXPIRY  CONSTANT BINARY_INTEGER := 0;
    PGM_SUP.MQEI_UNITS       CONSTANT BINARY_INTEGER := 10;

##### FEEDBACK Field

    PGM_SUP.MQFB_NONE                   CONSTANT BINARY_INTEGER := 0;
    PGM_SUP.MQFB_SYSTEM_FIRST           CONSTANT BINARY_INTEGER := 1;
    PGM_SUP.MQFB_EXPIRATION             CONSTANT BINARY_INTEGER := 258;
    PGM_SUP.MQFB_COA                    CONSTANT BINARY_INTEGER := 259;
    PGM_SUP.MQFB_COD                    CONSTANT BINARY_INTEGER := 260;
    PGM_SUP.MQFB_QUIT                   CONSTANT BINARY_INTEGER := 256;
    PGM_SUP.MQFB_CHANNEL_COMPLETED      CONSTANT BINARY_INTEGER := 262;
    PGM_SUP.MQFB_CHANNEL_FAIL_RETRY     CONSTANT BINARY_INTEGER := 263;
    PGM_SUP.MQFB_CHANNEL_FAIL           CONSTANT BINARY_INTEGER := 264;
    PGM_SUP.MQFB_APPL_CANNOT_BE_STARTED CONSTANT BINARY_INTEGER := 265;
    PGM_SUP.MQFB_TM_ERROR               CONSTANT BINARY_INTEGER := 266;
    PGM_SUP.MQFB_APPL_TYPE_ERROR        CONSTANT BINARY_INTEGER := 267;
    PGM_SUP.MQFB_STOPPED_BY_MSG_EXIT    CONSTANT BINARY_INTEGER := 268;
    PGM_SUP.MQFB_XMIT_Q_MSG_ERROR       CONSTANT BINARY_INTEGER := 271;
    PGM_SUP.MQFB_SYSTEM_LAST            CONSTANT BINARY_INTEGER := 65535;
    PGM_SUP.MQFB_APPL_FIRST             CONSTANT BINARY_INTEGER := 65536;
    PGM_SUP.MQFB_APPL_LAST              CONSTANT BINARY_INTEGER := 999999999;

##### FORMAT Field

    MQFMT_NONE               constant char(8) := '        ';
    MQFMT_ADMIN              constant char(8) := 'MQADMIN ';
    MQFMT_CHANNEL_COMPLETED  constant char(8) := 'MQCHCOM ';
    MQFMT_CICS               constant char(8) := 'MQCICS  ';
    MQFMT_COMMAND_1          constant char(8) := 'MQCMD1  ';
    MQFMT_COMMAND_2          constant char(8) := 'MQCMD2  ';
    MQFMT_DEAD_LETTER_HEADER constant char(8) := 'MQDEAD  ';
    MQFMT_DIST_HEADER        constant char(8) := 'MQHDIST ';
    MQFMT_EVENT              constant char(8) := 'MQEVENT ';
    MQFMT_IMS                constant char(8) := 'MQIMS   ';
    MQFMT_IMS_VAR_STRING     constant char(8) := 'MQIMSVS ';
    MQFMT_MD_EXTENTION       constant char(8) := 'MQHMDE  ';
    MQFMT_PCF                constant char(8) := 'MQPCF   ';
    MQFMT_REF_MSG_HEADER     constant char(8) := 'MQHREF  ';
    MQFMT_STRING             constant char(8) := 'MQSTR   ';
    MQFMT_TRIGGER            constant char(8) := 'MQTRIG  ';
    MQFMT_WORK_INFO_HEADER   constant char(8) := 'MQHWIH  ';
    MQFMT_XMIT_Q_HEADER      constant char(8) := 'MQXMIT  ';

##### MSGTYPE Field

    PGM_SUP.MQMT_SYSTEM_FIRST CONSTANT BINARY_INTEGER := 1;
    PGM_SUP.MQMT_REQUEST      CONSTANT BINARY_INTEGER := 1;
    PGM_SUP.MQMT_REPLY        CONSTANT BINARY_INTEGER := 2;
    PGM_SUP.MQMT_DATAGRAM     CONSTANT BINARY_INTEGER := 8;
    PGM_SUP.MQMT_REPORT       CONSTANT BINARY_INTEGER := 4;
    PGM_SUP.MQMT_SYSTEM_LAST  CONSTANT BINARY_INTEGER := 65535;
    PGM_SUP.MQMT_APPL_FIRST   CONSTANT BINARY_INTEGER := 65536;
    PGM_SUP.MQMT_APPL_LAST    CONSTANT BINARY_INTEGER := 999999999;

##### PERSISTENCE Field

    PGM_SUP.MQPER_PERSISTENT           CONSTANT BINARY_INTEGER := 1;
    PGM_SUP.MQPER_NOT_PERSISTENT       CONSTANT BINARY_INTEGER := 0;
    PGM_SUP.MQPER_PERSISTENCE_AS_Q_DEF CONSTANT BINARY_INTEGER := 2;

##### PRIORITY Field

    PGM_SUP.MQPRI_PRIORITY_AS_Q_DEF CONSTANT BINARY_INTEGER := -1;
    PGM_SUP.MQPRI_MIN_PRIORITY      CONSTANT BINARY_INTEGER := 0;
    PGM_SUP.MQPRI_MAX_PRIORITY      CONSTANT BINARY_INTEGER := 9;

##### PUTAPPLTYPE Field

    MQAT_UNKNOWN     constant binary_integer := -1;
    MQAT_NO_CONTEXT  constant binary_integer := 0;
    MQAT_CICS        constant binary_integer := 1;
    MQAT_MVS         constant binary_integer := 2;
    MQAT_OS390       constant binary_integer := 2;
    MQAT_IMS         constant binary_integer := 3;
    MQAT_OS2         constant binary_integer := 4;
    MQAT_DOS         constant binary_integer := 5;
    MQAT_AIX         constant binary_integer := 6;
    MQAT_UNIX        constant binary_integer := 6;
    MQAT_QMGR        constant binary_integer := 7;
    MQAT_OS400       constant binary_integer := 8;
    MQAT_WINDOWS     constant binary_integer := 9;
    MQAT_CICS_VSE    constant binary_integer := 10;
    MQAT_WINDOWS_NT  constant binary_integer := 11;
    MQAT_VMS         constant binary_integer := 12;
    MQAT_GUARDIAN    constant binary_integer := 13;
    MQAT_NSK         constant binary_integer := 13;
    MQAT_VOS         constant binary_integer := 14;
    MQAT_IMS_BRIDGE  constant binary_integer := 19;
    MQAT_XCF         constant binary_integer := 20;
    MQAT_CICS_BRIDGE constant binary_integer := 21;
    MQAT_NOTES_AGENT constant binary_integer := 22;
    MQAT_USER_FIRST  constant binary_integer := 65536;
    MQAT_USER_LAST   constant binary_integer := 999999999;
    MQAT_DEFAULT     constant binary_integer := 6;

##### REPORT Field

    MQRO_NEW_MSG_ID                constant raw(4) := '00000000';
    MQRO_COPY_MSG_ID_TO_CORREL_ID  constant raw(4) := '00000000';
    MQRO_DEAD_LETTER_Q             constant raw(4) := '00000000';
    MQRO_NONE                      constant raw(4) := '00000000';
    MQRO_PAN                       constant raw(4) := '00000001';
    MQRO_NAN                       constant raw(4) := '00000002';
    MQRO_PASS_CORREL_ID            constant raw(4) := '00000040';
    MQRO_PASS_MSG_ID               constant raw(4) := '00000080';
    MQRO_COA                       constant raw(4) := '00000100';
    MQRO_COA_WITH_DATA             constant raw(4) := '00000300';
    MQRO_COA_WITH_FULL_DATA        constant raw(4) := '00000700';
    MQRO_COD                       constant raw(4) := '00000800';
    MQRO_COD_WITH_DATA             constant raw(4) := '00001800';
    MQRO_COD_WITH_FULL_DATA        constant raw(4) := '00003800';
    MQRO_EXPIRATION                constant raw(4) := '00200000';
    MQRO_EXPIRATION_WITH_DATA      constant raw(4) := '00600000';
    MQRO_EXPIRATION_WITH_FULL_DATA constant raw(4) := '00E00000';
    MQRO_EXCEPTION                 constant raw(4) := '01000000';
    MQRO_EXCEPTION_WITH_DATA       constant raw(4) := '03000000';
    MQRO_EXCEPTION_WITH_FULL_DATA  constant raw(4) := '07000000';
    MQRO_DISCARD_MSG               constant raw(4) := '08000000';

##### VERSION Field

    MQMD_VERSION_1                constant binary_integer := 1;
    MQMD_VERSION_2                constant binary_integer := 2;
    MQMD_CURRENT_VERSION          constant binary_integer := 2;

##### Report Field, Mask Values

    PGM_SUP.MQRO_REJECT_UNSUP_MASK         CONSTANT RAW(4) := '101c0000';
    PGM_SUP.MQRO_ACCEPT_UNSUP_MASK         CONSTANT RAW(4) := 'efe000ff';
    PGM_SUP.MQRO_ACCEPT_UNSUP_IF_XMIT_MASK CONSTANT RAW(4) := '0003ff00';

#### PGM.MQOD Values

These topics provide information about `PGM`.`MQOD` values.

##### OBJECTTYPE Field

    PGM_SUP.MQOT_Q       CONSTANT BINARY_INTEGER := 1;
    PGM_SUP.MQOT_PROCESS CONSTANT BINARY_INTEGER := 3;
    PGM_SUP.MQOT_Q_MGR   CONSTANT BINARY_INTEGER := 5;
    PGM_SUP.MQOT_CHANNEL CONSTANT BINARY_INTEGER := 6;

##### OBJECTTYPE Field, Extended Values

    MQOT_ALL               constant binary_integer := 1001;
    MQOT_ALIAS_Q           constant binary_integer := 1002;
    MQOT_MODEL_Q           constant binary_integer := 1003;
    MQOT_LOCAL_Q           constant binary_integer := 1004;
    MQOT_REMOTE_Q          constant binary_integer := 1005;
    MQOT_SENDER_CHANNEL    constant binary_integer := 1007;
    MQOT_SERVER_CHANNEL    constant binary_integer := 1008;
    MQOT_REQUESTER_CHANNEL constant binary_integer := 1009;
    MQOT_RECEIVER_CHANNEL  constant binary_integer := 1010;
    MQOT_CURRENT_CHANNEL   constant binary_integer := 1011;
    MQOT_SAVED_CHANNEL     constant binary_integer := 1012;
    MQOT_SVRCONN_CHANNEL   constant binary_integer := 1013;
    MQOT_CLNTCONN_CHANNEL  constant binary_integer := 1014;

##### VERSION Field

    MQOD_VERSION_1                constant binary_integer := 1;
    MQOD_VERSION_2                constant binary_integer := 2;
    MQOD_CURRENT_VERSION          constant binary_integer := 2;

#### PGM.MQPMO Values

These topics provide information about `PGM`.`MQPMO` values.

##### OPTIONS Field

    MQPMO_NONE                     constant binary_integer := 0;
    MQPMO_SYNCPOINT                constant binary_integer := 2;
    MQPMO_NO_SYNCPOINT             constant binary_integer := 4;
    MQPMO_DEFAULT_CONTEXT          constant binary_integer := 32;
    MQPMO_NEW_MSG_ID               constant binary_integer := 64;
    MQPMO_NEW_CORREL_ID            constant binary_integer := 128;
    MQPMO_PASS_IDENTITY_CONTEXT    constant binary_integer := 256;
    MQPMO_PASS_ALL_CONTEXT         constant binary_integer := 512;
    MQPMO_SET_IDENTITY_CONTEXT     constant binary_integer := 1024;
    MQPMO_SET_ALL_CONTEXT          constant binary_integer := 2048;
    MQPMO_ALTERNATE_USER_AUTHORITY constant binary_integer := 4096;
    MQPMO_FAIL_IF_QUIESCING        constant binary_integer := 8192;
    MQPMO_NO_CONTEXT               constant binary_integer := 16384;
    MQPMO_LOGICAL_ORDER            constant binary_integer := 32768;

##### VERSION Field

    MQPMO_VERSION_1                constant binary_integer := 1;
    MQPMO_VERSION_2                constant binary_integer := 2;
    MQPMO_CURRENT_VERSION          constant binary_integer := 2;

#### MQCLOSE Values

These topics provide information about `MQCLOSE` values.

##### hobj Argument

    PGM_SUP.MQHO_UNUSABLE_HOBJ CONSTANT BINARY_INTEGER := -1;

##### options Argument

    PGM_SUP.MQCO_NONE         CONSTANT BINARY_INTEGER := 0;
    PGM_SUP.MQCO_DELETE       CONSTANT BINARY_INTEGER := 1;
    PGM_SUP.MQCO_DELETE_PURGE CONSTANT BINARY_INTEGER := 2;

#### MQOPEN Values

These topics provide information about `MQOPEN` values.

##### options Argument

    MQOO_BIND_AS_Q_DEF            constant binary_integer := 0;
    MQOO_INPUT_AS_Q_DEF           constant binary_integer := 1;
    MQOO_INPUT_SHARED             constant binary_integer := 2;
    MQOO_INPUT_EXCLUSIVE          constant binary_integer := 4;
    MQOO_BROWSE                   constant binary_integer := 8;
    MQOO_OUTPUT                   constant binary_integer := 16;
    MQOO_INQUIRE                  constant binary_integer := 32;
    MQOO_SET                      constant binary_integer := 64;
    MQOO_SAVE_ALL_CONTEXT         constant binary_integer := 128;
    MQOO_PASS_IDENTITY_CONTEXT    constant binary_integer := 256;
    MQOO_PASS_ALL_CONTEXT         constant binary_integer := 512;
    MQOO_SET_IDENTITY_CONTEXT     constant binary_integer := 1024;
    MQOO_SET_ALL_CONTEXT          constant binary_integer := 2048;
    MQOO_ALTERNATE_USER_AUTHORITY constant binary_integer := 4096;
    MQOO_FAIL_IF_QUIESCING        constant binary_integer := 8192;
    MQOO_BIND_ON_OPEN             constant binary_integer := 16384;
    MQOO_BIND_NOT_FIXED           constant binary_integer := 32768;
    MQOO_RESOLVE_NAMES            constant binary_integer := 65536;

#### Maximum Lengths for Fields of PGM Type Definitions

These constants contain the maximum lengths allowed for fields used by the PGM Type Definitions.

For example, the constant `PGM_SUP`.`MQ_ACCOUNTING_TOKEN_LENGTH` specifies that the maximum length for `PGM`.`MQMD`.`ACCOUNTINGTOKEN` is 32 characters.

    MQ_ABEND_CODE_LENGTH         constant binary_integer :=  4;
    MQ_ACCOUNTING_TOKEN_LENGTH   constant binary_integer :=  32;
    MQ_APPL_IDENTITY_DATA_LENGTH constant binary_integer :=  32;
    MQ_APPL_ORIGIN_DATA_LENGTH   constant binary_integer :=  4;
    MQ_ATTENTION_ID_LENGTH       constant binary_integer :=  4;
    MQ_AUTHENTICATOR_LENGTH      constant binary_integer :=  8;
    MQ_CANCEL_CODE_LENGTH        constant binary_integer :=  4;
    MQ_CLUSTER_NAME_LENGTH       constant binary_integer :=  48;
    MQ_CORREL_ID_LENGTH          constant binary_integer :=  24;
    MQ_CREATION_DATE_LENGTH      constant binary_integer :=  12;
    MQ_CREATION_TIME_LENGTH      constant binary_integer :=  8;
    MQ_DATE_LENGTH               constant binary_integer :=  12;
    MQ_EXIT_NAME_LENGTH          constant binary_integer :=  128;
    MQ_FACILITY_LENGTH           constant binary_integer :=  8;
    MQ_FACILITY_LIKE_LENGTH      constant binary_integer :=  4;
    MQ_FORMAT_LENGTH             constant binary_integer :=  8;
    MQ_FUNCTION_LENGTH           constant binary_integer :=  4;
    MQ_GROUP_ID_LENGTH           constant binary_integer :=  24;
    MQ_LTERM_OVERRIDE_LENGTH     constant binary_integer :=  8;
    MQ_MFS_MAP_NAME_LENGTH       constant binary_integer :=  8;
    MQ_MSG_HEADER_LENGTH         constant binary_integer :=  4000;
    MQ_MSG_ID_LENGTH             constant binary_integer :=  24;
    MQ_MSG_TOKEN_LENGTH          constant binary_integer :=  16;
    MQ_NAMELIST_DESC_LENGTH      constant binary_integer :=  64;
    MQ_NAMELIST_NAME_LENGTH      constant binary_integer :=  48;
    MQ_OBJECT_INSTANCE_ID_LENGTH constant binary_integer :=  24;
    MQ_NAME_LENGTH               constant binary_integer :=  48;
    MQ_PROCESS_APPL_ID_LENGTH    constant binary_integer :=  256;
    MQ_PROCESS_DESC_LENGTH       constant binary_integer :=  64;
    MQ_PROCESS_ENV_DATA_LENGTH   constant binary_integer :=  128;
    MQ_PROCESS_NAME_LENGTH       constant binary_integer :=  48;
    MQ_PROCESS_USER_DATA_LENGTH  constant binary_integer :=  128;
    MQ_PUT_APPL_NAME_LENGTH      constant binary_integer :=  28;
    MQ_PUT_DATE_LENGTH           constant binary_integer :=  8;
    MQ_PUT_TIME_LENGTH           constant binary_integer :=  8;
    MQ_Q_DESC_LENGTH             constant binary_integer :=  64;
    MQ_Q_MGR_DESC_LENGTH         constant binary_integer :=  64;
    MQ_Q_MGR_IDENTIFIER_LENGTH   constant binary_integer :=  48;
    MQ_Q_MGR_NAME_LENGTH         constant binary_integer :=  48;
    MQ_Q_NAME_LENGTH             constant binary_integer :=  48;
    MQ_REMOTE_SYS_ID_LENGTH      constant binary_integer :=  4;
    MQ_SERVICE_NAME_LENGTH       constant binary_integer :=  32;
    MQ_SERVICE_STEP_LENGTH       constant binary_integer :=  8;
    MQ_START_CODE_LENGTH         constant binary_integer :=  4;
    MQ_STORAGE_CLASS_LENGTH      constant binary_integer :=  8;
    MQ_TIME_LENGTH               constant binary_integer :=  8;
    MQ_TRAN_INSTANCE_ID_LENGTH   constant binary_integer :=  16;
    MQ_TRANSACTION_ID_LENGTH     constant binary_integer :=  4;
    MQ_TP_NAME_LENGTH            constant binary_integer :=  64;
    MQ_TRIGGER_DATA_LENGTH       constant binary_integer :=  64;
    MQ_USER_ID_LENGTH            constant binary_integer :=  12;

#### Error Code Definitions

This topic describes some error code definitions.

##### Error Code -29400: Data Cartridge Error

This error code indicates that the MQI opcode implemented in DG4MQ fails. Refer to IBM WebSphere reference manual for information about the cause by looking up the opcode and its completion code and reason code.

    MQI opcode failed. completion code=xxxx. reason code=xxxx.

Example A-3 test.sql

    --
    -- Copyright Oracle, 2005 All Rights Reserved.
    --
    -- NAME
    --   test.sql
    --
    -- DESCRIPTION
    --
    --   Specify the database link name you created for the gateway. To do this,
    --   replace the database link name 'YOUR_DBLINK_NAME' with the dblink name
    --   you chose when the database link was created.
    --
    --   This script performs a test run for the MQSeries gateway. In this
    --   script the queuename is 'YOUR_QUEUE_NAME', replace queuename with
    --   a valid queue name at the queue manager the gateway is configured
    --   for.
    --
    --   First the script puts a raw message of 10 bytes on the specified
    --   queue.
    --
    --   When successfully completed the put operation, the script does a
    --   get on the same queue to read the message back.
    --
    --   The contents of both messages put and retrieved from the queue are
    --   printed to standard out for verification by the user.
    --
    -- NOTES
    --   Run the script from the SQL*Plus command line.
    --
    --   Make the sure the user is granted 'EXECUTE' on package dbms_output
    --

    set serveroutput on

    declare

      objdesc    PGM.MQOD;
      hobj       PGM.MQOH;
      msgdesc    PGM.MQMD;
      putmsgopts PGM.MQPMO;
      getmsgopts PGM.MQGMO;
      options    binary_integer;
      putbuffer  raw(10) := '10203040506070809000';
      getbuffer  raw(10);

    begin

      --
      -- Print the message we are putting on the queue
      --

      dbms_output.put_line('message put on queue = ' || rawtohex(putbuffer));

      --
      -- Specify queue name and dblink name (replace with proper names).
      --
      objdesc.objectname := 'YOUR_QUEUE_NAME';
      objdesc.dblinkname := 'YOUR_DBLINK_NAME';

      --
      -- Specify a put operation.
      --

      options := pgm_sup.MQOO_OUTPUT;

      --
      -- Open the queue.
      --

      PGM.MQOPEN(objdesc, options, hobj);

      --
      -- Put the message buffer on the queue.
      --

      PGM.MQPUT(hobj, msgdesc, putmsgopts, putbuffer);

      --
      -- Define close options.
      --

      options := pgm_sup.MQCO_NONE;

      --
      -- Close queue.
      --

      PGM.MQCLOSE(hobj, options);

      --
      -- Specify a get operation.
      --

      options := pgm_sup.MQOO_INPUT_AS_Q_DEF;

      --
      -- Open queue.
      --

      PGM.MQOPEN(objdesc, options, hobj);

      --
      -- Get message from the queue.
      --

      getmsgopts.msglength := 10;
      PGM.MQGET(hobj, msgdesc, getmsgopts, getbuffer);

      --
      -- Define close options.
      --

      options := pgm_sup.MQCO_NONE;

      --
      -- Close the queue again.
      --

      PGM.MQCLOSE(hobj, options);

      --
      -- Print the result
      --

      dbms_output.put_line('message read back = ' || rawtohex(getbuffer));

    exception

      --
      -- When no more messages... tell the user and close the queue.
      --

      when pgm_sup.NO_MORE_MESSAGES then
        dbms_output.put_line('Warning: No message found on the queue');
        options := pgm_sup.MQCO_NONE;
        PGM.MQCLOSE(hobj, options);

      --
      -- something else went wrong.. tell the user.
      --
      when others then
        dbms_output.put_line('Error: Procedural Gateway for IBM MQSeries verification
     script failed.');
        dbms_output.put_line(SQLERRM);

    end;
    /
