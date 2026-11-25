The following topics describe how to migrate to new instances of Oracle Database Gateway for DRDA from an existing installation. Perform the following steps to migrate to a new release of Oracle Database Gateway for DRDA from an existing release:

1.  Install the New Release

2.  Gateway Initialization Parameter File

3.  Bind Gateway Package

4.  Install or Upgrade Data Dictionary Views

### 16.1 Install the New Release

Install the new release of the gateway in a separate directory, as discussed [Installing Oracle Database Gateway for DRDA](install-drda-gateway.md).

**Note:**

Do not install the gateway over a previously existing gateway installation. This corrupts the existing installation.

### 16.2 Gateway Initialization Parameter File

This release of Database Gateway for DRDA has a completely new architecture. Most of the prior parameters are obsolete. You should not use the old initialization file as a base and try to modify it. Instead, you should use the new initialization generated as part of installation as a base. Refer to [Initialization Parameters](initialization-parameters-for-gateways.md) for the syntax of the parameters.

Existing TG4DB2 customer migrating to this release of Database Gateway for DRDA would need to provide the recovery user's password `HS_FDS_RECOVERY_PWD`, with this release of gateway.

### 16.3 Bind Gateway Package

The binding of the package is automatic. Refer to [Configuring the DRDA Server](config-drda-server.md).

### 16.4 Install or Upgrade Data Dictionary Views

For the correct functioning of the gateway, the data dictionary views must be installed on any DB2 system that will be accessed by the gateway. If you are upgrading the gateway, then you must replace the data dictionary views to the ones shipped with the latest gateway. The new views are required for the correct functioning of the latest version of the gateway. They contain necessary backward functionality to be compatible with the previous versions. Refer to [Configuring Oracle Database Gateway for DRDA](config-drda-gateway.md) for more information on creating data dictionary views.
