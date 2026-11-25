## Overview of Oracle Linux Configuration with Oracle Database Preinstallation RPM

Use Oracle Database Preinstallation RPM to simplify operating system configuration, and to ensure that you have required kernel packages.

Oracle recommends that you install Oracle Linux and use Oracle Database Preinstallation RPM to configure your operating systems for Oracle Database and Oracle Grid Infrastructure installations.

Configure Oracle Database Preinstallation RPM only once on your operating system when you install Oracle Database or Oracle Grid Infrastructure for the first time on your system. For subsequent installations on the same system, do not install Oracle Database Preinstallation RPM again.

Do not install Oracle Database Preinstallation RPM on Oracle Engineered Systems, such as Oracle Exadata Database Machine. Oracle Engineered Systems include integrated system software that contain the required version of the operating system kernel and all software packages.

The Oracle Database Preinstallation RPM for your Oracle Linux distributions and database release automatically installs any additional packages needed for installing Oracle Grid Infrastructure and Oracle Database, and configures your server operating system automatically, including setting kernel parameters and other basic operating system requirements for installation. For more information about Oracle Linux and Oracle Database Preinstallation RPM, refer to:

<https://docs.oracle.com/en/operating-systems/oracle-linux/>

Configuring a server using Oracle Linux and the Oracle Database Preinstallation RPM consists of the following steps:

1.  Install Oracle Linux.

2.  Register your Linux distribution with Oracle Unbreakable Linux Network (ULN) or download and configure the yum repository for your system using the Oracle Linux yum server for your Oracle Linux release.

3.  Install the Oracle Database Preinstallation RPM with the RPM for your Oracle Grid Infrastructure and Oracle Database releases, and update your Linux release.

4.  Create role-allocated groups and users with identical names and ID numbers.

5.  Complete network interface configuration for each cluster node candidate.

6.  Complete system configuration for shared storage access as required for each standard or core node cluster candidate.

After these steps are complete, you can proceed to install Oracle Grid Infrastructure and Oracle Database.

**Parent topic:** [Automatically Configuring Oracle Linux with Oracle Database Preinstallation RPM](automatically-configuring-oracle-linux-with-oracle-preinstallation-rpm.md)
