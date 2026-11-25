Lists the sharding functions.

The following table lists the sharding OCI functions that are described in this section.

Table 26-7 Sharding Functions

| Function                  | Purpose                                                                                                           |
|:--------------------------|:------------------------------------------------------------------------------------------------------------------|
| OCIShardingKeyColumnAdd() | Adds sharding key columns to form a compound sharding key or a compound super sharding key.                       |
| OCIShardingKeyReset()     | Resets an already created sharding key or super sharding key for reuse with new key column values.                |
| OCIShardInstancesGet()    | Returns instance names for a given sharding key descriptor, super sharding key descriptor, and connection string. |

### 26.8.1 OCIShardingKeyColumnAdd()

Adds sharding key columns to form a compound sharding key or a compound super sharding key.

#### Purpose

Adds sharding key columns to form a compound sharding key or a compound super sharding key. A sharding key column is a column in a table that is used as the key. If there are multiple columns to be used as the key then it is a compound key.

#### Syntax

    sword OCIShardingKeyColumnAdd(OCIShardingKey   *shardingKey,
                                  OCIError         *errhp,
                                  void             *col,
                                  ub4               colLen,
                                  ub2               colType,
                                  ub4               mode);

#### Parameters

shardingKey (IN)
The sharding key or super sharding key.

errhp (IN/OUT)
An error handle that you can pass to `OCIErrorGet()` for diagnostic information in the event of an error.

col (IN)
The sharding key column, a component of the compound key. For character strings, the values are assumed to be in the client character set (specified by `NLS_LANG` or the `OCIEnvNLSCreate()` call).

colLen (IN)
Length of the sharding key column.

colType (IN)
The data type of the column.

mode (IN)
`OCI_DEFAULT` is the only value supported.

#### Returns

`OCI_SUCCESS` or `OCI_ERROR`

#### Usage Notes

Users must allocate an `OCIShardingKey` descriptor.

Call `OCIShardingKeyColumnAdd()` as many times as there are columns in the compound key (one time for a simple sharding key), in the order in which the key is defined in the database. The `colType` variable indicates the data type of the column.

The following table shows the supported OCI data type values for the `colType` parameter and its corresponding C data type.

| OCI Data Type  | C Data Type   |
|:---------------|:--------------|
| SQLT_NUM       | ub1\*         |
| SQLT_CHR       | OraText\*     |
| SQLT_DATE      | ub1\*         |
| SQLT_TIMESTAMP | OCIDateTime\* |
| SQLT_RAW       | ub1\*         |
| SQLT_VNU       | ub1\*         |
| SQLT_INT       | int\*         |

#### Examples

Example 26-1 Creating a Compound Sharding Key

Use the` OCIShardingKey` descriptor for the sharding key, then allocate a descriptor and call `OCIShardingKeyColumnAdd()` as many times as needed to create the compound sharding key.

    OCIShardingKey   *shardKey;
    text *name = “KK”;
    int  empid = 150;

    checker(&status, errhp, OCIDescriptorAlloc(envhp,(dvoid **)&shardKey,
               OCI_DTYPE_SHARDING_KEY, 0,(dvoid **)0)));

    /* construct a compound key */

    OCIShardingKeyColumnAdd(shardKey, OCIError *errhp,(ub4*)&empid, sizeof(empid),
                         SQLT_INT, OCI_DEFAULT);
    OCIShardingKeyColumnAdd(shardKey, OCIError *errhp, name, strlen(name),
                         SQLT_CHR, OCI_DEFAULT));

**Related Topics**

- [OCIDescriptorAlloc()](handle-and-descriptor-functions.md)
- [OCISessionPoolCreate()](connect-authorize-and-initialize-functions.md)

### 26.8.2 OCIShardingKeyReset()

Resets an already created sharding key or super sharding key for reuse with new key column values.

#### Purpose

A sharding key or super sharding key descriptor can be reset using this routine, which removes all the key column values added prior to this call. After this call, the descriptor can be used to set new key column values.

#### Syntax

    sword OCIShardingKeyReset(OCIShardKey *shardKey,
                              OCIError    *errhp,
                              ub4          mode);

#### Parameters

shardKey(IN)
The sharding key or super sharding key descriptor.

errhp (IN/OUT)
An error handle you can pass to `OCIErrorGet()` for diagnostic information in the event of an error.

mode (IN)
`OCI_DEFAULT` is the only value currently supported.

#### Returns

`OCI_SUCCESS` or `OCI_ERROR`

#### Usage Notes

None.

**Related Topics**

