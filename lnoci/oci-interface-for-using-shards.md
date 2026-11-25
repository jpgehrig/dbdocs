This chapter describes the OCI interface for using Oracle Sharding.

Shards are locations in a set of databases where each database stores some part of the data. The part of the data stored at each database is represented by a set of chunks, where each chunk is associated with a certain range of the data.

To make requests that read from or write to a chunk, your application must be routed to the appropriate database (shard) that stores that chunk during the connection initiation step. This routing is accomplished by using a data key. The data key enables routing to the specific chunk by specifying its sharding key or to a group of chunks by specifying its super sharding key. In order to get a connection to the correct shard containing the chunk you wish to operate on, you must specify a key in your application before getting a connection to a sharded Oracle database for either standalone connections or connections obtained from an OCI Session pool. For an OCI Session pool, you must specify a data key before you check out connections from the pool.

For OCI Session pools and stand alone connections, the steps to form sharding keys and shard group keys and get a session with an underlying connection include:

1.  Allocate the sharding key descriptor by calling `OCIDescriptorAlloc()` and specifying the descriptor type parameter as `OCI_DTYPE_SHARDING_KEY` to form the sharding key.

    1.  Add all of the columns of the sharding key by calling `OCIShardingKeyColumnAdd()` as many times as is needed to form the complete sharding key.

    2.  Call `OCIAttrSet()` and specify the `OCI_ATTR_SHARDING_KEY` attribute to set the sharding key on the authentication handle.

2.  Allocate the shard group key descriptor by calling `OCIDescriptorAlloc()` and specifying the descriptor type parameter as `OCI_DTYPE_SHARDING_KEY` to form the shard group key.

    1.  Add all of the group columns of the sharding key by calling `OCIShardingKeyColumnAdd()` as many times as is needed to form the complete shard group key.

    2.  Call `OCIAttrSet()` and specify the `OCI_ATTR_SUPER_SHARDING_KEY` attribute to set the shard group key on the authentication handle.

3.  Call `OCISessionGet()` using the initialized authentication handle from the previous step containing the sharding key and shard group key information to get the database connection to the shard and chunk specified by the sharding key and group of chunks as specified by the shard group key.

For custom pools, the steps to form sharding keys and shard group keys and check out a connection from the pool include:

1.  If there are no existing connections in your custom pool, go directly to Step 7. Otherwise, do the following steps.

2.  Allocate the sharding key descriptor by calling `OCIDescriptorAlloc()` and specifying the descriptor type parameter as `OCI_DTYPE_SHARDING_KEY` to form the sharding key. Add all of the columns of the sharding key by calling `OCIShardingKeyColumnAdd()` as many times as is needed to form the complete sharding key.

3.  Allocate the shard group key descriptor by calling `OCIDescriptorAlloc()` and specifying the descriptor type parameter as `OCI_DTYPE_SHARDING_KEY` to form the shard group key. Add all of the group columns of the sharding key by calling `OCIShardingKeyColumnAdd()` as many times as is needed to form the complete shard group key.

4.  Call `OCIShardInstancesGet()` with the sharding key, super sharding key descriptors and the connect string to return the instance name or names that contain the desired chunk for the specified sharding key descriptor and super sharding key descriptor.

5.  Examine each connection in the custom pool to see if it points to one of the instances whose name was returned by `OCIShardInstancesGet()`. To check the instance that a connection in your custom pool points to, you can get the instance name using `OCI_ATTR_INSTNAME` on the service context handle (`OCISvcCtx *`).

6.  If you find a suitable connection in your custom pool that points to one of the desired instances, then call `OCIAttrSet()` to associate the sharding key and super sharding key with that connection. Now the connection is ready for executing your application's OCI calls on the desired shard. You can skip Step 7. If you do not find a suitable connection in your custom pool that points to the desired instance, continue to Step 7.

7.  If there is no matching connection found, create a new connection with the sharding key, super sharding key, and connect string and call `OCISessionGet()` and specify the `OCI_SESSGET_CUSTOM_POOL` mode to explicitly cache the shard topology that contains the shard to chunking mapping information. Now you have a connection to the desired shard. Now the connection is ready for executing your application's OCI calls on the desired shard.

Providing the sharding key or a super sharding key to OCI enables it to get a connection to the desired shard. As previously noted, these keys must be specified before getting a standalone connection to the database, or before checking out a connection from the OCI Session pool so that an appropriate connection to the desired shard can be returned.

