## Creating Required Operating System Groups and Users

If you are installing Oracle software for the first time, then create operating system groups and users to grant Oracle Database system privileges.

You can choose to create one administrative user and use one group for operating system authentication for all system privileges on the storage and database tiers. For example, you can designate the `oracle` user to be the Oracle Installation user for all Oracle software and use only the `ORA_DBA` group for authentication. You can also create custom configuration groups and users based on job role separation that divide access privileges.

Log in as an Administrator user, and use the following instructions to create the Oracle Installation user for Oracle Database.

**See Also:**

[Oracle Database Platform Guide for Microsoft Windows](../ntqrf/overview-of-ntfs-file-system-and-windows-registry-permissions.md)

- [About the Oracle Installation User](about-the-oracle-installation-user.md)
  To install Oracle Restart or Oracle Database software, you must use either a local or a domain user that is also a member of the Administrators group.
- [Creating Oracle Home User](creating-oracle-home-user.md)
  During Oracle Database installation, you can specify an optional Oracle home user associated with the Oracle home.
- [Understanding the Oracle Inventory Directory and the Oracle Inventory Group](understanding-oracle-inventory-directory.md)
  The Oracle Inventory directory is the central inventory location for all Oracle software installed on a server.
- [Operating System Groups Created During Oracle Database Installation](operating-system-groups-created-during-oracle-database-installation.md)
  During installation, the user groups listed in the following table are created, if they do not already exist.
- [Operating System Groups and Users for Job Role Separation](operating-system-groups-and-users-for-job-role-separation.md)
  A job role separation configuration of Oracle Database and Oracle ASM is a configuration with groups and users to provide separate groups for operating system authentication.

**Parent topic:** [Configuring Users, Groups and Environments for Oracle Database](configuring-users-groups-and-environments-for-oracle-database.md)
