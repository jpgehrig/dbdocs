Migrating to new instances of Oracle Database Gateway for APPC from an existing installation is straightforward, provided you follow some guidelines. The following topics provide information to make these new installations as easy as possible. They also provide the parameters you need if you are using the TCP/IP for IMS Connect communication protocol on your gateway.

The following sections provide information that is specific to this release of Oracle Database Gateway for APPC for IBM AIX on POWER Systems (64-Bit), Linux x86-64, Oracle Solaris on SPARC (64-Bit), and HP-UX Itanium:

- Migrating An Existing Gateway Instance to a New Release Using SNA Protocol

- Migrating from an Existing Gateway to TCP/IP Using SNA

### Migrating An Existing Gateway Instance to a New Release Using SNA Protocol

Follow these steps to migrate an existing gateway to12c Release 2 (12.2) of the gateway using the SNA communication protocol.

Note that if you are using the gateway TCP/IP support for IMS Connect, you will not be migrating an existing release to the current release of the gateway. However, you will need to place valid Heterogeneous Services parameters into your `init``sid.``ora` file. Proceed to "Parameter Changes: Version 4 to 12c Release 2 (12.2) of the Gateway".

#### Step 1: Install the New Release

Install the new release of the gateway in a separate directory as outlined in [Installing the Gateway](appc-gateway-installation.md).

**Note:**

Do not install the gateway over a previously existing gateway installation. Doing this corrupts the existing installation.

#### Step 2: Transferring the initsid.ora Gateway Initialization File Parameters

Copy the `init``sid.``ora` file from the old gateway instance to the new instance.

If you are migrating from Release 9.0.1 or earlier of the gateway, `PGA_TRACE` is not supported. You need to modify the parameter to `TRACE_LEVEL` instead.

**Note:**

If you are using `TRACE_LEVEL`, you must set the path for the `LOG_DESTINATION` parameter.

If you have encrypted some of the parameters at file `init``sid``.ora` by using `dg4pwd`, copy the `$ORACLE_HOMRE/dg4appc/admin/init``sid``.pwd` file from the old gateway instance to the new instance.

**Note:**

If you are migrating from Release 9.0.1 or earlier of the gateway, you do not need to copy this file into the new instance.

#### Backout Considerations When Migrating to New Releases

Oracle recommends that you keep the old gateway Oracle home directory and instance configurations intact and operational when you are installing a new release of the gateway and upgrading existing instances, in case there are problems with the upgrade. This helps to ensure minimum down time between changes to different gateway instances.

#### Oracle Net Considerations

Oracle Database Gateway for APPC uses the Heterogeneous Services (HS) facilities of Oracle and Oracle Net. If you are upgrading from a version 4 gateway, then you need to slightly modify the gateway service name entries in the `tnsnames.ora` file. Add an `(HS=)` clause to tell Oracle Net that the gateway uses HS facilities. For more information, refer to [Configuring Your Oracle Network](appc-gateway-config-oracle-network.md).

#### Parameter Changes: Version 4 to 12c Release 2 (12.2) of the Gateway

This release of Oracle Database Gateway for APPC introduces new and changed initialization parameters if you are migrating from a Version 4 gateway to 12c Release 2 (12.2) of the gateway.

**Note:**

The "Parameter Changes: Version 4 to 12c Release 2 (12.2) of the Gateway" section does not apply to you if you are migrating to Release 10.2.0 from Version 8 of the Oracle Database Gateway for APPC.

If you are using the gateway TCP/IP support for IMS Connect, you will not be migrating from Version 4 to the current release of the gateway. However, you need to place valid Heterogeneous Services parameters into your `init``sid.``ora` file.

Migration from existing gateways contains references to the particular HS parameters that you need to run the gateway.

**Note:**

