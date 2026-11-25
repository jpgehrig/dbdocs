This method returns schema information for the data source of the `OracleConnection` using the specified string for the collection name.

### Declaration

    // C#
    public override DataTable GetSchema (string collectionName);

### Parameters

`collectionName`

Name of the collection for which metadata is required.

### Return Value

A `DataTable` object.

### Exceptions

`ArgumentException` – The requested collection is not defined.

`InvalidOperationException` – The connection is closed.

`InvalidOperationException` – The requested collection is not supported by current version of Oracle database.

`InvalidOperationException` – No population string is specified for requested collection.

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

            //Get MetaDataCollections and write to an XML file.
            //This is equivalent to GetSchema()
            DataTable dtMetadata =
              conn.GetSchema(DbMetaDataCollectionNames.MetaDataCollections);
            dtMetadata.WriteXml(ProviderName + "_MetaDataCollections.xml");

            //Get Restrictions and write to an XML file.
            DataTable dtRestrictions =
              conn.GetSchema(DbMetaDataCollectionNames.Restrictions);
            dtRestrictions.WriteXml(ProviderName + "_Restrictions.xml");

            //Get DataSourceInformation and write to an XML file.
            DataTable dtDataSrcInfo =
              conn.GetSchema(DbMetaDataCollectionNames.DataSourceInformation);
            dtDataSrcInfo.WriteXml(ProviderName + "_DataSourceInformation.xml");

            //data types and write to an XML file.
            DataTable dtDataTypes =
              conn.GetSchema(DbMetaDataCollectionNames.DataTypes);
            dtDataTypes.WriteXml(ProviderName + "_DataTypes.xml");

            //Get ReservedWords and write to an XML file.
            DataTable dtReservedWords =
              conn.GetSchema(DbMetaDataCollectionNames.ReservedWords);
            dtReservedWords.WriteXml(ProviderName + "_ReservedWords.xml");

            //Get all the tables and write to an XML file.
            DataTable dtTables = conn.GetSchema("Tables");
            dtTables.WriteXml(ProviderName + "_Tables.xml");

            //Get all the views and write to an XML file.
            DataTable dtViews = conn.GetSchema("Views");
            dtViews.WriteXml(ProviderName + "_Views.xml");

            //Get all the columns and write to an XML file.
            DataTable dtColumns = conn.GetSchema("Columns");
            dtColumns.WriteXml(ProviderName + "_Columns.xml");
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
