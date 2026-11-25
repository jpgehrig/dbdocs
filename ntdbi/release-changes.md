## Changes in this Release for Oracle Database Installation Guide

Changes in Oracle Database Installation Guide for Oracle Database 19c.

- Changes in Oracle Database 19c
  New features, deprecated features, and desupported features in this release.

### Changes in Oracle Database 19c

New features, deprecated features, and desupported features in this release.

The following are changes in Oracle Database Installation Guide for Oracle Database 19c:

- New Features
  Review new features available with Oracle Database installation in Oracle Database 19c.
- Deprecated Features
  Review features that are deprecated starting with Oracle Database 19c.
- Desupported Features for Oracle Database 19c
  There are no desupported features at the time of release.

**Parent topic:** Changes in this Release for Oracle Database Installation Guide

#### New Features

Review new features available with Oracle Database installation in Oracle Database 19c.

- Simplified Image Based Oracle Database Client Installation

**Parent topic:** Changes in Oracle Database 19c

##### Simplified Image Based Oracle Database Client Installation

Starting with Oracle Database 19c, the Oracle Database Client software is available as an image file for download and installation. You must extract the image software into a directory where you want your Oracle home to be located, and then run the `runInstaller` script to start the Oracle Database Client installation. Oracle Database Client installation binaries continue to be available in the traditional format as non-image zip files.

As with Oracle Database and Oracle Grid Infrastructure image file installations, Oracle Database Client image installations simplify Oracle Database Client installations and ensure best practice deployments.

**Parent topic:** New Features

#### Deprecated Features

Review features that are deprecated starting with Oracle Database 19c.

The following feature is deprecated in this release, and may be desupported in another release. For more information about deprecated and desupported features, parameters and views, refer to Oracle Database Upgrade Guide.

- Deprecation of clone.pl

  The `clone.pl` script is deprecated in Oracle Database 19c. The functionality of performing a software-only installation, using the gold image, is available in the installer wizard.

  The `clone.pl` script can be removed in a future release. Instead of using the `clone.pl` script, Oracle recommends that you install the extracted gold image as a home, using the installer wizard.

**Related Topics**

- [Oracle Database Upgrade Guide](../upgrd/oracle-database-changes-deprecations-desupports.md)

**Parent topic:** Changes in Oracle Database 19c

#### Desupported Features for Oracle Database 19c

There are no desupported features at the time of release.

**Parent topic:** Changes in Oracle Database 19c
