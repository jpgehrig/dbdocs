## Creating Identical Database Users and Groups on Other Cluster Nodes

Oracle software owner users and the Oracle Inventory, OSDBA, and OSOPER groups must exist and be identical on all cluster nodes.

To create users and groups on the other cluster nodes, repeat the following procedure on each node:

You must complete the following procedures only if you are using local users and groups. If you are using users and groups defined in a directory service such as NIS, then they are already identical on each cluster node.

1.  Log in to the node as `root`.
2.  Enter commands similar to the following to create the `asmadmin`, `asmdba`, `backupdba`, `dgdba`, `kmdba`, `asmoper`, `racdba`, and `oper` groups, and if not configured by the Oracle Database Preinstallation RPM or prior installations, then the `oinstall` and `dba` groups.
    Use the `-g` option to specify the correct group ID for each group.

        # groupadd -g 54421 oinstall
        # groupadd -g 54322 dba
        # groupadd -g 54323 oper
        # groupadd -g 54324 backupdba
        # groupadd -g 54325 dgdba
        # groupadd -g 54326 kmdba
        # groupadd -g 54327 asmdba
        # groupadd -g 54328 asmoper
        # groupadd -g 54329 asmadmin
        # groupadd -g 54330 racdba

    **Note:**

    You are not required to use the UIDs and GIDs in this example. If a group already exists, then use the `groupmod` command to modify it if necessary. If you cannot use the same group ID for a particular group on a node, then view the `/etc/group` file on all nodes to identify a group ID that is available on every node. You must then change the group ID on all nodes to the same group ID.
3.  To create the Oracle Grid Infrastructure (`grid`) user, enter a command similar to the following:
        # useradd -u 54322 -g oinstall -G asmadmin,asmdba,racdba grid

    - The `-u` option specifies the user ID, which must be the user ID that you identified earlier.

    - The `-g` option specifies the primary group for the Grid user, which must be the Oracle Inventory group (OINSTALL), which grants the OINSTALL system privileges. In this example, the OINSTALL group is `oinstall`.

    - The `-G` option specifies the secondary groups. The Grid user must be a member of the OSASM group (`asmadmin`) and the OSDBA for ASM group (`asmdba`).

    **Note:**

    If the user already exists, then use the `usermod` command to modify it if necessary. If you cannot use the same user ID for the user on every node, then view the `/etc/passwd` file on all nodes to identify a user ID that is available on every node. You must then specify that ID for the user on all of the nodes.
4.  Set the password of the user.
    For example:

        # passwd grid
5.  Complete user environment configuration tasks for each user.

**Parent topic:** [Creating Operating System Oracle Installation User Accounts](creating-operating-system-oracle-installation-user-accounts.md)
