Oracle Database 19c provides access control to separate the roles on Windows.

With Oracle Database services running under the Oracle Home User account instead of the Local System Account, the Oracle ASM access control feature must be enabled to support role separation on Windows. In previous releases, this feature was disabled on Windows because all Oracle Database services ran under Windows Built-in Local System Account.

The new user groups added are `ORA_``HOMENAME``_DBA`, `ORA_``HOMENAME``_OPER`, `ORA_``HOMENAME``_SYSBACKUP`, and so on. For Oracle ASM administration, new groups `ORA_ASMADMIN`, `ORA_ASMDBA` and `ORA_ASMOPER` are automatically created and populated during Oracle Database installation. The Oracle ASM administrator can manage these Windows groups using Windows tools, though you must ensure that the required user names are not removed from these groups.

**Related Topics**

- [Managing New Users and User Groups](managing-new-users-and-user-groups.md)

**See Also:**

- [Oracle Database Installation Guide for Microsoft Windows](../ntdbi/operating-system-groups-and-users-for-job-role-separation.md)

- [Oracle Grid Infrastructure Installation and Upgrade Guide for Microsoft Windows x64 (64-Bit)](../cwwin/standard-administration-and-job-role-separation-user-groups.md)

**Parent topic:** [Oracle Automatic Storage Management File Access Control](oracle-automatic-storage-management-file-access-control.md)
