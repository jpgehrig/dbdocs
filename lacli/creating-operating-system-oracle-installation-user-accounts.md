## Creating Operating System Oracle Installation User Accounts

Before starting installation, create Oracle software owner user accounts, and configure their environments.

Oracle software owner user accounts require resource settings and other environment configuration. To protect against accidents, Oracle recommends that you create one software installation owner account for each Oracle software program you install.

- [Creating an Oracle Software Owner User](creating-an-oracle-software-owner-user.md)
  If the Oracle software owner user (`oracle` ) does not exist, or if you require a new Oracle software owner user, then create it as described in this section.
- [Environment Requirements for Oracle Software Owners](environment-requirements-for-oracle-software-owners.md)
  You must make the following changes to configure Oracle software owner environments:
- [Procedure for Configuring Oracle Software Owner Environments](procedure-for-configuring-oracle-software-owner-environments.md)
  Configure each Oracle installation owner user account environment:
- [Setting Remote Display and X11 Forwarding Configuration](setting-remote-display-and-x11-forwarding-configuration.md)
  If you are on a remote terminal, and the local system has only one visual (which is typical), then use the following syntax to set your user account `DISPLAY` environment variable:

**Parent topic:** [Configuring Users, Groups and Environments for Oracle Database Client](configuring-users-groups-and-environments-for-oracle-database-client.md)
