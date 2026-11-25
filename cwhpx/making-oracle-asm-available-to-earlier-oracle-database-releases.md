To use Oracle ASM with Oracle Database releases earlier than Oracle Database 12c Release 2 (12.2), you must pin all the cluster nodes.

After you install Oracle Grid Infrastructure 18c or later release, if you want to use Oracle ASM to provide storage service for Oracle Database releases that are earlier than Oracle Database 12c Release 2 (12.2), then you must use the following command to pin the nodes:

`$ crsctl pin css -n node1 node2`

This setting updates the `oratab` file for Oracle ASM entries.

You can check the pinned nodes using the following command:

`$ ./olsnodes -t -n`

**Note:**

Restart Oracle ASM to load the updated `oratab` file.

**Parent topic:** [Using Earlier Oracle Database Releases with Oracle Grid Infrastructure](using-earlier-oracle-database-releases-with-oracle-grid-infrastructure.md)
