Create an Oracle Inventory group manually as part of a planned installation, particularly where more than one Oracle software product is installed on servers.

By default, if an oraInventory group does not exist, then the installer uses the primary group of the installation owner for the Oracle software being installed as the oraInventory group. Ensure that this group is available as a primary group for all planned Oracle software installation owners. If the `oraInst.loc` file does not exist, then create the Oracle Inventory group using the following procedure:

1.   Enter the following command:
        # smit security
2.  Choose the appropriate menu items to create the Oracle Inventory (`oinstall`) group.
3.  Press F10 to exit.

**Parent topic:** [Required Operating System Groups and Users](required-operating-system-groups-and-users.md)
