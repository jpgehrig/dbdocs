## Creating Oracle Home User

During Oracle Database installation, you can specify an optional Oracle home user associated with the Oracle home.

For example, assume that you use an Administrator user named `OraSys` to install the software (Oracle Installation user), then you can specify the `ORADOMAIN\OraDb` domain user as the Oracle home user for this installation. The specified Oracle home domain user must exist before you install the Oracle Database software.

Oracle home user can be a Windows Built-in Account (LocalSystem for Server and LocalService for Client), Virtual Account, or a regular (not an administrator) Windows account. If you specify an existing user as the Oracle home user, then the Windows User Account you specify can either be a Windows Domain User or a Windows Local User.

A Windows User Account need not be created by the Administrator if a Virtual Account or a Windows Built-in Account is used during installation.

If you specify a non-existing user as the Oracle home user, then the Windows User Account you specify must be a Windows Local User. The installer creates this account automatically to run the Windows services for the Oracle home. Do not log in using this account to perform administrative tasks.

The Group Managed Services Account (gMSA) and Virtual Accounts enables you to install Oracle Database, create, and manage Database services without passwords. The gMSA is a domain level account that can be used by multiple servers in a domain to run the services using this account. Windows User Account can be a Windows Local User, Windows Domain User, Managed Services Account (MSA), or Group Managed Services Account (gMSA).

If you want to create a new user during installation, then it can only be a Windows Local User. It cannot be a Windows Domain User, an MSA, or a gMSA. The new user that is created is denied interactive logon privileges to the Windows computer. However, a Windows administrator can manage this account like any other Windows account. Oracle recommends that you use Virtual Account or a standard Windows User Account (instead of Windows Built-in Account) as the Oracle Home User for enhanced security.

**Note:**

You cannot change the Oracle Home User after the installation is complete. If you must change the Oracle Home User, then you must reinstall the Oracle Database software.

When you specify an Oracle Home user, the installer configures that user as the Oracle Service user for all software services that run from the Oracle home. The Oracle Service user is the operating system user that the Oracle software services run as, or the user from which the services inherit privileges.

Silent installation is enhanced to support password prompt for the Oracle home user. So, customers and independent software vendors (ISV) can use response files without hard coding the password into the source code.

Oracle recommends using Virtual Account or a standard Windows User Account (not an Administrator account) as the Oracle Home User for typical installation, software-only installation, and cloning.

If an existing Windows User Account is used as the Oracle home user for software-only installation, then a password is not required. Thus, you can perform a silent, software-only installation using Windows User Account.

If you use a Windows User Account as the Oracle home user for cloning individual Oracle Database installations, then a password is not required.

Virtual Account is the Oracle home user for Oracle Database Single Instance database installation. The account enables you to install Oracle Database, create, and manage Database services without passwords. The gMSA is a domain level account that can be used by multiple servers in a domain to run the services using this account. The gMSA is a low privilege user account.

**Parent topic:** [Creating Required Operating System Groups and Users](creating-required-operating-system-groups-and-users.md)