- [OCIAttrSet()](handle-and-descriptor-functions.md)
- [OCIAttrGet()](handle-and-descriptor-functions.md)

### 26.8.3 OCIShardInstancesGet()

For use with custom pools only, gets the instance names given a sharding key descriptor, super sharding key descriptor, and a connection string.

#### Purpose

For use with custom pools only, returns instance names for a given sharding key descriptor for a chunk and super sharding key descriptor for a group of chunks and a connection string. Shards are locations in a set of databases where each database stores some part of the data. The part of the data stored at each database is represented by a set of chunks, where each chunk is associated with a certain range of the data.

#### Syntax

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

#### Parameters

shTopoCtx(IN/OUT)
An opaque context that is created by OCI and returned in the first call to this method for a given connect string. This is an optional parameter and can be passed as `NULL`. For better performance, pass the `void * shardTopoCtx` returned from a prior call (if any) to `OCIShardInstancesGet()` for the same connection string.

errhp (IN/OUT)
An error handle you can pass to `OCIErrorGet()` for diagnostic information in the event of an error.

connstr (IN)
The original connect string passed by the application to the `OCISessionGet()` call.

connstrl(IN)
Length of the `connstr` parameter.

shardingKey (IN)
The sharding key for the desired chunk.

superShardingKey (IN)
The super sharding key for the desired chunk; this value can be NULL.

shardInsts(OUT)
An array of `OCIShardInst` descriptors corresponding to instances that serve the chunk associated with the sharding key and super sharding key.

numShardInsts(OUT)
The number of elements in `shardInsts`.

mode(IN)
`OCI_DEFAULT` is the only value supported.

#### Returns

`OCI_SUCCESS` or `OCI_ERROR`

#### Usage Notes

None.

#### Examples

Example 26-2 Custom Pool Example

This example uses a custom pool and illustrates how to get the instance name of a given connection and how to look up for instances hosting a given sharding key, shard name, and super sharding name for a given connection. If there is no matching connection in the custom pool, it creates a new connection.

        OCIShardInstancesGet(           
                           &shTopoCtx,
                           errhp,
                           connstr,
                           strlen(connstrl),
                                shardingKey,
                           superShardingKey,
                           &shardInsts,
                           &numShardInsts,
                           OCI_DEFAULT);    

     /* Iterate through all the shard instances that have the data satisfying the sharding key. */
       
       for (k=0; k < numShardInsts; k++ )     
       {      
         OCIAttrGet(shardInstances[k],            
                   (ub4) OCI_DTYPE_SHARD_INST,
                   (dvoid *)&iName,
                   (ub4 *)&inameLen,           
                    OCI_ATTR_INSTNAME,
                   (OCIError *)errhp);
            
    /* Look up in the custom pool for a connection to the same shard instance. */      
    /* The following attribute can be used to find the instance name. */             

       OCIAttrGet(svchp[i],
                  OCI_HTYPE_SVCCTX,
                  &cshardName[i],
                  (ub4 *) &cshardNameLen[i],                   
                  OCI_ATTR_INSTNAME, errhp);        

    /* If a matching connection is found (iName and cshardName[i]). */  
        
        {          
         OCIAttrSet(svchp[i],
                   OCI_HTYPE_SVCCTX,
                   shardingKey,
                   sizeof(shardingKey),               
                   OCI_ATTR_SHARDING_KEY,
                   errhp);           

    /* Return that connection to the requester. */           
        return svchp[i];          
       }      
      }     

    /* If no free existing connection is found, create a new connection in the pool and return it. */    
      {        
       OCIAttrSet(authp,
                  OCI_HTYPE_AUTHINFO,
                  shardingKey,
                  sizeof(shardingKey),
                  OCI_ATTR_SHARDING_KEY,
                  errhp);
            
       OCISessionGet ((OCIEnv *)envhp,             
                      (OCIError *)errhp,
                      (OCISvcCtx **)&mysvc,             
                      (OCIAuthInfo *)authp,
                      (OraText *)connstr,             
                      (ub4)strlen((char*)connstrl),
                      (OraText *)NULL, (ub4)0,             
                      (OraText **)0, (ub4 *)0,
                      (boolean *)0,OCI_SESSGET_CUSTOM_POOL);        
       return mysvc; /* Track in the pool too. */     
      }

**Related Topics**

- [OCIAttrSet()](handle-and-descriptor-functions.md)
- [OCIAttrGet()](handle-and-descriptor-functions.md)
- [OCISessionGet()](connect-authorize-and-initialize-functions.md)
