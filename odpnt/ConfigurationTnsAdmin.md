This property specifies the `tnsnames.ora` and/or `sqlnet.ora` directory location.

### Declaration

    // C#
    public static string TnsAdmin { get; set; }

### Property Type

`System.String`

The backslash (\\ is a special character in .NET that represents the beginning of an escape sequence. To specify a directory location, use any one of the following formats in .NET so that backslashes are correctly represented in a directory location:

    // C#
    OracleConfiguration.TnsAdmin = "D:\\oracle\\client\\admin";
    OracleConfiguration.TnsAdmin = @"D:\oracle\client\admin";
    OracleConfiguration.TnsAdmin = "D:/oracle/client/admin";

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConfiguration Class](OracleConfigurationClass.md)

- [OracleConfiguration Members](OracleConfigurationMembers.md)
