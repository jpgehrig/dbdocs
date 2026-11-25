Oracle Net Services such as Oracle Listener, CMADMIN, and CMAN Proxy Listener run under the specified Oracle Home User account (Windows User Account) specified during the installation.

Oracle recommends that you specify the standard Windows User Account (not an Administrator) as the Oracle Home User. Oracle Universal Installer also has an option to create a new Windows User Account with limited privileges. When the Windows built-in account is used as the Oracle Home User, then Oracle Listener service runs under an high-privileged Local System Account (LSA) for database installation. For CMAN installation, if a Windows built-in account is used as the Oracle Home User, then CMADMIN and CMAN Proxy Listener runs under a low privileged LocalService Account.

**Note:**

The lsnrctl start command or CMAN proxy start command may prompt for password when relevant service does not exist. This happens for the first time for a given alias. Once the service is created, all subsequent start commands do not prompt for password. However, there is no prompt for password if you select Use Built-in Account as Oracle Home User.

**See Also:**

- [Oracle Database Net Services Administrator's Guide](../netag/enabling-advanced-features.md) for more information about User Accounts and Security

- [Oracle Database Net Services Reference](../netrf/listener-control-utility.md) for more information about START

**Parent topic:** [About Listener Requirements](about-listener-requirements.md)
