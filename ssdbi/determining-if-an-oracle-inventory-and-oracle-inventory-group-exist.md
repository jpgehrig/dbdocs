Determine if you have an existing Oracle central inventory, and ensure that you use the same Oracle Inventory for all Oracle software installations. Also, ensure that all Oracle software users you intend to use for installation have permissions to write to this directory.

When you install Oracle software on the system for the first time, OUI creates the `oraInst.loc` file. This file identifies the name of the Oracle Inventory group (by default, `oinstall`), and the path of the Oracle central inventory directory. If you have an existing Oracle central inventory, then ensure that you use the same Oracle Inventory for all Oracle software installations, and ensure that all Oracle software users you intend to use for installation have permissions to write to this directory.

An `oraInst.loc` file contains lines in the following format, where `central_inventory_location` is the path to an existing Oracle central inventory, and `group` is the name of the operating system group whose members have permissions to write to the central inventory:

    inventory_loc=central_inventory_location
    inst_group=group

Use the `more` command to determine if you have an Oracle central inventory on your system. For example:

`# more /var/opt/oracle/oraInst.loc`

    inventory_loc=/u01/app/oraInventory
    inst_group=oinstall

Use the command `grep groupname /etc/group` to confirm that the group specified as the Oracle Inventory group still exists on the system. For example:

    $ grep oinstall /etc/group
    oinstall:x:54321:grid,oracle

**Note:**

Do not put the `oraInventory` directory under the Oracle base directory for a new installation, because that can result in user permission errors for other installations.

**Parent topic:** [Required Operating System Groups and Users](required-operating-system-groups-and-users.md)
