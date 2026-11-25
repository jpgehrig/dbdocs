## 8 Oracle Database Postinstallation Tasks

Complete configuration tasks after you install Oracle Database.

Oracle recommends that you complete additional tasks immediately after installation. You must also complete product-specific configuration tasks before you use those products.

- [Downloading Release Update Patches](downloading-and-installing-patch-updates.md)
  Download and install Release Updates (RU) and Release Update Revisions (RUR) patches for your Oracle software after you complete installation.
- [Requirements for Database Password](requirements-for-database-password.md)
  To secure your database, every password must satisfy the Oracle recommended password requirements, even the passwords for predefined user accounts.
- [About Installing Oracle Autonomous Health Framework](downloading-installing-the-orachk-health-check-tool.md)
  Install the latest version of Oracle Autonomous Health Framework to perform proactive heath checks and collect diagnostics data for the Oracle software stack.
- [Recompiling Invalid Objects on Windows Systems](recompiling-invalid-objects-on-windows-systems.md)
  Run the `utlrp.sql` script after you install, patch, or upgrade a database, to identify, and recompile invalid objects.
- [Configuring the Secure Sockets Layer](configuring-the-secure-sockets-layer.md)
  Oracle highly recommends that you configure and use a Secure Sockets Layer (SSL) to ensure that passwords and other sensitive data are not transmitted in clear text in HTTP requests.
- [Configuring Oracle Components](configuring-oracle-components.md)
  Many Oracle products and options must be configured before you use them for the first time.
- [Creating a Fast Recovery Area Disk Group](creating-a-fast-recovery-area-disk-group.md)
  During installation, by default you can create multiple disk groups.
- [Enabling and Disabling Database Options After Installation](enabling-and-disabling-database-options-after-installation.md)
  When you install Oracle Database, some options are enabled and the others disabled. You can view the enabled Oracle Database options by querying the `V$OPTION` view using SQL\*Plus.
- [Changing the Oracle Home User Password](changing-the-oracle-home-user-password.md)
  Oracle Home User Control is a command-line utility that allows an administrator to update the password for an Oracle Home User.
