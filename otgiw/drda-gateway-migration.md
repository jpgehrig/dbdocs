This section describes how to migrate to new instances of Oracle Database Gateway for DRDA from an existing installation. Perform the following steps to migrate to a new release of Oracle Database Gateway for DRDA from an existing release:

1.  Install the New Release

2.  Use the New Gateway Initialization Parameter File

3.  Update the Initialization Parameters

4.  Bind Gateway Package

5.  Install or Upgrade Data Dictionary Views

### Install the New Release

Install the new release of the gateway in a separate directory, as discussed in [Installing Oracle Database Gateway for DRDA](install-drda-gateway.md) .

**Note:**

Do not install the gateway over a previously existing gateway installation. This corrupts the existing installation.

### Use the New Gateway Initialization Parameter File

This release of Database Gateway for DRDA has a completely new architecture. Most of the prior parameters are obsolete. You should not use the old initialization file as a base and try to modify it. Instead, you should use the new initialization generated as part of installation as a base. Refer to [Initialization Parameters](init-param-gateway.md) for the syntax of the parameters.

Existing TG4DB2 customer migrating to this release of Database Gateway for DRDA would need to provide the recovery user's password `HS_FDS_RECOVERY_PWD`, with this release of gateway.

### Update the Initialization Parameters

The next step in migrating to a new release of Oracle Database Gateway for DRDA consists of updating the initialization parameters.

#### Changed Parameters

The use of `DRDA_CONNECT_PARM` has changed in this version. Refer to [Initialization Parameters](init-param-gateway.md) for the syntax of the parameter.

#### Obsolete Parameters

The following parameters are obsolete for the 11g version. Remove them from your configuration files:

- `MODE`

- `SERVER_PATH`

- `DRDA_OVERRIDE_FROM_CODEPAGE`

- `DRDA_OVERRIDE_TO_CODEPAGE`

- `ERROR_LOGGING`

- `ERROR_REPORTING`

- `ERRORTAG`

- `GATEWAY_SID`

- `GROUP_BY_OFF`

- `GTWDEBUG`

- `INCREMENT_CURSORS`

- `DRDA_CALLDESC_STMT`

- `DRDA_CALLDESC_PROC`

### Bind Gateway Package

When upgrading to 11g release you must rebind the gateway package if you have changed any of the following initialization parameters:

- `DRDA_DISABLE_CALL`

- `DRDA_ISOLATION_LEVEL`

- `DRDA_PACKAGE_COLLID`

- `DRDA_PACKAGE_CONSTOKEN`

- `DRDA_PACKAGE_NAME`

- `DRDA_PACKAGE_OWNER`

- `DRDA_PACKAGE_SECTIONS`

### Install or Upgrade Data Dictionary Views

For the correct functioning of the gateway, the data dictionary views must be installed on any DB2 system that will be accessed by the gateway. If you are upgrading the gateway, then you must replace the data dictionary views to the ones shipped with the latest gateway. The new views are required for the correct functioning of the latest version of the gateway. They contain necessary backward functionality to be compatible with the previous versions. Refer to [Configuring Oracle Database Gateway for DRDA](config-gateway-drda.md) for more information on creating data dictionary views.
