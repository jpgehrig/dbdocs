## Changes in this Release for Oracle Database

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

- Oracle Memory Speed Support for PMEM Devices
- Root Scripts Automation Support for Oracle Database Installation
- Simplified Image-Based Oracle Database Client Installation

**Parent topic:** Changes in this Release for Oracle Database

#### Oracle Memory Speed Support for PMEM Devices

Oracle recommends that you use Oracle Database with the Oracle Memory Speed (OMS) file system to fully utilize the potential of persistent memory (PMEM) devices safely in data centers.

With PMEM as the backing device, OMS utilizes a memory-mapped file hosted on an XFS-based, DAX-enabled file system to perform I/O operations. You must export the PMEM device as a file using a DAX-enabled file system, such as XFS.

**Related Topics**

- [Deploying the Oracle Memory Speed File System](deploying_oms.md)

**Parent topic:** New Features

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

- Deprecation of Oracle ACFS on IBM AIX

  The ACFS storage option on IBM AIX is deprecated in Oracle Database 19c.

  To align the support for the IBM AIX platform, Oracle Automatic Storage Management Cluster File System (ACFS) on IBM AIX (called Oracle Advanced Cluster File System starting with Oracle Database 21c) is deprecated in Oracle Database 19c. For data or files currently stored on an ACFS file system that cannot be stored in the Oracle database, the IBM General Parallel File System (GPFS) can be used.

**Related Topics**

- [Oracle Database Upgrade Guide](../upgrd/oracle-database-changes-deprecations-desupports.md)

**Parent topic:** Changes in this Release for Oracle Database

### Other Changes

Review other changes for Oracle Database 19c.

- Rapid Home Provisioning Name Change

  Starting with Oracle Database 19c and Oracle Grid Infrastructure 19c, Rapid Home Provisioning is renamed to Fleet Patching and Provisioning (FPP).

- Operating System Package Names

  To simplify the installation of operating system packages required for an Oracle Database and Oracle Grid Infrastructure installation on Linux, starting with 19c, only the operating system package names will be listed and not the exact package version. Install or update to the latest version of these packages from the minimum supported Linux distribution.Only packages that are officially released by Oracle or your operating system vendor are supported.

**Parent topic:** Changes in this Release for Oracle Database
