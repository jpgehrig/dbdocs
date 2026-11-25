An `OracleDataReader` object represents a forward-only, read-only, in-memory result set.

Unlike the `DataSet`, the `OracleDataReader` object stays connected and fetches one row at a time.

The following section contain related information:

- "[Obtaining LONG and LONG RAW Data](featData.md)".

- "[Obtaining Data from an OracleDataReader Object](featData.md)".

### Class Inheritance

`System.Object`

`  System.MarshalByRefObject`

`    System.Data.Common.DataReader`

`      System.Data.Common.DbDataReader`

`        Oracle.DataAccess.Client.OracleDataReader`

### Declaration

    // C#
    public sealed class OracleDataReader : DbDataReader, IEnumerable,
       IDataReader, IDisposable, IDataRecord

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  | ODP.NET, Managed Driver           | ODP.NET Core                      |
|:---------------|:---------------------------|:----------------------------------|:----------------------------------|
| Assembly       | `Oracle.DataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` | `Oracle.ManagedDataAccess.Client` | `Oracle.ManagedDataAccess.Client` |
| .NET Framework | 4.5, 4.6, 4.7              | 4.5, 4.6, 4.7                     | 4.6.1 or higher                   |
| .NET Core      | \-                         | \-                                | 2.1 or higher                     |

### Thread Safety

All public static methods are thread-safe, although instance methods do not guarantee thread safety.

### Remarks

An `OracleDataReader` instance is constructed by a call to the `ExecuteReader` method of the `OracleCommand` object. The only properties that can be accessed after the `DataReader` is closed or has been disposed, are `IsClosed` and `RecordsAffected`.

To minimize the number of open database cursors, `OracleDataReader` objects should be explicitly disposed.

### Example

The following `OracleDataReader` example retrieves the data from the `EMP` table:

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

    class OracleDataReaderSample
    {
      static void Main()
      {
        string constr = "User Id=scott;Password=tiger;Data Source=oracle";
        OracleConnection con = new OracleConnection(constr);
        con.Open();

        string cmdstr = "SELECT * FROM EMPINFO";
        OracleConnection connection = new OracleConnection(constr);
        OracleCommand cmd = new OracleCommand(cmdstr, con);

        OracleDataReader reader = cmd.ExecuteReader();

        // Declare the variables to retrieve the data in EmpInfo
        short empNo;
        string empName;
        DateTime hireDate;
        double salary;
        string jobDesc;
        byte[] byteCodes = new byte[10];

        // Read the next row until end of row
        while (reader.Read())
        {
          empNo = reader.GetInt16(0);
          Console.WriteLine("Employee number: " + empNo);
          empName = reader.GetString(1);
          Console.WriteLine("Employee name: " + empName);

          // The following columns can have NULL value, so it
          //   is important to call IsDBNull before getting the column data
          if (!reader.IsDBNull(2))
          {
            hireDate = reader.GetDateTime(2);
            Console.WriteLine("Hire date: " + hireDate);
          }

          if (!reader.IsDBNull(3))
          {
            salary = reader.GetDouble(3);
            Console.WriteLine("Salary: " + salary);
          }

          if (!reader.IsDBNull(4))
          {
            jobDesc = reader.GetString(4);
            Console.WriteLine("Job Description: " + jobDesc);
          }

          if (!reader.IsDBNull(5))
          {
            long len = reader.GetBytes(5, 0, byteCodes, 0, 10);

            Console.Write("Byte codes: ");
            for (int i = 0; i < len; i++)
              Console.Write(byteCodes[i].ToString("x"));

            Console.WriteLine();
          }

          Console.WriteLine();
        }

        // Clean up
        reader.Dispose();
        con.Dispose();
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataReader Members](DataReaderMembers.md)

- [OracleDataReader Static Methods](DataReaderStaticMethods.md)

- [OracleDataReader Properties](DataReaderProperties.md)

- [OracleDataReader Public Methods](DataReaderPublicMethods.md)
