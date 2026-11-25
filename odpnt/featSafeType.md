The ODP.NET `OracleDataAdapter` class provides the Safe Type Mapping feature to ensure that the following Oracle data types do not lose data when converted to their closely related .NET types in the `DataSet`:

- `NUMBER`

- `DATE`

- `TimeStamp` (refers to all `TimeStamp` objects)

- `INTERVAL` `DAY` `TO` `SECOND`

**Note:**

ODP.NET, Managed Driver and ODP.NET do not support Safe Type Mapping.

This section includes the following topics:

- Comparison Between Oracle Data Types and .NET Types

- SafeMapping Property

### Comparison Between Oracle Data Types and .NET Types

The following sections provide more details about the differences between the Oracle data types and the corresponding .NET types. In general, the Oracle data types allow a greater degree of precision than the .NET types do.

#### Oracle NUMBER Type to .NET Decimal Type

The Oracle data type `NUMBER` can hold up to 38 precision, and the .NET `Decimal` type can hold up to 28 precision. If a `NUMBER` data type that has more than 28 precision is retrieved into a .NET `Decimal` type, it loses precision.

Table 3-28 lists the maximum and minimum values for Oracle `NUMBER` and .NET `Decimal` types.

Table 3-28 Oracle NUMBER to .NET Decimal Comparisons

| Value Limits | Oracle NUMBER                                 | .NET Decimal                            |
|:-------------|:----------------------------------------------|:----------------------------------------|
| Maximum      | 9.9999999999999999999999999999999999999 e125  | 79,228,162,514,264,337,593,543,950,335  |
| Minimum      | -9.9999999999999999999999999999999999999 e125 | -79,228,162,514,264,337,593,543,950,335 |

#### Oracle Date Type to .NET DateTime Type

The Oracle data type `DATE` can represent dates in BC whereas the .NET `DateTime` type cannot. If a `DATE` that goes to BC get retrieved into a .NET `DateTime` type, it loses data.

Table 3-29 lists the maximum and minimum values for Oracle `Date` and .NET `DateTime` types.

Table 3-29 Oracle Date to .NET DateTime Comparisons

| Value Limits | Oracle Date     | .NET DateTime                    |
|:-------------|:----------------|:---------------------------------|
| Maximum      | Dec 31, 9999 AD | Dec 31, 9999 AD 23:59:59.9999999 |
| Minimum      | Jan 1, 4712 BC  | Jan 1, 0001 AD 00:00:00.0000000  |

#### Oracle TimeStamp Type to .NET DateTime Type

Similar to the `DATE` data type, the Oracle `TimeStamp` data type can represent a date in BC, and a .NET `DateTime` type cannot. If a `TimeStamp` that goes to BC is retrieved into a.NET `DateTime` type, it loses data. The Oracle `TimeStamp` type can represent values in units of e-9; the .NET `DateTime` type can represent only values in units of e-7. The Oracle `TimeStamp` with time zone data type can store time zone information, and the .NET `DateTime` type cannot.

Table 3-30 lists the maximum and minimum values for Oracle `TimeStamp` and .NET `DateTime` types.

Table 3-30 Oracle TimeStamp to .NET DateTime Comparisons

| Value Limits | Oracle TimeStamp                   | .NET DateTime                    |
|:-------------|:-----------------------------------|:---------------------------------|
| Maximum      | Dec 31, 9999 AD 23:59:59.999999999 | Dec 31, 9999 AD 23:59:59.9999999 |
| Minimum      | Jan 1, 4712 BC 00:00:00.000000000  | Jan 1, 0001 AD 00:00:00.0000000  |

#### Oracle INTERVAL DAY TO SECOND to .NET TimeSpan

The Oracle data type `INTERVAL` `DAY` `TO` `SECOND` can hold up to 9 precision, and the .NET TimeSpan type can hold up to 7 precision. If an `INTERVAL` `DAY` `TO` `SECOND` data type that has more than 7 precision is retrieved into a .NET TimeSpan type, it loses precision. The Oracle `INTERVAL` `DAY` `TO` `SECOND` type can represent values in units of e-9, and the .NET `TimeSpan` type can represent only values in units of e-7.

Table 3-31 lists the maximum and minimum values for Oracle `INTERVAL` `DAY` `TO` `SECOND` and .NET `DateTime` types.

