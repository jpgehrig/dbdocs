## Overview of Oracle Base Directories

The Oracle base directory is the location where Oracle software and configuration files are stored.

By default, Oracle Universal Installer (OUI) installs the Oracle Database software binary files by version and Oracle Home Name in a subdirectory of the Oracle base directory. An Oracle base directory can be used for multiple installations of software by a given installation owner. A separate Oracle base directory is created for each Oracle Home user you specify during installing of the Oracle Database software.

The Oracle Home User has complete control over the Oracle base directory. For reasons of security, different Windows User Accounts used as Oracle Home Users for different Oracle home directories are not allowed to share the same Oracle base directory. However, to support Oracle Database upgrade, Oracle supports the sharing of an Oracle base directory between a Built-in Account and a Windows User Account. If you choose to reuse an Oracle base directory from an earlier release of Oracle Database in Oracle Database 19c Release, then the Oracle Home User of the Oracle Database 19c Release has complete control over the Oracle base directory of the earlier release.

The default Oracle base path contains the Oracle Home User name if an Oracle Home User is specified during installation of the Oracle Database software. In a default Windows installation, the Oracle base directory appears as follows, where username is the Oracle Installation user if you choose Windows Built-in Account as the Oracle Home User, or it is the Oracle Home user if one is specified:

    DRIVE_LETTER:\app\username

If you have separate Oracle Home Users for the Oracle Grid Infrastructure installation and the Oracle RAC installation, then you have two Oracle base paths that are in accordance with Optimal Flexible Architecture (OFA) guidelines. For example, if the user `grid` is the Oracle Home User for the Oracle Grid infrastructure installation and the user `oracle` is the Oracle Home User for the Oracle Database installation, then you have two Oracle base directories. In the following examples, `X:` represents a mounted disk:

- `X:\app\grid`—This is the Oracle base for the Grid user (`grid` in this example), which is the Oracle Home User for the Oracle Grid Infrastructure installation.

- `X:\app\oracle`—This is the Oracle base for the Oracle user (`oracle` in this example), which is the Oracle Home User for the Oracle Database installation.

**Caution:**

After installing Oracle Database 12c Release 1 (12.1) (or later) release with a Windows User Account as Oracle Home User, do not install older versions of Oracle Databases that share the same Oracle Base Directory. During installation of the software for older releases, the ACLs are reset and Oracle Database 12c Release 1 (12.1) (or later) services may not be able to access the Oracle Base directory and files.

**Parent topic:** [Overview of Installation Directories for Oracle RAC](overview-of-installation-directories-for-oracle-rac.md)
