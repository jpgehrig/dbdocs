## Oracle Base Directory

If you install Oracle Database 19c on a computer with no other Oracle software installed, Oracle Universal Installer creates an Oracle base directory for you.

If Oracle software is installed, then one or more Oracle base directories exist. In the latter case, Oracle Universal Installer offers you a choice of Oracle base directories to install Oracle Database.

The Oracle Home User has complete control over the Oracle base for a particular home. For security reasons, different Windows User Accounts used as Oracle Home Users for different Oracle homes are not allowed to share the same Oracle base. However, to support Oracle Database upgrade, Oracle supports the sharing of an Oracle base between a Windows Built-in Account and a Windows User Account. This means that if you choose to reuse an Oracle base from an earlier release of Oracle Database in Oracle Database 19c, then the Oracle Home User of Oracle Database 19c Oracle home has complete control over the Oracle base of the earlier release.

**See Also:**

[Oracle Database Platform Guide for Microsoft Windows](../ntqrf/managing-oracle-home-user.md)

In a default Windows installation, the Oracle base directory appears as follows:

    DRIVE_LETTER:\app\username

where `username` is the Oracle Installation User if you choose Windows Built-in Account, else it is the Oracle Home User (standard Windows User Account).

**Caution:**

After installing Oracle Database 19c with a Windows User Account used as the Oracle Home User, do not install older version of databases and share the same Oracle base directory. During the installation of older releases of Oracle Database, ACLs are reset corresponding to older releases. Thus Oracle Database 19c services may not be able to access the Oracle base directory and the files in it.

**Note:**

You can choose to create an Oracle base directory, even if the other Oracle base directories exist on the system.

**Parent topic:** [Installation Considerations](installation-considerations.md)
