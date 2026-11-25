This method returns schema information for the data source of the `OracleConnection`.

### Declaration

    // C#
    public override DataTable GetSchema();


### Return Value

A `DataTable` object.

### Exceptions

`InvalidOperationException` – The connection is closed.

### Remarks

This method returns a `DataTable` object that contains a row for each metadata collection available from the database.

The method is equivalent to specifying the String value `"MetaDataCollections"` when using the `GetSchema(String)` method.

### Example

    // C#

    using System;
    using System.Data;
    using System.Data.Common;
    using Oracle.DataAccess.Client;

    class GetSchemaSample
    {
      static void Main(string[] args)
      {
        string constr = "User Id=scott; Password=tiger; Data Source=oracle;";
        string ProviderName = "Oracle.DataAccess.Client";

        DbProviderFactory factory = DbProviderFactories.GetFactory(ProviderName);

        using (DbConnection conn = factory.CreateConnection())
        {
          try
          {
            conn.ConnectionString = constr;
            conn.Open();

            //Get all the schema collections and write to an XML file.
            //The XML file name is Oracle.DataAccess.Client_Schema.xml
            DataTable dtSchema = conn.GetSchema();
            dtSchema.WriteXml(ProviderName + "_Schema.xml");
          }
          catch (Exception ex)
          {
            Console.WriteLine(ex.Message);
            Console.WriteLine(ex.StackTrace);
          }
        }
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnection Class](OracleConnectionClass.md)

- [OracleConnection Members](ConnectionMembers.md)
