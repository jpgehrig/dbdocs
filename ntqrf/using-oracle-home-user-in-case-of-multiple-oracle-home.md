Different Oracle homes on a system can use the same Oracle Home User or use different Oracle Home User names. Note that the earlier releases (11.2 and earlier) of Oracle Database are treated equivalent to using the Windows Built-in Account as the Oracle Home User.

As the Oracle Home User has complete control over the Oracle base directory for an Oracle home, multiple Oracle homes are allowed to share the same Oracle base only when they use the same Oracle Home User. This is done for security reasons.

However, as an exception, Oracle supports the sharing of an Oracle base directory between a Windows built-in account (server) and a specific Windows User Account, and Windows built-in account (server) and Virtual Account. This enables easier upgrade of Oracle home from the older releases of Oracle Database to Oracle Database 19c as the same Oracle base can be shared, and all the files under the Oracle base can be accessed by the Oracle Home User.

**Note:**

- When you share an Oracle base between 11g Release 2 (or earlier), 12c Release 2, and Oracle Database 19c, Windows User Account (used as Oracle Home User) is granted full control of the Oracle base and its subdirectories. This means that the Windows User Account for Oracle home can access or update any database files for the earlier release.

- After installing Oracle Database 12c Release 1 (or later) with a Windows User Account or Virtual Account as the Oracle Home User, do not install older versions of Oracle Database and share the same Oracle base directory. During the installation of older releases, ACLs are reset corresponding to the older releases and Oracle Database 12c Release 2 (or later) services may not be able to access the Oracle base directory and files.

On the contrary, if you decide to use a different Oracle base for Oracle Database 19c, there may be some issues in terms of Oracle services accessing the files from the older Oracle base.

**See Also:**

- [Oracle Database Installation Guide for Microsoft Windows](../ntdbi/creating-oracle-home-user.md)

**Related Topics**

- [Setting File Permissions](about-setting-file-system-acls-manually.md)

**Parent topic:** [Supporting Oracle Home User on Windows](supporting-oracle-home-user-on-windows.md)
