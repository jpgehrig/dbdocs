## Using DBCA to Select Storage to Use With any Oracle RAC Database

You can choose to use either Oracle ASM disk groups or a supported cluster file system as storage.

On the Specify Database Storage Options page, if you do not see the disk groups in DBCA, then either Oracle ASM is not configured, or disk groups are not mounted. You can create disk groups using ASMCA in the Grid Infrastructure home before starting DBCA.

If you are using Oracle ASM or cluster file system storage, then you can also select the fast recovery area and size on this page. If you are using Oracle ASM, then the Fast Recovery Area defaults to the Oracle ASM disk group.

**Parent topic:** [Selecting DBCA Options to Create an Oracle RAC or Oracle RAC One Node Database](creating-an-oracle-rac-or-oracle-rac-one-node-database-with-dbca.md)
