Log in as `root`, and use the following instructions to locate or create the Oracle Inventory group, and create a software owner for Oracle Grid Infrastructure, and directories for Oracle home.

Oracle software installations require an installation owner, an Oracle Inventory group, which is the primary group of all Oracle installation owners, and at least one group designated as a system privileges group. Review group and user options with your system administrator. If you have system administration privileges, then review the topics in this section and configure operating system groups and users as needed.

- [Determining If an Oracle Inventory and Oracle Inventory Group Exist](determining-if-an-oracle-inventory-and-oracle-inventory-group-exist.md)
  Determine if you have an existing Oracle central inventory, and ensure that you use the same Oracle Inventory for all Oracle software installations. Also, ensure that all Oracle software users you intend to use for installation have permissions to write to this directory.
- [Creating the Oracle Inventory Group If an Oracle Inventory Does Not Exist](creating-the-oracle-inventory-group-if-an-oracle-inventory-does-not-exist.md)
  Create an Oracle Inventory group manually as part of a planned installation, particularly where more than one Oracle software product is installed on servers.
- [About Oracle Installation Owner Accounts](about-oracle-installation-owner-accounts.md)
  Select or create an Oracle installation owner for your installation, depending on the group and user management plan you want to use for your installations.
- [Restrictions for Oracle Software Installation Owners](restrictions-for-oracle-software-installation-owners.md)
  Review the following restrictions for users created to own Oracle software.
- [Identifying an Oracle Software Owner User Account](identifying-an-oracle-software-owner-user-account.md)
  You must create at least one software owner user account the first time you install Oracle software on the system. Either use an existing Oracle software user account, or create an Oracle software owner user account for your installation.
- [About the Oracle Base Directory for the grid User](about-the-oracle-base-directory-for-the-grid-user.md)
  Review this information about creating the Oracle base directory on each cluster node.
- [About the Oracle Home Directory for Oracle Grid Infrastructure Software](about-the-oracle-home-directory-for-oracle-grid-infrastrucrure.md)
  Review this information about creating the Oracle home directory location on each cluster node.
- [About Creating the Oracle Home and Oracle Base Directory](about-creating-oracle-base-oracle-home-directories.md)
  Create Grid home and Oracle base home directories on each cluster node.

**Parent topic:** [Configuring Users, Groups and Environments for Oracle Grid Infrastructure and Oracle Database](configuring-users-groups-and-environments-for-oracle-grid-infrastructure-and-oracle-database.md)
