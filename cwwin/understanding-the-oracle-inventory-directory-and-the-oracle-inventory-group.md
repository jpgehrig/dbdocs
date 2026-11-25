## Understanding the Oracle Inventory Directory and the Oracle Inventory Group

You must have a group whose members are given access to write to the Oracle Inventory directory, which is the central inventory record of all Oracle software installations on a server.

When you install Oracle software on the system for the first time, Oracle Universal Installer (OUI) creates the directories for the Oracle central inventory. OUI also creates the Oracle Inventory group, `ORA_INSTALL`. The `ORA_INSTALL` group contains all the Oracle Home users for all Oracle homes on the server. The location of the Oracle central inventory on Windows is always `%SYSTEM_DRIVE%\Program Files\Oracle\Inventory`.

Whether you are performing the first installation of Oracle software on this server, or are performing an installation of additional Oracle software on the server, you do not need to create the Oracle central inventory or the `ORA_INSTALL` group. You cannot change the name of the Oracle Inventory group - it is always `ORA_INSTALL`.

Members of the Oracle Inventory group have write privileges to the Oracle central inventory directory, and are also granted permissions for various Oracle Clusterware resources, OCR keys, directories in the Oracle Clusterware home to which DBAs need write access, and other necessary privileges. All Oracle software install users must be members of the Oracle Inventory group. Members of this group can talk to Cluster Synchronization Service (CSS).

**Note:**

If Oracle software is already installed on the system, then, when you install new Oracle software, the existing Oracle Inventory group is used instead of creating a new Inventory group.

**Parent topic:** [Creating Installation Groups and Users for Oracle Grid Infrastructure and Oracle RAC](creating-installation-groups-and-users-for-grid-and-rac.md)
