## DROP CONTEXT

### Purpose

Use the `DROP` `CONTEXT` statement to remove a context namespace from the database.

Removing a context namespace does not invalidate any context under that namespace that has been set for a user session. However, the context will be invalid when the user next attempts to set that context.

**See Also:**

[CREATE CONTEXT](CREATE-CONTEXT.md) and [Oracle Database Security Guide](../dbseg/using-application-contexts-to-retrieve-user-information.md) for more information on contexts

### Prerequisites

You must have the `DROP` `ANY` `CONTEXT` system privilege.

### Syntax

### drop_context::=

![Description of drop_context.eps follows](img/drop_context.gif)
[Description of the illustration drop_context.eps](img_text/drop_context.md)

### Semantics

### namespace

Specify the name of the context namespace to drop. You cannot drop the built-in namespace `USERENV`.

**See Also:**

[SYS_CONTEXT](SYS_CONTEXT.md) for information on the `USERENV` namespace

### Examples

Dropping an Application Context: Example

The following statement drops the context created in [CREATE CONTEXT](CREATE-CONTEXT.md):

    DROP CONTEXT hr_context;
