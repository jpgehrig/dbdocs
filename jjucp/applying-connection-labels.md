Labels are applied on a borrowed connection using the `applyConnectionLabel` method from the `LabelableConnection` interface. This method is typically called from the `configure` method of the labeling callback. Any number of connection labels may be cumulatively applied on a borrowed connection. Each time a label is applied to a connection, the supplied key/value pair is added to the collection of labels already applied to the connection. Only the last applied value is retained for any given key.

**Note:**

A labeling callback must be registered on the connection pool before a label can be applied on a borrowed connection; otherwise, an exception is thrown.

The following example demonstrates initializing a connection with a transaction isolation level and then applying a label to the connection:

    String pname = "property1";
    String pvalue = "value";
    Connection conn = pds.getConnection();

    // initialize the connection as required.

    conn.setTransactionIsolation(Connection.TRANSACTION_SERIALIZABLE);

    ((LabelableConnection) conn).applyConnectionLabel(pname, pvalue);

In order to remove a given key from the set of connection labels applied, apply a label with the key to be removed and a `null` value. This may be used to clear a particular key/value pair from the set of connection labels.

**Related Topics**

- [Implementation of a Labeling Callback in UCP](implementing-labeling-ucp-connections.md)
