## Using DBCA to Select Storage to Use With Oracle RAC Database

You can choose to use either Oracle ASM Disk groups or a shared file system as storage for Oracle RAC database files.

- On the Specify Database Storage Options page, if you do not see the diskgroups in Oracle Database Configuration Assistant (DBCA), then either Oracle ASM is not configured, or the diskgroups are not mounted.
  You can create diskgroups using Oracle Automatic Storage Management Configuration Assistant (ASMCA) in the Grid Infrastructure home before starting DBCA.
- If you are using Oracle ASM, then you can select the Fast Recovery Area and size on the Specify Database Storage Options page.
  When using Oracle ASM, the Fast Recovery Area defaults to the Oracle ASM Disk Group.

**Parent topic:** [Selecting DBCA Options to Create an Oracle RAC or Oracle RAC One Node Database](creating-an-oracle-rac-or-oracle-rac-one-node-database-with-dbca.md)
