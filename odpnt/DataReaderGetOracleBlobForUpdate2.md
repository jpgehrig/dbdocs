This method returns an updatable `OracleBlob` object of the specified `BLOB` column using a `WAIT` clause.

### Declaration

    // C#
    public OracleBlob GetOracleBlobForUpdate(int index, int wait);

### Parameters

- `index`

  The zero-based column index.

- `wait`

  The number of seconds the method waits to acquire a lock.

### Return Value

An updatable `OracleBlob` object.

### Exceptions

`InvalidOperationException` - The connection is closed, the reader is closed, `Read()` has not been called, or all rows have been read.

`IndexOutOfRangeException` - The column index is invalid.

`InvalidCastException` - The accessor method is invalid for this column type or the column value is `NULL`.

### Remarks

When the `OracleCommand`'s `ExecuteReader()` method is invoked, all the data fetched by the `OracleDataReader` is from a particular snapshot. Therefore, calling an accessor method on the same column always returns the same value. However, the `GetOracleBlobForUpdate()` method incurs a database round-trip to obtain a reference to the current `BLOB` data while also locking the row using the `FOR` `UPDATE` clause. This means that the `OracleBlob` obtained from `GetOracleBlob()` can have a different value than the `OracleBlob` obtained from `GetOracleBlobForUpdate()` since it is not obtained from the original snapshot.

`IsDBNull` should be called to check for `NULL` values before calling this method.

The returned `OracleBlob` object can be used to safely update the `BLOB` because the `BLOB` column has been locked after a call to this method.

Invoking this method internally executes a `SELECT..FOR UPDATE` statement which locks the row.

Different `WAIT` clauses are appended to the statement, depending on the `wait` value. If the `wait` value is:

- `0`

  "`NOWAIT`" is appended at the end of a `SELECT..FOR` `UPDATE` statement. The statement executes immediately whether the lock is acquired or not. If the lock is not acquired, an exception is thrown.

- `n`

  "`WAIT` `n`" is appended at the end of a `SELECT..FOR` `UPDATE` statement. The statement executes as soon as the lock is acquired. However, if the lock cannot be acquired by `n` seconds, this method call throws an exception.

  The `WAIT` `n`" feature is only available for Oracle9i or later. For any version lower than Oracle9i, `n` is implicitly treated as `-1` and nothing is appended at the end of a `SELECT..FOR` `UPDATE` statement.

- `-1`

  Nothing is appended at the end of the `SELECT..FOR` `UPDATE`. The statement execution waits indefinitely until a lock can be acquired.

### Example

The `GetOracleBlobForUpdate` methods are comparable. See "[Example](DataReaderGetOracleBlobForUpdate1.md)" for a code example demonstrating usage.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Class](OracleDataReaderClass.md)

- [OracleDataReader Members](DataReaderMembers.md)

- "[LOB Support](featLOBsupp.md)"
