Migrating to new instances of the Oracle Database Gateway for APPC from an existing installation is straightforward, provided you follow some guidelines. The following topics provide information to make these new installations as easy as possible. They also provide the parameters you will need if you are using the TCP/IP for IMS Connect communication protocol on your gateway.

- Migrating an Existing Gateway Instance to New Release Using SNA Protocol

- Migrating from an Existing Gateway Using SNA to TCP/IP

### Migrating an Existing Gateway Instance to New Release Using SNA Protocol

Follow these steps to migrate an existing gateway to 12c Release 2 (12.2) of the gateway using the SNA communication protocol.

Note that if you are using the gateway's TCP/IP support for IMS Connect, you will not be migrating an existing release to the current release of the gateway. However, you will need to place valid Heterogeneous Services parameters into your initsid.ora file. Proceed to "Parameter Changes: Version 4 to 12c Release 2 (12.2) of the Gateway".

#### Step 1: Install the New Release

Install the new release of the gateway in a separate directory as outlined in [Installing the Gateway](appc-gateway-installation.md).

**Note:**

Do not install the gateway over an existing gateway installation. Doing so will corrupt the existing installation.

#### Step 2: Transfer initsid.ora Gateway Initialization File Parameters

Copy the `init``sid``.ora` file from the old gateway instance to the new instance.

Note that if you are migrating from Release 9.0.1 or earlier of the gateway, then `PGA_TRACE` is not supported, you will need to modify the parameter to `TRACE_LEVEL`, instead.

**Note:**

If you are using `TRACE_LEVEL`, then you must set the path for the `LOG_DESTINATION` parameter.

#### Backout Considerations When Migrating to New Releases

Oracle recommends that you keep the old gateway Oracle home directory and instance configurations intact and operational when you are installing a new release of the gateway and upgrading existing instances, in case there are problems with the upgrade. This will help ensure minimal downtime between changes to different gateway instances.

#### Oracle Net Considerations

The Oracle Database Gateway for APPC uses the Heterogeneous Services (HS) facilities of Oracle and Oracle Net. If you are upgrading from a version 4 gateway, then you need to slightly modify the gateway service name entries in the `tnsnames.ora` file. Add an `(HS=)` clause to communicate to Oracle Net that the gateway uses HS facilities. For more information, refer to [Configuring Your Oracle Network](appc-gateway-configure-oracle-network.md).

#### Parameter Changes: Version 4 to 12c Release 2 (12.2) of the Gateway

This release of the Oracle Database Gateway for APPC introduces new and changed initialization parameters if you are migrating from version 4 gateway to 12c Release 2 (12.2) of the gateway.

**Note:**

This section does not apply to you if you are migrating to 12c Release 2 (12.2) from version 8 of the Oracle Database Gateway for APPC.

If you are using the gateway's TCP/IP support for IMS Connect, then you will not be migrating from version 4 to the current release of the gateway. However, you will need to place valid Heterogeneous Services parameters into your `init``sid``.ora` file.

The following topics contain references to the particular HS parameters you need to run the gateway.

**Note:**

Refer to the [Oracle Database Heterogeneous Connectivity User's Guide](../heter/index.md) for a complete list and descriptions of all HS parameters used in Oracle products.

##### New Gateway Initialization Parameters

The following parameters are in the gateway initialization file (`init``sid``.ora`):

- `FDS_CLASS`

- `FDS_INSTANCE`

- `HS_FDS_FETCH_ROWS`

- `LOG_DESTINATION`

- `TRACE_LEVEL`

- `PGA_TCP_DB` (TCP/IP only)

- `PGA_TCP_USER` (TCP/IP only)

- `PGA_TCP_PASS` (TCP/IP only)

  **Note:**

  The `HS_` parameters are specific to Oracle Heterogeneous Services. For details on HS parameters, refer to the [Oracle Database Administrator's Guide](../admin/index.md).

##### Renamed Gateway Initialization File Parameters

Following is a list of the gateway initialization file (initsid.ora) parameters that have been renamed in this release of the gateway, the parameters' former names are shown in parentheses.

- `HS_COMMIT_STRENGTH_POINT` (`COMMIT_STRENGTH_POINT`)

- `HS_DB_DOMAIN` ( `DB_DOMAIN`)

- `HS_DB_INTERNAL_NAME` (`DB_INTERNAL_NAME`)

- `HS_DB_NAME` (`DB_NAME`)

- `HS_DESCRIBE_CACHE_HWM` (`DESCRIBE_CACHE_HWM`)

- `HS_LANGUAGE` (`LANGUAGE`)

- `HS_NLS_DATE_FORMAT` (`NLS_DATE_FORMAT`)

- `HS_NLS_DATE_LANGUAGE` (`NLS_DATE_LANGUAGE`)

- `HS_OPEN_CURSORS` (`OPEN_CURSORS`)

- `HS_ROWID_CACHE_SIZE` (`ROWID_CACHE_SIZE`)

##### Obsolete Parameters

The following parameters are now obsolete. Please remove them from your configuration files:

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

The following startup shell script parameter must be added to initsid.ora if you are migrating from version 4 or version 8 gateway to the current release of the Oracle Database Gateway for APPC:

- `FDS_CLASS_VERSION`

#### Migrating from Gateway Release 9.0.1 or 9.2.0 to Gateway 12c Release 2 (12.2)

No new parameters were added between release 9.0.1 and this release of the gateway.

### Migrating from an Existing Gateway Using SNA to TCP/IP

The following sections are for users who have an existing release of the gateway using the SNA protocol but who wish to switch to using TCP/IP support for IMS Connect.

The TCP/IP support for IMS Connect feature in this release of the gateway allows you to continue to use existing TIPs.

#### To Use Existing TIPs with Existing Side Profile Definitions

Follow these instructions:

1.  Make sure you have used the `pg4tcpmap` tool to insert valid parameter values into the `PGA_TCP_IMSC` table.
    Refer to [Gateway Configuration Using TCP/IP Communication Protocol](configure-appc-gateway-using-tcp-ip.md) for instructions on loading the `PGA_TCP_IMSC` table.
2.  Make sure that the `LANGUAGE` parameter in your TIPs is set to `american_america_us7ascii`.
3.  Use PGAU to regenerate the IMS TIPs.
4.  Add the following new TCP/IP parameters to the initsid.ora file:
    - `PGA_TCP_DB`

    - `PGA_TCP_USER`

    - `PGA_TCP_PASS`

    You will find descriptions and information about adding these parameters in Parameter Changes: Version 4 to 12c Release 2 (12.2) of the GatewayParameter Changes: Version 4 to 12c Release 2 (12.2) of the Gateway. You will also find descriptions of the parameters in [Gateway Initialization Parameters for TCP/IP Communication Protocol](appc-gateway-initialization-parameters-tcp-ip.md).

    **Note:**

    If your TIPs from a previous version of the gateway were already defined using a side profile name and the `NLS_``LANGUAGE` parameter has been set to a value of `american_america_us7ascii`, then you will not need to recompile these TIPs. You will still need to map your parameter values using the pg4tcpmap tool.

    **Note:**

    TIPS must be recompiled when changing the communication protocol from SNA to TCP/IP.

    If you have existing TIPs that were generated previously on a gateway using the SNA protocol and you want to use the new TCP/IP feature, then the TIPs will have to be regenerated by PGAU with mandatory `NLS_LANGUAGE` and Side Profile Settings. Specify the suitable ASCII character set in the `DEFINE TRANSACTION` command.

    This is due to the fact that the gateway assumes that the suitable user exit in IMS Connect is being used, which would translate between the suitable ASCII and EBCDIC character sets.
