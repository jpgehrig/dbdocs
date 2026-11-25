## Creating Oracle Home User

During Oracle Database Client installation, you can specify an optional Oracle Home User associated with the Oracle home.

For example, assume that you use an Administrator user named `OraSys` to install the software (Oracle Installation user), then you can specify the `ORADOMAIN\OraDb` domain user as the Oracle Home User for this installation. The specified Oracle home domain user must exist before you install the Oracle Database Client software.

The Oracle Home User can be either the Windows Built-in Account (LocalService) or a Windows User Account. This account is used for running the Windows services for the Oracle home. Do not log in using this account to perform administrative tasks.

Windows User Account can be a Windows Local User, Windows Domain User, Managed Services Account (MSA), or Group Managed Services Account (gMSA). Starting with Oracle Database 19c, Group Managed Services Account (gMSA) is introduced as an additional option.

Using Windows built-in account, MSA, or gMSA enables you to install Oracle Database Client, and create and manage Database services without passwords.

If you specify an existing user as the Oracle Home User, then the Windows User Account you specify can either be a Windows Domain User or a Windows Local User. If you specify a non-existing user as the Oracle Home User, then the Windows User Account you specify must be a Windows Local User. The new user is then created during installation and the created user is denied interactive logon privileges to the Windows computer. However, a Windows administrator can manage this account like any other Windows account.

For enhanced security, Oracle recommends that you use the standard Windows User Account or Windows Built-in Account (LocalService), which is not an administrator account, to install Oracle Database Client.

**Note:**

You cannot change the Oracle Home User after the installation is complete. If you must change the Oracle Home User, then you must reinstall the Oracle Database Client software.

When you specify an Oracle Home User, the installer configures that user as the Oracle Service user for all software services that run from the Oracle home. The Oracle Service user is the operating system user that the Oracle software services run as, or the user from which the services inherit privileges.

Silent installation is enhanced to support password prompt for the Oracle Home User. So, customers and independent software vendors (ISV) can use response files without hard coding the password into the source code.

**Parent topic:** [Oracle Database Client Preinstallation Tasks](oracle-database-client-preinstallation-tasks.md)
