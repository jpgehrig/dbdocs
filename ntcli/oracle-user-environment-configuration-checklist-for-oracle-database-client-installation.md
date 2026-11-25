## Oracle User Environment Configuration Checklist for Oracle Database Client Installation

Use this checklist to plan operating system users, groups, and environments for Oracle Database Client management.

Table 1-4 Oracle User Environment Configuration Checklist for Oracle Database Client Installation

| Check                                                                                     | Task                                                                                                                                                                                                                                                                                                                                |
|:------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Oracle Inventory and `ORA_INSTALL` Group Requirements                                     | The Oracle Inventory directory is the central inventory of Oracle software installed on your system. You do not need to create the Oracle central inventory or the `ORA_INSTALL` group as Oracle Universal Installer creates it for you.                                                                                            |
| Create operating system groups and users for standard or role-allocated system privileges | Create operating system groups and users depending on your security requirements, as described in this install guide.                                                                                                                                                                                                               |
| Unset Oracle Software Environment Variables                                               | If you have an existing installation on your system, and use the same user account to install this installation, then unset the `ORACLE_HOME`, `ORACLE_BASE`, `ORACLE_SID`, `TNS_ADMIN` environment variables and any other environment variable set for the Oracle installation user that is connected with Oracle software homes. |

**Parent topic:** [Oracle Database Client Installation Checklist](oracle-database-client-installation-checklist.md)
