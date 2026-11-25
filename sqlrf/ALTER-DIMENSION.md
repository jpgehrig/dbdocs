## ALTER DIMENSION

### Purpose

Use the `ALTER` `DIMENSION` statement to change the hierarchical relationships or dimension attributes of a dimension.

**See Also:**

[CREATE DIMENSION](CREATE-DIMENSION.md) and [DROP DIMENSION](DROP-DIMENSION.md)

### Prerequisites

The dimension must be in your schema or you must have the `ALTER` `ANY` `DIMENSION` system privilege to use this statement.

A dimension is always altered under the rights of the owner.

### Syntax

### alter_dimension::=

![Description of alter_dimension.eps follows](img/alter_dimension.gif)
[Description of the illustration alter_dimension.eps](img_text/alter_dimension.md)

(level_clause::=, hierarchy_clause::=, attribute_clause::=, extended_attribute_clause::=)

### level_clause::=

![Description of level_clause.eps follows](img/level_clause.gif)
[Description of the illustration level_clause.eps](img_text/level_clause.md)

### hierarchy_clause::=

![Description of hierarchy_clause.eps follows](img/hierarchy_clause.gif)
[Description of the illustration hierarchy_clause.eps](img_text/hierarchy_clause.md)

(dimension_join_clause::=)

### dimension_join_clause::=

![Description of dimension_join_clause.eps follows](img/dimension_join_clause.gif)
[Description of the illustration dimension_join_clause.eps](img_text/dimension_join_clause.md)

### attribute_clause::=

![Description of attribute_clause.eps follows](img/attribute_clause.gif)
[Description of the illustration attribute_clause.eps](img_text/attribute_clause.md)

### extended_attribute_clause::=

![Description of extended_attribute_clause.eps follows](img/extended_attribute_clause.gif)
[Description of the illustration extended_attribute_clause.eps](img_text/extended_attribute_clause.md)

### Semantics

The following keywords, parameters, and clauses have meaning unique to `ALTER` `DIMENSION`. Keywords, parameters, and clauses that do not appear here have the same functionality that they have in the `CREATE` `DIMENSION` statement. Refer to [CREATE DIMENSION](CREATE-DIMENSION.md) for more information.

### schema

Specify the schema of the dimension you want to modify. If you do not specify `schema`, then Oracle Database assumes the dimension is in your own schema.

### dimension

Specify the name of the dimension. This dimension must already exist.

ADD

The `ADD` clauses let you add a level, hierarchy, or attribute to the dimension. Adding one of these elements does not invalidate any existing materialized view.

Oracle Database processes `ADD` `LEVEL` clauses prior to any other `ADD` clauses.

DROP

The `DROP` clauses let you drop a level, hierarchy, or attribute from the dimension. Any level, hierarchy, or attribute you specify must already exist.

Within one attribute, you can drop one or more level-to-column relationships associated with one level.

Restriction on DROP

If any attributes or hierarchies reference a level, then you cannot drop the level until you either drop all the referencing attributes and hierarchies or specify `CASCADE`.

CASCADE

Specify `CASCADE` if you want Oracle Database to drop any attributes or hierarchies that reference the level, along with the level itself.

RESTRICT

Specify `RESTRICT` if you want to prevent Oracle Database from dropping a level that is referenced by any attributes or hierarchies. This is the default.

COMPILE

Specify `COMPILE` to explicitly recompile an invalidated dimension. Oracle Database automatically compiles a dimension when you issue an `ADD` clause or `DROP` clause. However, if you alter an object referenced by the dimension (for example, if you drop and then re-create a table referenced in the dimension), Oracle Database invalidates, and you must recompile it explicitly.

### Examples

Modifying a Dimension: Examples

The following examples modify the `customers_dim` dimension in the sample schema `sh`:

    ALTER DIMENSION customers_dim
       DROP ATTRIBUTE country;

    ALTER DIMENSION customers_dim
       ADD LEVEL zone IS customers.cust_postal_code
       ADD ATTRIBUTE zone DETERMINES (cust_city);
