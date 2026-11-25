## Creating the Oracle Inventory Group If an Oracle Inventory Does Not Exist

Create an Oracle Inventory group manually as part of a planned installation, particularly where more than one Oracle software product is installed on servers.

By default, if an oraInventory group does not exist, then the installer uses the primary group of the installation owner for the Oracle software being installed as the oraInventory group. Ensure that this group is available as a primary group for all planned Oracle software installation owners.

If the `oraInst.loc` file does not exist, then create the Oracle Inventory group by entering a command similar to the following:

    # /usr/sbin/groupadd -g 54321 oinstall

**Parent topic:** [Required Operating System Groups and Users](required-operating-system-groups-and-users.md)
