## Multiple Oracle Home Directories on Windows

Install each Oracle product in its own Oracle home.

The value for `%ORACLE_BASE%` is stored in the registry (for example, in `HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\HOME0`). The values for `ORACLE_HOME` and `ORACLE_SID` are also stored in the registry. Symbolic links for these directories, like those used on UNIX platforms, are not supported on Windows platforms.

Oracle Universal Installer (OUI) records the values for environment variables such as `ORACLE_BASE`, `ORACLE_HOME`, and `ORACLE_SID` in the registry and also updates the value for the `PATH` environment variable for the user performing the installation. In Linux and UNIX systems, you must manually set these environment variables in the user session or user profile.

- [Changing the Current Setting for Oracle Home](changing-the-current-setting-for-oracle-home.md)
  Use Oracle Universal Installer (OUI) to change the current Oracle home.

**Related Topics**

- [Running Oracle Net Configuration Assistant Using Response Files](running-oracle-net-configuration-assistant-using-response-files.md)
- [Oracle Database Administrator’s Reference for Microsoft Windows](../ntqrf/about-configuration-arameters.md)

**Parent topic:** [Understanding the Oracle RAC Installed Configuration](understanding-the-oracle-rac-installed-configuration.md)