Refer to the [Oracle Database Heterogeneous Connectivity User's Guide](../heter/index.md) for a complete list and descriptions of all HS parameters used in Oracle products.

##### New Gateway Initialization Parameters

The following parameters are in the gateway initialization file (`init``sid.``ora`):

- `FDS_CLASS`

- `FDS_INSTANCE`

- `HS_FDS_FETCH_ROWS`

- `LOG_DESTINATION`

- `TRACE_LEVEL`

- `PGA_TCP_DB` (TCP/IP only)

- `PGA_TCP_USER` (TCP/IP only)

- `PGA_TCP_PASS` (TCP/IP only)

  **Note:**

  The `HS_` parameters are specific to Oracle Heterogeneous Services. For details on HS parameters, refer to the[ Oracle Database Heterogeneous Connectivity User's Guide](../heter/index.md).

##### Renamed Gateway Initialization File Parameters

Following is a list of the gateway initialization file (`init``sid.``ora`) parameters that have been renamed in this release of the gateway. The former names of the parameters are shown in parentheses.

- `HS_COMMIT_STRENGTH_POINT` (formerly `COMMIT_STRENGTH_POINT`)

- `HS_DB_DOMAIN` (formerly `DB_DOMAIN`)

- `HS_DB_INTERNAL_NAME` (formerly `DB_INTERNAL_NAME`)

- `HS_DB_NAME` (formerly `DB_NAME`)

- `HS_DESCRIBE_CACHE_HWM` (formerly `DESCRIBE_CACHE_HWM`)

- `HS_LANGUAGE` (formerly `LANGUAGE`)

- `HS_NLS_DATE_FORMAT` (formerly `NLS_DATE_FORMAT`)

- `HS_NLS_DATE_LANGUAGE` (formerly `NLS_DATE_LANGUAGE`)

- `HS_OPEN_CURSORS` (formerly `OPEN_CURSORS`)

- `HS_ROWID_CACHE_SIZE` (formerly `ROWID_CACHE_SIZE`)

##### Obsolete Parameters

The following parameters are obsolete. If necessary, remove them from your configuration files:

- `MODE`

- `SERVER_PATH`

- `ERROR_LOGGING`

- `ERROR_REPORTING`

- `ERRORTAG`

- `GATEWAY_SID`

- `GROUP_BY_OFF`

- `GTWDEBUG`

- `INCREMENT_CURSORS`

- `INIT_CURSORS`

- `LIST`

- `MAX_LOG_SIZE`

- `OPTIMIZE_FILE_OPEN`

- `ORDER_BY_OFF`

- `RESOLVE_BINDS`

- `RETRY`

- `SET`

- `SNMP_SUPPORT`

- `SQL_TRACE`

- `TRIM_CURSORS`

- `D_OPEN_CURSORS`

- `D_INIT_CURSORS`

- `D_INCREMENT_CURSORS`

- `D_TRIM_CURSORS`

- `PGA_TRACE`

#### Parameter Changes: Version 8 or Earlier to Gateway 12c Release 2 (12.2)

The following startup shell script parameter must be added to `init``sid.``ora` if you are migrating from a Version 4 or Version 8 gateway to 12c Release 2 (12.2) of the Oracle Database Gateway for APPC:

- `FDS_CLASS_VERSION`

#### Migrating from Gateway Release 9.0.1 or 9.2.0 or 10.1.0 to Gateway 12c Release 2 (12.2)

No new parameters were added between release 9.0.1 and this release of the gateway.

### Migrating from an Existing Gateway to TCP/IP Using SNA

The following sections are for those users who have an existing release of the gateway using the SNA protocol, but who want to switch to using TCP/IP support for IMS Connect.

The TCP/IP support for IMS Connect feature in this release of the gateway enables you to continue to use existing TIPs.

#### Using Existing TIPs with Existing Side Profile Definitions

Follow these instructions:

1.  Make sure you have used the `pg4tcpmap` tool to insert valid parameter values into the `PGA_TCP_IMSC` table.
    Refer to [Gateway Configuration Using TCP/IP Communication Protocol](config-appc-gateway-using-tcp-ip.md) for instructions to load the `PGA_TCP_IMSC` table.
2.  Make sure the `LANGUAGE` parameter in your TIPs is set to `american_america_us7ascii`.
3.  Use PGAU to regenerate the IMS TIPs.
4.  Add the following new TCP/IP parameters to the `init``sid.``ora` file:
    - `PGA_TCP_DB`

    - `PGA_TCP_USER`

    - `PGA_TCP_PASS`

    You will find descriptions and information about adding these parameters in Parameter Changes: Version 4 to 12c Release 2 (12.2) of the Gateway. You will also find descriptions of the parameters in [Gateway Initialization Parameters for TCP/IP Communication Protocol](appc-gateway-initialization-parameters-tcp-ip.md) .

    **Note:**

    If your TIPs from a previous version of the gateway were already defined using a SideProfileName and the `NLS_ LANGUAGE` parameter has been set to a value of `american_america_us7ascii`, then you will not need to recompile these TIPs. You still need to map your parameter values using the `pg4tcpmap` tool.

    **Note:**

    TIPs must be recompiled when changing communication protocol from SNA to TCP/IP.

    If you have existing TIPs that were generated previously on a gateway using the SNA communication package protocol, and you want to use the new TCP/IP feature, then the TIPs have to be regenerated by PGAU with mandatory `NLS_LANGUAGE` and Side Profile Settings. Specify the appropriate ASCII character set in the `DEFINE TRANSACTION` command.

    This is because the gateway assumes that the appropriate user exit in IMS Connect is being used, which would translate between the appropriate ASCII and EBCDIC character sets.