In the case of custom pools, when the pool is empty, the custom pool implementer can use the steps as described above to first create standalone connections to the desired shards by providing the sharding key and super sharding key (with `OCI_SESSGET_CUSTOM_POOL` mode) to populate the custom pool, and secondly, for subsequent requests for connections to specific shards, use the `OCIShardInstancesGet()` call as described in conjunction with `OCIAttrGet()` of `OCI_ATTR_INSTNAME` to determine if an existing connection to the desired shard already exists in the custom pool, and if it does, then the connection can be reused.

The section describes the OCI interfaces that:

- Create a sharding key and a super sharding key using OCI data types.

- Create a connection specifying a sharding key and a super sharding key.

- Specify the sharding key and super sharding key to the connection request from an OCI session pool.

- Use custom connection pooling to get the shard name for a given connection and to get the shard name and the chunk name, given a sharding key and super sharding key.

### About Specifying a Sharding Key and Super Sharding Keys for a Standalone Connection

Use the `OCISessionGet()` call for creating the connection. This call takes an authentication handle, `authp`, as input, on which various properties are set, including the two attributes to support creating connections to specific shards: `OCI_ATTR_SHARDING_KEY` for the sharding key and `OCI_ATTR_SUPER_SHARDING_KEY` for the super sharding key.

### About Creating a Sharding Key and Super Sharding Key

Use the OCI descriptor type `OCIShardingKey` for forming the sharding key and the super sharding key. This descriptor wraps the key value (for a single part key) or multiple values (for a compounded key).

Use the following `OCIShardingKeyColumnAdd()` call to add all of the columns of the key to form the complete key.

    OCIShardingKeyColumnAdd(OCIShardingKey *shardingKey,
                         OCIError    *errhp,
                         void        *col,
                         ub4          colLen,
                         ub2          colType,
                         ub4          mode)

You should perform this call as many times as there are columns in the compound key (or just once for a simple sharding key) in the order in which the key is defined in the database. The `columnType` parameter indicates the data type of the column.

The following table shows the supported OCI data type values for the `columnType` parameter and its corresponding C data type.

| OCI Data Type  | C Data Type   |
|:---------------|:--------------|
| SQLT_NUM       | ub1\*         |
| SQLT_CHR       | OraText\*     |
| SQLT_DATE      | ub1\*         |
| SQLT_TIMESTAMP | OCIDateTime\* |
| SQLT_RAW       | ub1\*         |
| SQLT_VNU       | ub1\*         |
| SQLY_INT       | int\*         |

The character key values are assumed to be in the client character set (specified by `NLS_LANG` or `OCIEnvNLSCreate()` calls) .

After forming the sharding key and the super sharding key using the`OCIShardingKeyColumnAdd()` call, the keys can be set on the authentication handle using the sharding key attribute `OCI_ATTR_SHARDING_KEY` and the super sharding key attribute `OCI_ATTR_SUPER_SHARDING_KEY` as follows:

    OCIAttrSet(authp,
               OCI_HTYPE_AUTHINFO,
               shardKey,
               sizeof(shardKey),
               OCI_ATTR_SHARDING_KEY,
               errhp);

    OCIAttrSet(authp,
               OCI_HTYPE_AUTHINFO,
               shardGroupKey,
               sizeof(shardGroupKey),
               OCI_ATTR_SUPER_SHARDING_KEY,
               errhp);

When you use this `authp` parameter in an `OCISessionGet()` call, it will ensure that you create a connection to the shard containing the data corresponding to the sharding key and super sharding key values that are set.

### About Getting the Actual Sharding Key and Super Sharding Key Values

If you want to know the Base64 representation of the sharding key and super sharding key for diagnostic purposes, you can use the attribute `OCI_ATTR_SHARDING_KEY_B64`, on the `OCIShardingKey` descriptor. The `OCIAttrGet()` call takes the `OCIShardingKey` descriptor as input and returns the text value in base64 format of the sharding key and super sharding key.

    OCIAttrGet((dvoid *) OCIShardingKey,
       (ub4)             OCI_DTYPE_SHARDING_KEY,
       (dvoid *)         &sekyVale,
       (ub4*)            &skeyValueLen,
                         OCI_ATTR_SHARDING_KEY_B64,
       (OCIError *)      errhp);

In addition, you can use the `OCIShardingKeyReset()` call shown as follows for your application to reset and reuse the allocated descriptor for creating a new sharding key and super sharding key.

    sword OCIShardingKeyReset(OCIShardingKey *shardKey,
                              OCIError       *errhp,
                              ub4             mode);

