If you created statistics tables using the `DBMS_STATS.CREATE_STAT_TABLE` procedure, then upgrade these tables by running `DBMS_STATS.UPGRADE_STAT_TABLE`.

In the following example, `green` is the owner of the statistics table and `STAT_TABLE` is the name of the statistics table.

    EXECUTE DBMS_STATS.UPGRADE_STAT_TABLE('green', 'stat_table');

Perform this procedure for each statistics table.

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_STATS.md) for information about the DBMS_STATS package

**Parent topic:** [Recommended and Best Practices to Complete After Upgrading Oracle Database](recommended-and-best-practices-complete-upgrading-oracle-database.md)
