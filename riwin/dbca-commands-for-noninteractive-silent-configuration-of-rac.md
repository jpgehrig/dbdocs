## Using DBCA Commands for Noninteractive (Silent) Configuration of Oracle RAC

You can use Oracle Database Configuration Assistant (DBCA) in non-interactive mode to create an Oracle RAC database.

Example A-1 Using DBCA in Silent Mode to Create an Oracle RAC Database

You can use the following command syntax to create an Oracle RAC database using the general purpose template, placing the data files in an existing Oracle ASM disk group. Nodes `node1` and `node2` are the cluster nodes on which Oracle RAC database instances are created. The disk group name is `+ASMgrp1`. An Oracle Home User was specified for this installation, and is indicated with the `-serviceUserPassword` option:

    %ORACLE_HOME%\bin\dbca -silent -createDatabase -templateName General_Purpose.dbc
    -gdbName %DBNAME% -sid %ORACLE_SID% -sysPassword -systemPassword
    -sysmanPassword -dbsnmpPassword  -serviceUserPassword
    -emConfiguration LOCAL -storageType ASM -diskGroupName +ASMgrp1
    -datafileJarLocation %ORACLE_HOME%\assistants\dbca\templates
    -nodeinfo node1,node2 -characterset WE8MSWIN1252
    -obfuscatedPasswords false -sampleSchema false -asmSysPassword

After you run this command, if you did not include the passwords as values in the above command, then DBCA prompts you for the passwords for the SYS, SYSTEM, SYSMAN, DBSNMP, Oracle Home (or Oracle Service) and SYSASM users, for example:

    Enter SYS user password:
    password
    Enter SYSTEM user password:
    password
    ...

**See Also:**

[Oracle Database Administrator's Guide](../admin/creating-and-configuring-an-oracle-database.md) for a complete description of the `dbca` commands and options

**Parent topic:** [Using Scripts or Response Files to Create Oracle RAC Databases](using-scripts-or-response-files-to-create-oracle-rac-databases.md)
