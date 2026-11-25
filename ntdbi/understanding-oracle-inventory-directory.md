## Understanding the Oracle Inventory Directory and the Oracle Inventory Group

The Oracle Inventory directory is the central inventory location for all Oracle software installed on a server.

By default, the location of the Oracle Inventory directory is `C:\Program Files\Oracle\Inventory`.

When you install Oracle software on the system for the first time, Oracle Universal Installer creates the directories for the Oracle central inventory and the Oracle Inventory group, `ORA_INSTALL`. The `ORA_INSTALL` group contains all the Oracle Home Users for all Oracle homes on the server.

Whether you are performing the first installation of Oracle software on this server, or are performing an installation of additional Oracle software on the server, you do not need to create the Oracle central inventory or the `ORA_INSTALL` group; the Oracle Universal Installer creates them automatically. You cannot change the name of the Oracle Inventory group - it is always `ORA_INSTALL`.

**Parent topic:** [Creating Required Operating System Groups and Users](creating-required-operating-system-groups-and-users.md)
