## AutoUpgrade and Microsoft Windows ACLs and CLIs

When running AutoUpgrade on Microsoft Windows systems, Oracle recommends additional best practices with access control lists (ACLs) and command-line interfaces (CLIs).

### AutoUpgrade and Access Control Lists (ACLs)

When you use AutoUpgrade on Windows systems, there are difficulties in setting up automated tools to work with Windows access control lists. Oracle strongly recommends that you complete the following best practice procedures:

- Review permissions for each of your target databases, and how these permissions relate to directories for these databases, such as the Oracle base directory, and the `oraInventory` files.

- Refer to the Oracle Database Administrator's Reference section on postinstallation configuration tasks for NTFS file systems.

- Review Microsoft's documentation regarding Windows PowerShell.

- Review the permissions for the groups `ORA_DBA`, `ORA_HOME_USERS`, and `ORA_ASM` groups. The `ORA_DBA` group only provides `SYSDBA` privileges to Oracle Database. The Oracle ASM management privileges are controlled by members of the group `ASM DISKGROUPS`.

- The `ORA_DBA` group member permissions to perform many administration tasks is limited, compared to the privileges available on `POSIX` systems. To enable AutoUpgrade to run as expected, Oracle recommends that the user account with Administrator rights on the Microsoft Windows server also manages Oracle base directory elements such as traces, listeners, and configuration.

- AutoUpgrade must be run using a command console (`CMD`) with administrative rights, and that console should be opened as the Oracle Installation User, or a user with similar privileges.

- Refer to My Oracle Support notes 1529702.1, and 1595375.1.

AutoUpgrade uses the following procedure with services running on the database:

- AutoUpgrade stops the services on the source database, and creates a temporary service on the target database Oracle home.

  If a restore is required, then the service in the target is dropped, and the service in the source is restarted.

- After Deploy Mode processing has completed successfully, the service in the target is dropped. At that point, it is the responsibility of the DBA for the upgraded Oracle Database to use `ORADIM` to create a service. Creating this service manually is required, because AutoUpgrade does not have the password to obtain permissions to create the ORADIM service.

### AutoUpgrade and Windows Command-Line Interfaces

With command-line interfaces on Windows, applications can stop responding while waiting for a return character to be sent to the console. This behavior can affect the AutoUpgrade utility. The cause is a well-known Microsoft Windows console window characteristic related to the QEM (Quick Edit Mode). Even if you disable the Quick Edit console mode, the application can still encounter this behavior.

To avoid the program waiting for a response, press the enter key a few times after the application starts. Doing this provides the terminal input required to help the application proceed without awaiting a terminal response.

**Related Topics**

- [Oracle Database Administrator’s Reference for Microsoft Windows](../ntqrf/overview-of-ntfs-file-system-and-windows-registry-permissions.md)
- [My Oracle Support Note 1529702.1](https://support.oracle.com/rs?type=doc&id=1529702.1)
- [My Oracle Support Note 1595375.1](https://support.oracle.com/rs?type=doc&id=1595375.1)

**Parent topic:** [Using AutoUpgrade for Oracle Database Upgrades](using-autoupgrade-oracle-database-upgrades.md)
