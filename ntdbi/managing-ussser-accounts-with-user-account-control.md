## Managing User Accounts with User Account Control

To ensure that only trusted applications run on your computer, the Windows operating systems that support Oracle Database, provide User Account Control.

If you have enabled this security feature, then, depending on the configuration, Oracle Universal Installer prompts you for either your consent or your credentials when installing Oracle Database.

You must have Administrator privileges to run Oracle tools, such as Database Configuration Assistant, Net Configuration Assistant, and OPatch, or to run any tool or application that writes to any directory within the Oracle home. If User Account Control is enabled, and you are logged in as the local Administrator, then you can successfully run each of these commands. However, if you are logged in as a member of the Administrator group, then you must explicitly start these tasks with Windows Administrator privileges. All the Oracle shortcuts that require Administrator privileges start as Administrator by default when you click the shortcuts. However, if you run the above tools from a Windows command prompt, you must run them from an Administrator command prompt. OPatch does not have a shortcut and has to be run from an Administrator command prompt.

**See Also:**

[Oracle Database Administrator’s Reference for Microsoft Windows](../ntqrf/running-tools-with-windows-user-account-control.md)

### To start a command prompt window with Windows Administrator privileges:

1.  On your desktop, create a shortcut for the command prompt window. An icon for that shortcut appears on the desktop.
2.  Right-click the icon for the newly created shortcut, and specify Run as administrator.

When you open this window, the title bar reads Administrator: Command Prompt. Run commands from within this window using Administrator privileges.

**Parent topic:** [Configuring User Accounts](configuring-user-accounts.md)
