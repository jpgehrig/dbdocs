## Managing User Accounts with User Account Control

To ensure that only trusted applications run on your computer, Windows Server provides User Account Control.

If you have enabled the User Account Control security feature, then depending on how you have it configured, OUI prompts you for either your consent or your credentials when installing Oracle Database. Provide either the consent or your Windows Administrator credentials as appropriate.

You must have Administrator privileges to run some Oracle tools, such as DBCA, NETCA, and OPatch, or to run any tool or application that writes to any directory within the Oracle home. If User Account Control is enabled and you are logged in as the local Administrator, then you can successfully run each of these commands. However, if you are logged in as "a member of the Administrators group," then you must explicitly run these tools with Windows Administrator privileges.

All of the Oracle shortcuts that require Administrator privileges are automatically run as an "Administrator" user when you click the shortcuts. However, if you run the previously mentioned tools from a Windows command prompt, then you must run them from an Administrator command prompt.

OPatch does not have a shortcut and must be run from an Administrator command prompt.

**Parent topic:** [Configuring User Accounts](configuring-user-accounts.md)
