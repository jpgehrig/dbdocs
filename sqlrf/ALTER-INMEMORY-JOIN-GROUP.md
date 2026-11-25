## ALTER INMEMORY JOIN GROUP

### Purpose

Use the `ALTER` `INMEMORY` `JOIN` `GROUP` statement to add a table column to a join group or remove a table column from a join group.

**See Also:**

- [CREATE INMEMORY JOIN GROUP](CREATE-INMEMORY-JOIN-GROUP.md) and [DROP INMEMORY JOIN GROUP](DROP-INMEMORY-JOIN-GROUP.md)

- [Oracle Database In-Memory Guide](../inmem/optimizing-queries-with-join-groups.md) for more information on join groups

### Prerequisites

If the join group is not in your own schema, or if the column you want to add to or remove from the join group is in a table that is not in your own schema, then you must have the `ALTER` `ANY` `TABLE` system privilege.

### Syntax

### alter_inmemory_join_group::=

![Description of alter_inmemory_join_group.eps follows](img/alter_inmemory_join_group.gif)
[Description of the illustration alter_inmemory_join_group.eps](img_text/alter_inmemory_join_group.md)

### Semantics

### schema

Specify the schema containing the join group. If you omit `schema`, then the database assumes the join group is in your own schema.

### join_group

Specify the name of the join group to be modified.

You can view existing join groups by querying the `DBA_JOINGROUPS` or `USER_JOINGROUPS` data dictionary view. Refer to [Oracle Database Reference](../refrn/DBA_JOINGROUPS.md) for more information on these views.

### ADD

Specify `ADD` to add a table column to the join group. A join group can contain a maximum of 255 columns.

### REMOVE

Specify `REMOVE` to remove a table column from the join group. A join group must contain at least 2 columns.

### schema

Specify the schema of the table that contains the column to be added to or removed from the join group. If you omit `schema`, then Oracle Database assumes the table is in your own schema.

### table

Specify the name of the table that contains the column to be added to or removed from the join group.

### column

Specify the name of the column to be added to or removed from the join group.

### Examples

The following example adds a column to the `prod_id1` join group created in [Examples](CREATE-INMEMORY-JOIN-GROUP.md) in the documentation on `CREATE` `INMEMORY` `JOIN` `GROUP`:

    ALTER INMEMORY JOIN GROUP prod_id1
      ADD(product_descriptions(product_id));

The following example removes a column from the `prod_id1` join group:

    ALTER INMEMORY JOIN GROUP prod_id1
      REMOVE(product_descriptions(product_id));
