Understand the software owner user environments to configure before installing Oracle Grid Infrastructure.

You run the installer software with the Oracle Grid Infrastructure installation owner user account (`oracle` or `grid`). However, before you start the installer, you must configure the environment of the installation owner user account. If needed, you must also create other required Oracle software owners.

- [Environment Requirements for Oracle Software Owners](environment-requirements-for-oracle-software-owners.md)
  You must make the following changes to configure Oracle software owner environments:
- [Procedure for Configuring Oracle Software Owner Environments](procedure-for-configuring-oracle-software-owner-environments.md)
  Configure each Oracle installation owner user account environment:
- [Checking Resource Limits for Oracle Software Installation Users](checking-resource-limits-for-oracle-software-installation-users.md)
  For each installation software owner user account, check the resource limits for installation.
- [Setting Remote Display and X11 Forwarding Configuration](setting-remote-display-and-x11-forwarding-configuration.md)
  If you are on a remote terminal, and the local system has only one visual (which is typical), then use the following syntax to set your user account `DISPLAY` environment variable:
- [Preventing Installation Errors Caused by Terminal Output Commands](preventing-installation-errors-caused-by-terminal-output-commands.md)
  During an Oracle Grid Infrastructure installation, OUI uses SSH to run commands and copy files to the other nodes. During the installation, hidden files on the system (for example, `.bashrc` or `.cshrc`) can cause `makefile` and other installation errors if they contain terminal output commands.

**Parent topic:** [Configuring Users, Groups and Environments for Oracle Grid Infrastructure and Oracle Database](configuring-users-groups-and-environments-for-oracle-grid-infrastructure-and-oracle-database.md)
