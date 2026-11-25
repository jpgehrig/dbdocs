This method returns schema information for the data source of the `OracleConnection` using the specified string for the collection name and the specified string array for the restriction values.

### Declaration

    // C#
    public override DataTable GetSchema (string collectionName,
        string[] restrictions);


### Parameters

- `collectionName`

  The name of the collection of metadata being retrieved.

- `restrictions`

  An array of restrictions that apply to the metadata being retrieved.

### Return Value

A `DataTable` object.

### Exception

- `ArgumentException` – The requested collection is not defined.

- `InvalidOperationException` – One of the following conditions exist:

  - The connection is closed.

  - The requested collection is not supported by the current version of Oracle database.

  - More restrictions were provided than the requested collection supports.

  - No population string is specified for requested collection.

### Remarks

This method takes the name of a metadata collection and an array of String values that specify the restrictions for filtering the rows in the returned `DataTable`. This returns a `DataTable` that contains only rows from the specified metadata collection that match the specified restrictions.

For example, if the `Columns` collection has three restrictions (`owner`, `tablename`, and `columnname`), to retrieve all the columns for the `EMP` table regardless of schema, the `GetSchema` method must pass in at least these values: null, `EMP`.

If no restriction value is passed in, default values are used for that restriction, which is the same as passing in null. This differs from passing in an empty string for the parameter value. In this case, the empty string (`""`) is considered the value for the specified parameter.

`collectionName` is not case-sensitive, but restrictions (string values) are.

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

            //Get Restrictions
            DataTable dtRestrictions =
              conn.GetSchema(DbMetaDataCollectionNames.Restrictions);

            DataView dv = dtRestrictions.DefaultView;

            dv.RowFilter = "CollectionName = 'Columns'";
            dv.Sort = "RestrictionNumber";

            for (int i = 0; i < dv.Count; i++)
              Console.WriteLine("{0} (default) {1}" ,
                                dtRestrictions.Rows[i]["RestrictionName"],
                                dtRestrictions.Rows[i]["RestrictionDefault"]);

            //Set restriction string array
            string[] restrictions = new string[3];

            //Get all columns from all tables owned by "SCOTT"
            restrictions[0] = "SCOTT";
            DataTable dtAllScottCols = conn.GetSchema("Columns", restrictions);

            // clear collection
            for (int i = 0; i < 3; i++)
              restrictions[i] = null;

            //Get all columns from all tables named "EMP" owned by any
            //owner/schema
            restrictions[1] = "EMP";
            DataTable dtAllEmpCols = conn.GetSchema("Columns", restrictions);

            // clear collection
            for (int i = 0; i < 3; i++)
              restrictions[i] = null;

            //Get columns named "EMPNO" from tables named "EMP",
            //owned by any owner/schema
            restrictions[1] = "EMP";
            restrictions[2] = "EMPNO";
            DataTable dtAllScottEmpCols = conn.GetSchema("Columns", restrictions);

            // clear collection
            for (int i = 0; i < 3; i++)
              restrictions[i] = null;

            //Get columns named "EMPNO" from all
            //tables, owned by any owner/schema
            restrictions[2] = "EMPNO";
            DataTable dtAllEmpNoCols = conn.GetSchema("Columns", restrictions);
          }
          catch (Exception ex)
          {
            Console.WriteLine(ex.Message);
            Console.WriteLine(ex.Source);
          }
        }
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnection Class](OracleConnectionClass.md)

- [OracleConnection Members](ConnectionMembers.md)