Table 3-31 Oracle INTERVAL DAY TO SECOND to .NET TimeSpan Comparisons

| Value Limits | Oracle INTERVAL DAY TO SECOND | .NET TmeSpan               |
|:-------------|:------------------------------|:---------------------------|
| Maximum      | +999999999 23:59:59.999999999 | +10675199 02:48:05.4775807 |
| Minimum      | -999999999 23:59:59.999999999 | -10675199 02:48:05.4775808 |

### SafeMapping Property

The `OracleDataAdapter` Safe Type Mapping feature prevents data loss when populating Oracle data for any of these types into a .NET `DataSet`. By setting the `SafeMapping` property appropriately, these types can be safely represented in the `DataSet`, as either of the following:

- .NET `byte[]` in Oracle format

- .NET `String`

By default, Safe Type Mapping is disabled.

#### Using Safe Type Mapping

To use the Safe Type Mapping feature, the `OracleDataAdapter`.`SafeMapping` property must be set with a hash table of key-value pairs. The key-value pairs must map database table column names (of type `string`) to a .NET type (of type `Type`). ODP.NET supports Safe Type Mapping to `byte[]` and `String` types. Any other type mapping causes an exception.

In situations where the column names are not known at design time, an asterisk ("\*") can be used to map all occurrences of database types to a safe .NET type. If both the valid column name and the asterisk are present, the column name is used.

**Note:**

- Database table column names are case-sensitive.

- Column names in the hash table that correspond to invalid column names are ignored.

Safe Type Mapping as a string is more readable without further conversion. Converting certain Oracle data types to a string requires extra conversion, which can be slower than converting it to a `byte[]`. Conversion of .NET strings back to ODP.NET types relies on the formatting information of the session.

##### SafeTyping Example

    // C#

    using System;
    using System.Data;
    using Oracle.DataAccess.Client;

    class SafeMappingSample
    {
      static void Main()
      {
        string constr = "User Id=scott;Password=tiger;Data Source=oracle";

        // In this SELECT statement, EMPNO, HIREDATE and SALARY must be
        // preserved using safe type mapping.
        string cmdstr = "SELECT EMPNO, ENAME, HIREDATE, SAL FROM EMP";

        // Create the adapter with the selectCommand txt and the connection string
        OracleDataAdapter adapter = new OracleDataAdapter(cmdstr, constr);

        // Get the connection from the adapter
        OracleConnection connection = adapter.SelectCommand.Connection;

        // Create the safe type mapping for the adapter
        // which can safely map column data to byte arrays, where
        // applicable. By executing the following statement, EMPNO, HIREDATE AND
        // SALARY columns will be mapped to byte[]
        adapter.SafeMapping.Add("*", typeof(byte[]));

        // Map HIREDATE to a string
        // If the column name in the EMP table is case-sensitive,
        // the safe type mapping column name must be case-sensitive.
        adapter.SafeMapping.Add("HIREDATE", typeof(string));

        // Map EMPNO to a string
        // If the column name in the EMP table is case-sensitive,
        // the safe type mapping column name must also be case-sensitive.
        adapter.SafeMapping.Add("EMPNO", typeof(string));
        adapter.SafeMapping.Add("SAL", typeof(string));

        // Create and fill the DataSet using the EMP
        DataSet dataset = new DataSet();
        adapter.Fill(dataset, "EMP");

        // Get the EMP table from the dataset
        DataTable table = dataset.Tables["EMP"];

        // Get the first row from the EMP table
        DataRow row = table.Rows[0];

        // Print out the row info
        Console.WriteLine("EMPNO Column: type = " + row["EMPNO"].GetType() +
          "; value = " + row["EMPNO"]);
        Console.WriteLine("ENAME Column: type = " + row["ENAME"].GetType() +
          "; value = " + row["ENAME"]);
        Console.WriteLine("HIREDATE Column: type = " + row["HIREDATE"].GetType()+
          "; value = " + row["HIREDATE"]);
        Console.WriteLine("SAL Column: type = " + row["SAL"].GetType() +
          "; value = " + row["SAL"]);
      }
    }

**See Also:**

"[SafeMapping](DataAdapterSafeMapping.md)"
