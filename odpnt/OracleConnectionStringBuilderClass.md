An `OracleConnectionStringBuilder` object allows applications to create or modify connection strings.

### Class Inheritance

`System.Object`

`  System.Data.Common.DbConnectionStringBuilder`

`    Oracle.DataAccess.Client.OracleConnectionStringBuilder`

### Declaration

    // C#
    public sealed class OracleConnectionStringBuilder : DbConnectionStringBuilder

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

The following rules must be followed for setting values with reserved characters:

1.  Values containing characters enclosed within single quotes

    If the value contains characters that are enclosed within single quotation marks, then the entire value must be enclosed within double quotation marks.

    For example, `password =` `"'scoTT'"` where the value is `'scoTT'`.

2.  Values containing characters enclosed within double quotes

    Values should be enclosed in double quotation marks to preserve the case and to avoid the upper casing of values.

    If the value contains characters enclosed in double quotation marks, then it must be enclosed in single quotation marks.

    For example, `password =` '`"scoTT"'` where the value is `"scoTT"`.

3.  Values containing characters enclosed in both single and double quotes

    If the value contains characters enclosed in both single and double quotation marks, the quotation mark used to enclose the value must be doubled each time it occurs within the value.

    For example, `password = ``'"sco''TT"'` where the value is `"sco'TT"`.

4.  Values containing spaces

    All leading and trailing spaces are ignored, but the spaces between the value are recognized. If the value needs to have leading or trailing spaces then it must be enclosed in double quotation marks.

    For example, `User ID =` `Sco` `TT` where the value is `<Sco` `TT>`.

    For example, `User ID =` `"Sco` `TT "` where the value is `<Sco` `TT>`.

5.  Keywords occurring multiple times in a connection string

    If a specific keyword occurs multiple times in a connection string, the last occurrence listed is used in the value set.

    For example, with `"User ID = scott; password = tiger; User ID = david"` connection string, `User ID` value is `david`.

To limit malicious access, the APIs of `OracleConnectionStringBuilder`, `Add` and `Item`, insert double quotes around connection string attributes that use special characters. Using special characters in strings can be a format string attack method. Adding double quotes for attributes will not affect database access in most cases. However, there are attributes that require exact string matching, such as passwords. `OracleConnectionStringBuilder`'s addition of double quotes to a password with special characters may result in a generation of a connection string that fails to authenticate against the database.

### Example

    // C#

    using System;
    using System.Data;
    using System.Data.Common;
    using Oracle.DataAccess.Client;
    using System.Collections;

    class ConnectionStringBuilderSample
    {
    static void Main(string[] args)
      {
        bool bRet = false;

        // Create an instance of OracleConnectionStringBuilder
        OracleConnectionStringBuilder connStrBuilder =
          new OracleConnectionStringBuilder();

        // Add new key/value pairs to the connection string
        connStrBuilder.Add("User Id", "scott");
        connStrBuilder.Add("Password", "tiger");
        connStrBuilder.Add("Data Source", "oracle");
        connStrBuilder.Add("pooling", false);

        // Modify the existing value
        connStrBuilder["Data source"] = "inst1";

        // Remove an entry from the connection string
        bRet = connStrBuilder.Remove("pooling");

        //ContainsKey indicates whether or not the specific key exist
        //returns true even if the user has not specified it explicitly
        Console.WriteLine("Enlist exist: " +
                  connStrBuilder.ContainsKey("Enlist"));

        //returns false
        connStrBuilder.ContainsKey("Invalid");

        // ShouldSerialize indicates whether or not a specific key
        // exists in connection string inherited from DbConnectionStringBuilder.
        // returns true if the key is explicitly added the user otherwise false;
        // this will return false as this key doesn't exists.
        connStrBuilder.ShouldSerialize("user");

        // returns false because this key is nott added by user explicitly.
        connStrBuilder.ShouldSerialize("Enlist");

        // IsFixedSize [read-only property]
        Console.WriteLine("Connection String is fixed size only: "
                                + connStrBuilder.IsFixedSize);
        Console.WriteLine("Key/Value Pair Count: " + connStrBuilder.Count);

        //adding a new key which is not supported by the provider
        //is not allowed.
        try
        {
          //this will throw an exception.
          connStrBuilder.Add("NewKey", "newValue");
        }
        catch (Exception ex)
        {
          Console.WriteLine(ex.Message);
        }

        Console.WriteLine("Key/Value Pair Count: " + connStrBuilder.Count);

        //modifying a existing key is allowed.
        connStrBuilder.Add("Enlist", false);
        Console.WriteLine("Key/Value Pair Count: " + connStrBuilder.Count);

        // Get all the keys and values supported by the provider.
        ICollection keyCollection = connStrBuilder.Keys;
        ICollection valueCollection = connStrBuilder.Values;

        IEnumerator keys = keyCollection.GetEnumerator();
        IEnumerator values = valueCollection.GetEnumerator();

        while (keys.MoveNext())
        {
          values.MoveNext();
          Console.WriteLine("Key: {0}     Value: {1} \n"
            ,keys.Current ,values.Current);
        }
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnectionStringBuilder Members](OracleConnectionStringBuilderMembers.md)

- [OracleConnectionStringBuilder Constructors](ConnectionStringBuilderConstructors.md)

- [OracleConnectionStringBuilder Public Properties](ConnectionStringBuilderPublicProperties.md)

- [OracleConnectionStringBuilder Public Methods](ConnectionStringBuilderPublicMethods.md)
