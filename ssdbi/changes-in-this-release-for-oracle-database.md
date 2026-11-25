Learn about the new features and changes in Oracle Database Installation Guide for Oracle Database 19c.

- New Features
  Review new features available with Oracle Database installation in Oracle Database 19c.
- Deprecated Features
  Review features that are deprecated starting with Oracle Database 19c.
- Other Changes
  Review other changes for Oracle Database 19c.

**Related Topics**

- [Oracle Database New Features Guide](../newft/index.md)

### New Features

Review new features available with Oracle Database installation in Oracle Database 19c.

- Root Scripts Automation Support for Oracle Database Installation
- Simplified Image-Based Oracle Database Client Installation

**Parent topic:** Changes in this Release for Oracle Database

#### Root Scripts Automation Support for Oracle Database Installation

Starting with Oracle Database 19c, the database installer, or setup wizard, provides options to set up permissions to run the root configuration scripts automatically, as required, during a database installation. You continue to have the option to run the root configuration scripts manually.

Setting up permissions for root configuration scripts to run without user intervention can simplify database installation and help avoid inadvertent permission errors.

**Related Topics**

- [Running Oracle Database Setup Wizard to Install Oracle Database](running-oracle-universal-installer-to-install-oracle-database.md)

**Parent topic:** New Features

#### Simplified Image-Based Oracle Database Client Installation

Starting with Oracle Database 19c, the Oracle Database client software is available as an image file for download and installation. You must extract the image software into a directory where you want your Oracle home to be located, and then run the `runInstaller` script to start the Oracle Database client installation. Oracle Database client installation binaries continue to be available in the traditional format as non-image zip files.

As with Oracle Database and Oracle Grid Infrastructure image file installations, Oracle Database client image installations simplify Oracle Database client installations and ensure best practice deployments.

**Related Topics**

- [Installing Oracle Database Client Using Image File](../lacli/installing-database-client-using-image-files.md)

**Parent topic:** New Features

### Deprecated Features

Review features that are deprecated starting with Oracle Database 19c.

The following feature is deprecated in this release, and may be desupported in another release. For more information about deprecated and desupported features, parameters and views, refer to Oracle Database Upgrade Guide.

- Deprecation of clone.pl

  The `clone.pl` script is deprecated in Oracle Database 19c. The functionality of performing a software-only installation, using the gold image, is available in the installer wizard.

  The `clone.pl` script can be removed in a future release. Instead of using the `clone.pl` script, Oracle recommends that you install the extracted gold image as a home, using the installer wizard.

- Deprecation of the SERVICE_NAMES parameter

  The use of the `SERVICE_NAMES` parameter is no longer actively supported. It must not be used for high availability (HA) deployments. It is not supported to use service names parameter for any HA operations. This restriction includes FAN, load balancing, `FAILOVER_TYPE`, `FAILOVER_RESTORE`, `SESSION_STATE_CONSISTENCY`, and any other uses.

**Related Topics**

- [Oracle Database Upgrade Guide](../upgrd/oracle-database-changes-deprecations-desupports.md)

**Parent topic:** Changes in this Release for Oracle Database

### Other Changes

Review other changes for Oracle Database 19c.

- Rapid Home Provisioning Name Change

  Starting with Oracle Database 19c and Oracle Grid Infrastructure 19c, Rapid Home Provisioning is renamed to Fleet Patching and Provisioning (FPP).

**Parent topic:** Changes in this Release for Oracle Database
