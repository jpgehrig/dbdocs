Complete configuration tasks after you install Oracle Database.

You are required to complete some configuration tasks after Oracle Database is installed. In addition, Oracle recommends that you complete additional tasks immediately after installation. You must also complete product-specific configuration tasks before you use those products.

**Note:**

This chapter describes basic configuration only. Refer to product-specific administration and tuning guides for more detailed configuration and tuning information.

- [Required Postinstallation Tasks](required-postinstallation-tasks.md)
  Download and apply required patches for your software release after completing your initial installation.
- [Recommended Postinstallation Tasks](recommended-postinstallation-tasks.md)
  Oracle recommends that you complete these tasks after installation.
- [About Changes in Default SGA Permissions for Oracle Database](change-in-default-sga-permissions-for-oracle-database.md)
  Starting with Oracle Database 12c Release 2 (12.2.0.1), by default, permissions to read and write to the System Global Area (SGA) are limited to the Oracle software installation owner.
- [Checking Installed Oracle Database Contents and Directory Location](checking-installed-oracle-database-contents-and-directory-location.md)
  Use these steps to check the contents and directory location of an Oracle Database installation:
- [Enabling and Disabling Oracle Database Options After Installation](enabling-and-disabling-oracle-database-options-after-installation.md)
  The `chopt` tool changes your database options after installation.
- [Starting Oracle Enterprise Manager Database Express](starting-enterprise-manager-database-express.md)
  Use these steps to log in to Oracle Enterprise Manager Database Express (EM Express).
- [Creating a Fast Recovery Area](creating-a-fast-recovery-area.md)
  During an Oracle Restart installation, you can create only one disk group. During an Oracle Clusterware installation, you can create multiple disk groups. If you plan to add an Oracle Database for a standalone server or an Oracle RAC database, then you should create the fast recovery area for database files.
- [Cloning an Oracle Database Home](cloning-an-oracle-home.md)
  Cloning an Oracle home involves creating a copy of the Oracle home and then configuring it for a new environment.