This section includes the following topics:

- About Specifying a Sharding Key and Super Sharding Key for Getting a Connection from an OCI Session Pool

- About Specifying a Sharding Key and Super Sharding Key for Getting a Connection from a Custom Pool

**See Also:**

- [OCIShardingKeyColumnAdd()](shard-functions.md)

- [OCIShardingKeyReset()](shard-functions.md)

### 18.1 About Specifying a Sharding Key and Super Sharding Key for Getting a Connection from an OCI Session Pool

This topic describes how to specify a sharding key and super sharding key to get a connection from an OCI Session Pool.

By default, the `OCISessionGet()` call creates a new connection. You can also use this call to get an existing connection from an OCI Session pool. When you use the `OCI_ATTR_SHARDING_KEY` and `OCI_ATTR_SUPER_SHARDING_KEY` attribute settings, you can get a connection to the desired shard from an OCI Session pool. In an OCI Session pool, sessions in the pool can represent a variety of shards that are each authenticated by the database credentials passed in by the `OCISessionGet()` call using the initialized authentication handle `authp`.

The following example shows how to get a connection to the desired database shard from an OCI Session Pool created with the homogeneous and statement caching modes specified. Even though this example uses a homogeneous pool, you are not restricted to that type of pool.

    OCIShardingKey   *shardKey, *shardGroupKey;
      /* Error handling is omitted for brevity. */
      /* Create a homogeneous session pool. */
      checkerr(&status, errhp,
               OCISessionPoolCreate(envhp, errhp,
                     spoolhp,                                     /* session pool handle */
                    (OraText **) poolName, poolNameLenp,          /* returned poolname, length */
                    (const OraText *) connstr, strlen(connstr),   /* connect string */
                     min, max, increment,                         /* pool size constraints */
                    (OraText *) "hr", strlen((char *) "hr"),      /* username */
                    (OraText *) apppassword,                      /* password */
                     strlen((char *) apppassword),
                     OCI_SPC_HOMOGENEOUS|OCI_SPC_STMTCACHE));     /* modes */

    /* Allocate the sharding key and super sharding key descriptors. */
    OCIDescriptorAlloc(envhp,(dvoid **)&shardKey,
                   OCI_DTYPE_SHARDING_KEY, 0,(dvoid **)0)))
    text *name = “KK”;
    text *gname = “GOLD”;
    int  empid = 150;

    /* Add all the columns of the key to form the final sharding key. */
    OCIShardingKeyColumnAdd(shardKey,(ub1*)&empid, sizeof(empid),
                                   SQLT_INT, errhp, OCI_DEFAULT);
    OCIShardingKeyColumnAdd(shardKey, name, strlen(name),
                                   SQLT_CHAR, errhp, OCI_DEFAULT));

    OCIAttrSet(authp, OCI_HTYPE_AUTHINFO,
               shardKey, sizeof(shardKey),
               OCI_ATTR_SHARDING_KEY, errhp);

    /* Setting a shard group key. */
    /* Create a shard group key, in the same way as for a sharding key. */
    OCIDescriptorAlloc(envhp,(dvoid **)&shardGroupKey,
                       OCI_DTYPE_SHARDING_KEY, 0, (dvoid **)0));

    /* Add the column of the key to form the final super sharding key. */
    OCIShardingKeyColumnAdd(shardGroupKey, gname, strlen(gname),
                         SQLT_CHAR, errhp, OCI_DEFAULT));

    OCIAttrSet(authp, OCI_HTYPE_AUTHINFO,
               shardGroupKey, sizeof(shardGroupKey),
               OCI_ATTR_SUPER_SHARDING_KEY, errhp));

    /* Get the database connection from the OCI Session Pool. */
    checkerr(&status,
             errhp, OCISessionGet(envhp, errhp,
                    &svchp,                              /* returned database connection */
                    authp,                               /* initialized authentication handle */
                   (OraText *) poolName, poolNameLen,    /* connect string */
                    NULL, 0, NULL, NULL, NULL,           /* session tagging parameters: optional */
                    OCI_DEFAULT));                       /* modes */

#### Chunk Migrations and OCISessionGet() in Sharding

During chunk migrations, when a chunk migrates from one shard instance to another, OCI Session Pool can ensure that `OCISessionGet()` returns a connection to an instance having a writable chunk by implicitly doing retrials during chunk migration. This requires that a couple of properties be set:

- Setting `READONLY_CHUNK_OK` to `FALSE` in the connect string.

