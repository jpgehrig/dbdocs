## Creating the Oracle Inventory Group If an Oracle Inventory Does Not Exist

If the `oraInst.loc` file does not exist, then create the Oracle Inventory group.

Members of the OINSTALL group are granted privileges to write to the Oracle central inventory (`oraInventory`), and other system privileges for Oracle installation owner users.

An Oracle installation owner should always have the group you want to have designated as the OINSTALL group (`oinstall`) as its primary group. Ensure that this group is available as the primary group for all planned Oracle software installation owners. By default, if an `oraInst.loc` file does not exist and an Oracle central inventory (`oraInventory`) is not identified, then the installer designates the primary group of the installation owner running the installation as the OINSTALL group.

The following example creates the oraInventory group `oinstall`, with the group ID number 54321.

    # /usr/sbin/groupadd -g 54321 oinstall

**Note:**

For installations on Oracle Clusterware, group and user IDs must be identical on all nodes in the cluster. Ensure that the group and user IDs you want to use are available on each cluster member node, and confirm that the primary group for each Oracle Grid Infrastructure for a cluster installation owner has the same name and group ID.

**Parent topic:** [Creating Groups, Users and Paths for Oracle Grid Infrastructure](creating-users-groups-paths-for-grid-infrastructure.md)
