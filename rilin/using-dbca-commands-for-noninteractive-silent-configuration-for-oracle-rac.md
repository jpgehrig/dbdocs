## Using DBCA Commands for Noninteractive (Silent) Configuration for Oracle RAC

Review this topic for the command syntax to create an Oracle RAC database using DBCA.

You can use the following command syntax to create an Oracle RAC database using the general purpose template, placing the data files in an existing Oracle ASM disk group. Nodes `node1` and `node2` are the cluster nodes on which Oracle RAC database instances are created. The disk group name is `+ASMgrp1`, and `password` is a placeholder for a password. The passwords can be all the same password or different passwords each time:

    # su oracle -c "$ORACLE_HOME/bin/dbca -silent -createDatabase -templateName
    General_Purpose.dbc -gdbName $DBNAME -sid $ORACLE_SID -sysPassword password
    -systemPassword password -sysmanPassword password -dbsnmpPassword password
    -emConfiguration LOCAL -storageType ASM -diskGroupName ASMgrp1
    -datafileJarLocation $ORACLE_HOME/assistants/dbca/templates -nodeinfo
    node1,node2 -characterset WE8ISO8859P1 -obfuscatedPasswords false -sampleSchema
    false -asmSysPassword password"

**See Also:**

[Oracle Database Administrator's Guide](../admin/creating-and-configuring-an-oracle-database.md) for a complete description of DBCA commands and options

**Parent topic:** [Using Scripts or Response Files to Create Oracle RAC Databases](using-scripts-or-response-files-to-create-oracle-rac-databases.md)