- Setting pool handle attributes: `OCI_ATTR_SPOOL_GETMODE` and `OCI_ATTR_SPOOL_WAIT_TIMEOUT` to `OCI_SPOOL_ATTRVAL_TIMEDWAIT` and a suitable time out value in milliseconds. If the pool is unable to get a connection to a writable instance within the time out period, `OCISessionGet()` returns an `ORA-24495` error.

If the application can use read only chunks, it can set `READONLY_CHUNK_OK=true` in the connect string. In that case a connection available to the instance with chunks marked read-only also may be dispensed. If the application attempts any database write operation on such a connection, it gets in return suitable errors.

### 18.2 About Specifying a Sharding Key and Super Sharding Key for Getting a Connection from a Custom Pool

This topic describes features that support specifying a sharding key and super sharding key to get a connection from a custom pool.

This section describes the following features that support applications specifying a sharding key and super sharding key for getting a connection from a custom pool:

- `OCISessionGet()` mode `OCI_SESSGET_CUSTOM_POOL` — Used to explicitly cache the shard topology every time OCI connects to a new shard instance.

- `OCIShardInstancesGet()` — Returns instance names for a given sharding key descriptor, super sharding key descriptor, and connection string.

#### OCI_ATTR_INSTNAME Attribute

If your OCI client application uses custom connection pooling, you must be able to return connections to specific shards. To do this, you must know the shard name to which shard a connection has been made and the sharding key and super sharding key to shard name mapping to enable a look up for a matching connection.

This is possible when you use the attribute `OCI_ATTR_INSTNAME` on the service context (`svchp`) for this purpose. This attribute returns the instance name for a given connection. The instance name is unique for the shard instance pointed to by a given connection. Every shard instance has a unique name. The following code sample shows how this attribute is used to get the instance name from a given service context `svchp`.

    OraText shardName[OCI_INSTNAME_MAXLEN];
    ub4 shardNameLen;
       OCIAttrGet(svchp,
       OCI_HTYPE_SVCCTX,
       shardName,
       (ub4 *) &shardNameLen,
       OCI_ATTR_INSTNAME,
       errhp);

#### OCISessionGet() mode OCI_SESSGET_CUSTOM_POOL

OCI clients that do custom pooling must use the `OCISessionGet()` mode `OCI_SESSGET_CUSTOM_POOL` to explicitly cache the shard topology that contains the shard to chunking mapping information every time OCI connects to a new shard not previously visited. OCI clients that do not use custom pooling do not need to use this mode as this caching is done implicitly, for example, when you use OCI Session Pools.

#### OCIShardInstancesGet()

`OCIShardInstancesGet()` returns instance names for a given sharding key descriptor and super sharding key descriptor. This method has the following signature:

    sword OCIShardInstancesGet(
               void            **shTopoCtx,
               OCIError         *errhp,
               const OraText    *connstr,
               ub4               constrl,
               OCIShardingKey   *shardingKey,
               OCIShardingKey   *superShardingKey,
               OCIShardinst   ***shardinsts,
               ub4               numShardInsts,
               ub4               mode);

This call looks up the shard topology cache on the client.

If any connections were made with `OCI_SESSGET_CUSTOM_POOL` mode, then OCI maintains the shard topology cache locally.

The returned value may be `NULL` if the shard topology cache does not yet have the mapping either because no connections were made with `OCI_SESSGET_CUSTOM_POOL` or the connections that were made so far with `OCI_SESSGET_CUSTOM_POOL` did not connect to a shard that contains the chunk for the sharding key and super sharding key requested. In either case, the custom pool should create a new connection explicitly using `OCISessionGet()` with the `OCI_ATTR_SHARDING_KEY` and `OCI_ATTR_SUPER_SHARDING_KEY` attributes set as applicable with `OCI_SESSGET_CUSTOM_POOL` mode enabled. Doing this adds information about the new shard to the OCI shard topology cache. Subsequent `OCIShardInstancesGet()` calls will look for key ranges belonging to chunks located in these shards and return these shard instance names.

Note that a sharding key and super sharding key may refer to multiple shards as a result of the chunk being replicated. When the custom pool has a connection to the desired shard, the custom pool should ensure that the `OCI_ATTR_SHARDING_KEY` and `OCI_ATTR_SUPER_SHARDING_KEY` properties are set on the connection before dispensing. Setting these properties ensures that the chunk usage is tracked on the database side and to determine if there have been any chunk splits occurring on the database.

**See Also:**

[OCIShardInstancesGet()](shard-functions.md) for an example that uses custom pooling
