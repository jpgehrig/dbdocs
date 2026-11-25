For a single-instance Oracle Database and Oracle Database Client installations, you can use Built-in Account or a Windows User Account as the Oracle Home User. Single-instance Oracle Database installations may also use a Virtual Account.

Virtual Accounts allow you to install Oracle Database, create, and manage database services without passwords. Windows User Account can be an existing Windows Local User, Windows Domain User, Managed Services Account (MSA), or Group Managed Services Account (gMSA). For a Windows Local User Account or a Windows Domain User Account, you must provide both the user name and password during installation. For a Managed Services Account, you must provide the user name only.

The Group Managed Services Account (gMSA) enables you to install an Oracle Database and, create and manage Database services without passwords. The gMSA is a domain level account that can be used by multiple servers in a domain to run the services using this account.

For a Windows Local User, you also have the option of creating a new Windows user during installation. You must provide the user name and password for the user account and Oracle Universal Installer creates the Windows user during installation. The newly created Windows account is denied interactive logon privileges to the Windows computer. However, a Windows administrator can still manage this account like any other Windows account.

**Note:**

If a Windows Local User Account is chosen as the Oracle Home User during single-instance Oracle Database installation, Windows NT Native Authentication (NTS) cannot be used for authenticating Windows domain users or users from remote computers.

The Virtual Account option enables you to install an Oracle Database and, create and manage Database services without passwords. User names do not appear on the logon screen.

When the Windows built-in account is chosen as the Oracle Home User, Oracle services for a server home are run using the built-in privileged LocalSystem account. Hence for single-instance Oracle Database installations, Oracle recommends that you use Virtual Account or a standard Windows User Account instead of a Windows built-in account as the Oracle Home User for enhanced security. For Oracle Database Client installations, it is not necessary to use a Windows User Account as Oracle Home User for reasons of security. Even when the Windows built-in account is chosen as the Oracle Home User, Oracle services for a client home are run using the built-in low-privileged LocalService account.

**See Also:**

- [Oracle Grid Infrastructure Installation and Upgrade Guide for Microsoft Windows x64 (64-Bit)](../cwwin/index.md)

- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/adding-and-deleting-oracle-rac-from-nodes-on-windows-systems.md)

- [Oracle Grid Infrastructure Installation Guide for Microsoft Windows x64 (64-Bit)](../cwwin/index.md)

**Parent topic:** [Supporting Oracle Home User on Windows](supporting-oracle-home-user-on-windows.md)
