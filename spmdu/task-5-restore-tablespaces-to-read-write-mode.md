Make the transported tablespaces read/write again at the source database.

The following statements make the `sales_1` and `sales_2` tablespaces read/write:

    ALTER TABLESPACE sales_1 READ WRITE;
    ALTER TABLESPACE sales_2 READ WRITE;

You can postpone this task to first ensure that the import process succeeds.

**Parent topic:** [Migrating Oracle Database](migrating-oracle-database.md)
