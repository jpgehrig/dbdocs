This instance method enables applications to set the sharding key and the super sharding key before requesting a connection.

### Declaration

    // C#
    public void SetShardingKey(OracleShardingKey shardKey, OracleShardingKey superShardingKey);

### Exceptions

`InvalidArgumentException` – An invalid Oracle sharding key is supplied.

`InvalidOperationException` – The method is invoked when the connection is in an `Open` state.

### Remarks

This method sets the sharding key and the super sharding key that is to be used for returning the proper connection upon the `Open` method invocation.

This method can only be invoked when the connection is in a `Closed` state.

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

- [OracleConnection Class](OracleConnectionClass.md)

- [OracleConnection Members](ConnectionMembers.md)

- [OracleShardingKey Class](OracleShardingKeyClass.md)
