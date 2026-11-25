This section describes how the `OracleDataAdapter` object configures the `PrimaryKey` and `Constraints` properties of the `DataTable` object which guarantee uniqueness when the `OracleCommandBuilder` object is updating `DataSet` changes to the database.

Using the `OracleCommandBuilder` object to dynamically generate DML statements to be executed against the database is one of the ways to reconcile changes made in a single `DataTable` object with the database.

In this process, the `OracleCommandBuilder` object must not be allowed to generate DML statements that may affect (update or delete) more that a single row in the database when reconciling a single `DataRow` change. Otherwise the `OracleCommandBuilder` could corrupt data in the database.

To guarantee that each `DataRow` object change affects only a single row, there must be a set of `DataColumn` objects in the `DataTable` for which all rows in the `DataTable` have a unique set of values. The set of `DataColumn` objects indicated by the properties `DataTable.PrimaryKey` and `DataTable.Constraints` meets this requirement. The `OracleCommandBuilder` object determines uniqueness in the `DataTable` by checking if the `DataTable.PrimaryKey` is not a null value or if there exists a `UniqueConstraint` object in the `DataTable.Constraints` collection.

This discussion first explains what constitutes uniqueness in `DataRow` objects and then explains how to maintain that uniqueness while updating, through the `DataTable` property configuration.

This section includes the following topics:

- What Constitutes Uniqueness in DataRow Objects?

- Configuring PrimaryKey and Constraints Properties

- Updating Without PrimaryKey and Constraints Configuration

### What Constitutes Uniqueness in DataRow Objects?

This section describes the minimal conditions that must be met to guarantee uniqueness of `DataRow` objects. The condition of uniqueness must be guaranteed before the `DataTable.PrimaryKey` and `DataTable.Constraints` properties can be configured, as described in the next section.

Uniqueness is guaranteed in a `DataTable` object if any one of the following is true:

- All the columns of the primary key are in the select list of the `OracleDataAdapter.SelectCommand` property.

- All the columns of a unique constraint are in the select list of the `OracleDataAdapter.SelectCommand` property, with at least one involved column having a `NOT` `NULL` constraint defined on it.

- All the columns of a unique index are in the select list of the `OracleDataAdapter.SelectCommand` property, with at least one of the involved columns having a `NOT` `NULL` constraint defined on it.

- A `ROWID` is present in the select list of the `OracleDataAdapter.SelectCommand` property.

**Note:**

A set of columns, on which a unique constraint has been defined or a unique index has been created, requires at least one column that cannot be null for the following reason: if all the columns of the column set can be null, then multiple rows could exist that have a `NULL` value for each column in the column set. This would violate the uniqueness condition that each row has a unique set of values for the column set.

### Configuring PrimaryKey and Constraints Properties

If the minimal conditions described in "What Constitutes Uniqueness in DataRow Objects?" are met, then the `DataTable.PrimaryKey` or `DataTable.Constraints` properties can be set.

After these properties are set, the `OracleCommandBuilder` object can determine uniqueness in the `DataTable` by checking the `DataTable.PrimaryKey` property or the presence of a `UniqueConstraint` object in the `DataTable.Constraints` collection. Once uniqueness is determined, the `OracleCommandBuilder` object can safely generate DML statements to update the database.

The `OracleDataAdapter.FillSchema` method attempts to set these properties according to this order of priority:

1.  If the primary key is returned in the select list, it is set as the `DataTable.PrimaryKey` property.

2.  If a set of columns that meets the following criteria is returned in the select list, it is set as the `DataTable.PrimaryKey` property.

    Criteria: The set of columns has a unique constraint defined on it or a unique index created on it, with each column having a `NOT` `NULL` constraint defined on it.

3.  If a set of columns that meets the following criteria is returned in the select list, a `UniqueConstraint` object is added to the `DataTable.Constraints` collection, but the `DataTable.PrimaryKey` property is not set.

    Criteria: The set of columns has a unique constraint defined on it or a unique index created on it, with at least one column having a `NOT` `NULL` constraint defined on it.

4.  If a `ROWID` is part of the select list, it is set as the `DataTable.PrimaryKey` property.

Additionally, the `OracleDataAdapter.FillSchema` method performs as follows:

- Setting the `DataTable.PrimaryKey` property implicitly creates a `UniqueConstraint` object.

- If a column is part of the `DataTable.PrimaryKey` property or the `UniqueConstraint` object, or both, it will be repeated for each occurrence of the column in the select list.

### Updating Without PrimaryKey and Constraints Configuration

If the `DataTable.PrimaryKey` or `Constraints` properties have not been configured, for example, if the application has not called the `OracleDataAdapter.FillSchema` method, the `OracleCommandBuilder` object directly checks the select list of the `OracleDataAdapter.SelectCommand` property to determine if it guarantees uniqueness in the `DataTable`. However this check results in a database round-trip to retrieve the metadata for the `SELECT` statement of the `OracleDataAdapter.SelectCommand`.

Note that `OracleCommandBuilder` object cannot update a `DataTable` created from PL/SQL statements because they do not return any key information in their metadata.
