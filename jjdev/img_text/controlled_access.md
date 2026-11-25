# Description of the illustration controlled_access.gif

The figure illustrates the indirect access of the `payroll` table. The `EAST` and `WEST` schema have their own `sales` tables. These schemas access the analyze procedure of the HQ schema, which calls the definer's rights procedure, `calcComm`, which in turn accesses the `payroll` table on the `HQ` schema.
