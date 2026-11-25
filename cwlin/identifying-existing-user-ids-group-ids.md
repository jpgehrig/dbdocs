## Identifying Existing User and Group IDs

To create identical users and groups, you must identify the user ID and group IDs assigned them on the node where you created them, and then create the user and groups with the same name and ID on the other cluster nodes.

1.  Enter a command similar to the following (in this case, to determine a user ID for the `oracle` user):
        # id oracle

    The output from this command is similar to the following:
        uid=54321(oracle) gid=54421(oinstall) groups=54322(dba),54323(oper),54327(asmdba)
2.  From the output, identify the user ID (`uid`) for the user and the group identities (`gids`) for the groups to which it belongs.
    Ensure that these ID numbers are identical on each node of the cluster. The user's primary group is listed after `gid`. Secondary groups are listed after groups.

**Parent topic:** [Creating Operating System Oracle Installation User Accounts](creating-operating-system-oracle-installation-user-accounts.md)
