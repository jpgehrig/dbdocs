These topics contain last-minute features and changes for Microsoft Windows for Oracle Database 19c.

- Unsupported Products for Microsoft Windows
  There are no unsupported Microsoft Windows-specific products at this time.
- Product Support
  These are the supported products or features for Oracle Database 19c.
- Linking Applications with Oracle Client Libraries for Microsoft Windows
  You must use the dynamic Oracle client libraries to link the client code on Microsoft Windows. 
- Preinstallation Requirements for Microsoft Windows
  Refer to the installation guides for the preinstallation requirements for Oracle Database 19c.
- Installation, Configuration, and Upgrade Issues for Microsoft Windows
  These topics describe information about issues that affect Oracle Database installation, configuration, and upgrade.

### Unsupported Products for Microsoft Windows

There are no unsupported Microsoft Windows-specific products at this time.

**Parent topic:** Issues Affecting Microsoft Windows for Oracle Database 19c

### Product Support

These are the supported products or features for Oracle Database 19c.

Oracle ACFS and Oracle ADVM Support

Although Oracle ADVM supports raw disks in Oracle Automatic Storage Management disk groups, Oracle ADVM device special files created through raw are not supported; Oracle ADVM only supports block device special files.

For the latest information about supported platforms and releases, see the Note 1369107.1 on My Oracle Support at [https://support.oracle.com](https://support.oracle.com/)

Oracle Fail Safe Server Release 4.2.1 Support

Oracle Fail Safe Server, Release 4.2.1 is supported on the software listed in the following table:

| Software                                           | Release or Version                                                                                                                                                 |
|:---------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Oracle Database (Standard and Enterprise editions) | Oracle Database 11g Release 2 (11.2)<br>Oracle Database 12c Release 1 (12.1)<br>Oracle Database 12c Release 2 (12.2)<br>Oracle Database 18c<br>Oracle Database 19c |
| Microsoft Windows Platforms                        | Microsoft Windows Server 2012<br>Microsoft Windows Server 2012 R2<br>Microsoft Windows Server 2016<br>Microsoft Windows Server 2019                                |

Oracle Fail Safe Client Release 4.2.1 Support

Oracle Fail Safe Manager, the client, works with Oracle Fail Safe Server version 3.4.2.4 and later patch sets. Oracle Fail Safe Manager is supported on the following operating systems:

- Microsoft Windows Server 2012
- Microsoft Windows Server 2012 R2
- Microsoft Windows Server 2016
- Microsoft Windows Server 2019
- Windows 7
- Windows 8
- Windows 8.1
- Windows 10

For the latest certification information for Oracle Fail Safe, see the Certifications tab in My Oracle Support at [https://support.oracle.com](https://support.oracle.com/)

**Parent topic:** Issues Affecting Microsoft Windows for Oracle Database 19c

### Linking Applications with Oracle Client Libraries for Microsoft Windows

You must use the dynamic Oracle client libraries to link the client code on Microsoft Windows. 

Do not link the static Oracle client libraries.

**Parent topic:** Issues Affecting Microsoft Windows for Oracle Database 19c

### Preinstallation Requirements for Microsoft Windows

Refer to the installation guides for the preinstallation requirements for Oracle Database 19c.

**Parent topic:** Issues Affecting Microsoft Windows for Oracle Database 19c

### Installation, Configuration, and Upgrade Issues for Microsoft Windows

These topics describe information about issues that affect Oracle Database installation, configuration, and upgrade.

- Bug 20918120
- Bug 21325903
- Bug 29426320

**Parent topic:** Issues Affecting Microsoft Windows for Oracle Database 19c

#### Bug 20918120

Installing Oracle Real Application Clusters Database home with a Group Managed Services Account (gMSA) as the Oracle home user, fails with the following error if the gMSA name consists of more than 15 characters (including the domain name):

`[INS-32101] Specified Oracle Home user does not exist`

Workaround:

Use a gMSA name (including the domain name) that consists of less than 15 characters.

**Parent topic:** Installation, Configuration, and Upgrade Issues for Microsoft Windows

#### Bug 21325903

The deinstallation operation fails to remove Oracle home and displays `file in use` errors because the services and processes running from Oracle home are not removed completely before Oracle home removal.

Workaround:

Manually remove the Oracle home.

**Parent topic:** Installation, Configuration, and Upgrade Issues for Microsoft Windows

#### Bug 29426320

The following error occurs when running external procedures or Oracle Database Extensions for .NET procedures with a virtual user account:

    ORA-28575 Unable to open RPC connection to external procedure agent

Workaround#1

Restart the Oracle listener service and the OracleClrAgent service using a non-virtual user account.

Workaround#2

Reinstall Oracle Database 19c and select a non-virtual user account.

Workaround#3

If you require a virtual user account, then set `sqlnet.authentication_services` to `NONE` in `SQLNET.ORA`.

**Parent topic:** Installation, Configuration, and Upgrade Issues for Microsoft Windows
