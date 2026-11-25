Oracle recommends that you configure Oracle Database files, directories, and registry settings to provide full control to authorized database administrators (DBAs).

If you have created a database using Oracle Database Configuration Assistant or upgraded a database using Oracle Database Upgrade Assistant, then no further action is required.

Learn about the permissions automatically set by Oracle Universal Installer, Oracle Database Configuration Assistant, and Oracle Database Upgrade Assistant and the steps to set these permissions manually.

In addition to the various groups listed in Oracle Database software installation creates the following groups for Oracle internal use and sets permissions on files and registry entries for these groups to ensure that the Oracle software functions properly. The group memberships and permissions set for the following groups must not be changed or removed:

- `ORA_INSTALL`

- `ORA_GRID_LISTENERS`

- `ORA_CLIENT_LISTENERS`

- `ORA_``HOMENAME``_SVCSIDS`

**See Also:**

- Your operating system documentation for more information about modifying NTFS file system and Windows registry settings

- [Oracle Database Installation Guide for Microsoft Windows](../ntdbi/operating-system-groups-created-during-oracle-database-installation.md)

<!-- -->

- [Setting File Permissions](about-setting-file-system-acls-manually.md)
  Oracle Universal Installer, Oracle Database Configuration Assistant, and Oracle Database Upgrade Assistant set file permissions when you install or upgrade Oracle Database software.
- [Setting Permissions for Windows Registry Entries](setting-permissions-for-windows-registry-entries.md)
  Oracle Universal Installer sets the permissions for Windows registry entries pertaining to Oracle Database software.
- [Setting Permissions for Windows Service Entries](setting-permissions-for-windows-service-entries.md)
  Oracle Universal Installer sets the following permissions to users and user groups for Windows service entries for Oracle Database services.
- [Setting NTFS File System Security](setting-ntfs-file-system-security.md)
  Use this procedure to set the NTFS file system security.
- [Setting Windows Registry Security](setting-windows-registry.md)
  Oracle recommends that you remove write permissions from users who are not Oracle Database DBAs or system administrators in the `HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE` directory of the Windows registry.

**Parent topic:** [Postinstallation Configuration Tasks on Windows](postinstallation-configuration-tasks-on-windows.md)
