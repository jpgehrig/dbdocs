An `OracleShardingKey` object can represent either a sharding key or a super sharding key.

### Class Inheritance

`System.Object`

`   Oracle.DataAccess.Client.OracleShardingKey`

### Declaration

    // C#
    public class OracleShardingKey : IDisposable

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  |
|:---------------|:---------------------------|
| Assembly       | `Oracle.DataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         |

### Example

    // C#

    using System;
    using Oracle.DataAccess.Client;

    class Sharding
    {
      static void Main()
      {
        OracleConnection con = new OracleConnection("user id=hr;password=hr;Data Source=orcl;");
        //Setting a shard key
        OracleShardingKey shardingKey = new OracleShardingKey(OracleDbType.Int32, 123);
        //Setting a second shard key value for a composite key
        shardingKey.SetShardingKey(OracleDbType.Varchar2, "gold");
        //Creating and setting the super shard key
        OracleShardingKey superShardingKey = new OracleShardingKey();
        superShardingKey.SetShardingKey(OracleDbType.Int32, 1000);

        //Setting super sharding key and sharding key on the connection
        con.SetShardingKey(shardingKey, superShardingKey);
        con.Open();

        //perform SQL query
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleShardingKey Members](OracleShardingKeyMembers.md)

- [OracleShardingKey Constructors](OracleShardingKeyCtors.md)

- [OracleShardingKey Instance Methods](ShardingKeyInstanceMethods.md)
