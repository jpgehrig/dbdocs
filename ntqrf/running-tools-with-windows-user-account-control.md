You must ensure that only trusted applications run on your computer.

To ensure that only trusted applications run on your computer, all Windows operating systems supported for Oracle Database 19c provide User Account Control. If you have enabled this security feature, then, depending on how you have configured it, Oracle Universal Installer prompts you for either your consent or your credentials when installing Oracle Database Client. Provide either the consent or your Windows Administrator credentials as appropriate.

You must have the Administrator privileges to run some configuration tools, or to run any tool or application that writes to any directory within the Oracle home. If User Account Control is enabled, and you are logged in as the local Administrator, then you can successfully run each of these commands in the usual way. However, if you are logged in as a member of the Administrator group, then you must explicitly run these tasks with Windows Administrator privileges.

The following tools must be run with Administrator privileges:

- Oracle Net Configuration Assistant. This tool is available as a Configuration and Migration Tool.

- Oracle OLAP Analytic Workspace Manager and Worksheet. This tool is available as an Integrated Management Tool.

- Oracle Database Configuration Assistant. This tool is available as a Configuration and Migration Tool.

- Oracle Database Wallet Manager. This tool is available as an Integrated Management Tool.

- Oracle Database Upgrade Assistant. This tool is available as a Configuration and Migration Tool.

- Oracle Net Manager. This tool is available as a Configuration and Migration Tool.

- Oracle ASM Configuration Assistant. This tool is available as a Configuration and Migration Tool.

- Oracle ASM Disk Stamping Tool (`asmtool`, `asmtoolg`). This tool is available as a Configuration and Migration Tool.

To run any Start menu tool with Administrator privileges:

1.  Click the Start menu option.

2.  Select All Programs, then select Oracle - HOMENAME.

3.  Select the name of the tool, then right-click the name of the tool or application you want to run, and then select Run as administrator.

These steps describe how to start a tool as an Administrator from the command prompt:

1.  Create a shortcut for the command prompt window on your desktop. An icon for that shortcut appears on the desktop.
2.   Right-click the icon for the newly created shortcut, and specify Run as administrator.
    When you open this window, the title bar reads Administrator: Command Prompt. Commands running within this window are run with Administrator privileges.

**See Also:**

[Oracle Database Installation Guide for Microsoft Windows](../ntdbi/managing-ussser-accounts-with-user-account-control.md)

**Parent topic:** [Starting Database Tools](starting-database-tools.md)
