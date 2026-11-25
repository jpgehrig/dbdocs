This method returns an updatable `OracleBlob` object of the specified `BLOB` column.

### Declaration

    // C#
    public OracleBlob GetOracleBlobForUpdate(int index);

### Parameters

- `index`

  The zero-based column index.

### Return Value

An updatable `OracleBlob` object.

### Exceptions

`InvalidOperationException` - The connection is closed, the reader is closed, `Read()` has not been called, or all rows have been read.

`IndexOutOfRangeException` - The column index is invalid.

`InvalidCastException` - The accessor method is invalid for this column type or the column value is `NULL`.

### Remarks

When the `OracleCommand`'s `ExecuteReader()` method is invoked, all the data fetched by the `OracleDataReader` is from a particular snapshot. Therefore, calling an accessor method on the same column always returns the same value. However, the `GetOracleBlobForUpdate()` method incurs a database round-trip to obtain a reference to the current `BLOB` data while also locking the row using the `FOR` `UPDATE` clause. This means that the `OracleBlob` obtained from `GetOracleBlob()` can have a different value than the `OracleBlob` obtained from `GetOracleBlobForUpdate()` since it is not obtained from the original snapshot.

The returned `OracleBlob` object can be used to safely update the `BLOB` because the `BLOB` column has been locked after a call to this method.

Invoking this method internally executes a `SELECT..FOR UPDATE` statement without a `WAIT` clause. Therefore, the statement can wait indefinitely until a lock is acquired for that row.

`IsDBNull` should be called to check for `NULL` values before calling this method.

### Example

The following example gets the `OracleBlob` object for update from the reader, updates the `OracleBlob` object, and then commits the transaction.

    /* Database Setup, if you have not done so yet.
    connect scott/tiger@oracle
    CREATE TABLE empInfo (
    empno NUMBER(4) PRIMARY KEY,
    empName VARCHAR2(20) NOT NULL,
    hiredate DATE,
    salary NUMBER(7,2),
    jobDescription Clob,
    byteCodes BLOB
    );

    Insert into empInfo(EMPNO,EMPNAME,JOBDESCRIPTION,byteCodes) values
    (1,'KING','SOFTWARE ENGR', '5657');
    Insert into empInfo(EMPNO,EMPNAME,JOBDESCRIPTION,byteCodes) values
    (2,'SCOTT','MANAGER', '5960');
    commit;

    */
    // C#

    using System;
    using System.Data;
    using Oracle.DataAccess.Client;
    using Oracle.DataAccess.Types;

    class GetOracleBlobForUpdateSample
    {
      static void Main()
      {
        string constr = "User Id=scott;Password=tiger;Data Source=oracle";
        OracleConnection con = new OracleConnection(constr);
        con.Open();

        // Get the ByteCodes for empno = 1
        string cmdstr = "SELECT BYTECODES, EMPNO FROM EMPINFO where EMPNO = 1";
        OracleCommand cmd = new OracleCommand(cmdstr, con);

        // Since we are going to update the OracleBlob object, we will
        //have to create a transaction
        OracleTransaction txn = con.BeginTransaction();

        // Get the reader
        OracleDataReader reader = cmd.ExecuteReader();

        // Declare the variables to retrieve the data in EmpInfo
        OracleBlob byteCodesBlob;

        // Read the first row
        reader.Read();
        if (!reader.IsDBNull(0))
        {
          byteCodesBlob = reader.GetOracleBlobForUpdate(0);

          // Close the reader
          reader.Close();

          // Update the ByteCodes object
          byte[] addedBytes = new byte[2] {0, 0};
          byteCodesBlob.Append(addedBytes, 0, addedBytes.Length);

          // Now commit the transaction
          txn.Commit();
          Console.WriteLine("Blob Column successfully updated");
        }
        else
          reader.Dispose();

        // Close the connection
        con.Dispose();
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Class](OracleDataReaderClass.md)

- [OracleDataReader Members](DataReaderMembers.md)

- "[LOB Support](featLOBsupp.md)"
