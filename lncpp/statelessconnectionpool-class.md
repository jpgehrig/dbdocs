This class represents a pool of stateless, authenticated connections to the database.

Table 13-41 Enumerated Values Used by StatelessConnectionPool Class

| Attribute     | Options                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|:--------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `PoolType`    | • `HETEROGENEOUS` is the default state; connections with different authentication contexts can be created in the same pool. This pool type also supports external authentication.<br>• `HOMOGENEOUS` indicates that all connections in the pool are authenticated with the username and password provided during pool creation. No proxy connections can be created. `minConn` and `incrConn` values are considered only in these `HOMOGENEOUS` pools.<br>• `NO_RLB` turns off run-time load balancing in the connection pool. Can be used with both `HETEROGENEOUS` and `HOMOGENEOUS` pools.<br>• `USES_EXT_AUTH` indicates that the connections in the pool support external authentication. Can only be used with `HETEROGENEOUS` pools. |
| `BusyOption`  | • `WAIT` indicates that the thread waits and blocks until the connection becomes free.<br>• `NOWAIT` throws and error.<br>• `FORCEGET` indicates that a new connection is created, even when maximum number of connections is opened and all are busy.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `DestroyMode` | • `DEFAULT` indicates that if are still active busy connections in the pool, `ORA24422` error is thrown<br>• `SPD_FORCE` indicates that any busy connections in the pool are forcefully terminated and the pool is destroyed; the user loses memory corresponding to the number of connections forcefully terminated.                                                                                                                                                                                                                                                                                                                                                                                                                       |

Table 13-42 Summary of StatelessConnectionPool Methods

| Method                        | Description                                                                                                                                                           |
|:------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| getAnyTaggedConnection()      | Returns a pointer to the connection object, without the restriction of a matching tag.                                                                                |
| getAnyTaggedProxyConnection() | Returns a proxy connection from a connection pool.                                                                                                                    |
| getBusyConnections()          | Returns the number of busy connections in the connection pool.                                                                                                        |
| getBusyOption()               | Returns the behavior of the stateless connection pool when all the connections in the pool are busy and the number of connections have reached maximum                |
| getConnection()               | Returns a pointer to the `Connection` object.                                                                                                                         |
| getIncrConnections()          | Returns the number of incremental connections in the connection pool.                                                                                                 |
| getMaxConnections()           | Returns the maximum number of connections in the connection pool.                                                                                                     |
| getMinConnections()           | Returns the minimum number of connections in the connection pool.                                                                                                     |
| getOpenConnections()          | Returns the number of open connections in the connection pool.                                                                                                        |
| getPoolName()                 | Returns the name of the connection pool.                                                                                                                              |
| getProxyConnection()          | Returns a proxy connection from a connection pool.                                                                                                                    |
| getTimeOut()                  | Returns the timeout period of a connection in the connection pool.                                                                                                    |
| releaseConnection()           | Releases the connection back to the pool with an optional tag.                                                                                                        |
| setBusyOption()               | Specifies the behavior of the stateless connection pool when:<br>• all the connections in the pool are busy, and<br>• the number of connections have reached maximum. |
| setPoolSize()                 | Sets the maximum, minimum, and incremental number of pooled connections for the connection pool.                                                                      |
| setTimeOut()                  | Sets the timeout period of a connection in the connection pool.                                                                                                       |
| terminateConnection()         | Closes the connection and remove it from the pool.                                                                                                                    |

### 13.29.1 getAnyTaggedConnection()

Returns a pointer to the connection object, without the restriction of a matching tag.

This method works in an environment with enabled database resident connection pooling.

During the execution of this call, the pool is first searched based on the tag provided. If a connection with the specified tag exists, it is returned to the user. If a matching connection is not available, an appropriately authenticated untagged connection (with a `NULL` tag) is returned. In cases where an undated connection is not free, an appropriately authenticated connection with a different tag is returned.

A `getTag()` call to the `Connection` verifies that the connection tag is received.

| Syntax                                                                                                                                    | Description                                                                                                                                              |
|:------------------------------------------------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Connection *getAnyTaggedConnection(`<br>`   string &tag="")=0;`                                                                          | Returns a pointer to the connection object from a homogeneous stateless connection pool, without the restriction of a matching tag; `string` support.    |
| `Connection* getAnyTaggedConnection(`<br>`   const UString &tag)=0; `                                                                     | Returns a pointer to the connection object from a homogeneous stateless connection pool, without the restriction of a matching tag; `UString` support.   |
| `Connection *getAnyTaggedConnection(`<br>`   const string &userNname,`<br>`   const string &password,`<br>`   const string &tag="")=0;`   | Returns a pointer to the connection object from a heterogeneous stateless connection pool, without the restriction of a matching tag; `string` support.  |
| `Connection* getAnyTaggedConnection(`<br>`   const UString &userName, `<br>`   const UString &Password, `<br>`   const UString &tag)=0 ;` | Returns a pointer to the connection object from a heterogeneous stateless connection pool, without the restriction of a matching tag; `UString` support. |

| Parameter  | Description                                                                                                    |
|:-----------|:---------------------------------------------------------------------------------------------------------------|
| `userName` | The database username                                                                                          |
| `password` | The database password.                                                                                         |
| `tag`      | User-defined type of connection requested. This parameter can be ignored if a default connection is requested. |

### 13.29.2 getAnyTaggedProxyConnection()

Returns a proxy connection from a connection pool.

This method works in an environment with enabled database resident connection pooling.

During the execution of this call, the pool is first searched based on the tag provided. If a connection with the specified tag exists, it is returned to the user. If a matching connection is not available, an appropriately authenticated connection with a different tag is returned. In cases where an undated connection is not free, an appropriately authenticated connection with a different tag is returned.

Restrictions for matching the tag may be removed by passing an empty tag argument parameter.

A `getTag()` call to the connection verifies the connection tag received.

| Syntax                                                                                                                                                                                                                                       | Description                                                                                                               |
|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------|
| `Connection *getAnyTaggedProxyConnection(`<br>`   const string &name,`<br>`   string roles[],`<br>`   unsigned int numRoles,`<br>`   const string tag="",`<br>`   Connection::ProxyType `<br>`      proxyType=Connection::PROXY_DEFAULT);`   | Get a proxy connection with role specifications from a connection pool; includes support for roles and `string` support.  |
| `Connection* getAnyTaggedProxyConnection(`<br>`   const UString &name,`<br>`   string roles[],`<br>`   unsigned int numRoles,`<br>`   const UString &tag,`<br>`   Connection::ProxyType `<br>`      proxyType = Connection::PROXY_DEFAULT);` | Get a proxy connection with role specifications from a connection pool; includes support for roles and `UString` support. |
| `Connection *getAnyTaggedProxyConnection(`<br>`   const string &name,`<br>`   const string tag="",`<br>`   Connection::ProxyType       proxyType=Connection::PROXY_DEFAULT);`                                                                | Get a proxy connection with role specifications from a connection pool; `string` support.                                 |
| `Connection* getAnyTaggedProxyConnection(`<br>`   const UString &name,`<br>`   const UString &tag,`<br>`   Connection::ProxyType `<br>`      proxyType = Connection::PROXY_DEFAULT);`                                                        | Get a proxy connection within role specifications from the connection pool; `UString` support.                            |

| Parameter   | Description                                                                                                |
|:------------|:-----------------------------------------------------------------------------------------------------------|
| `name`      | The username.                                                                                              |
| `roles`     | The roles to activate on the database server                                                               |
| `numRoles`  | The number of roles to activate on the database server                                                     |
| `tag`       | User defined tag associated with the connection.                                                           |
| `proxyType` | The type of proxy authentication to perform; `ProxyType` is defined in [Table 13-11](connection-class.md). |

### 13.29.3 getBusyConnections()

Returns the number of busy connections in the connection pool. When using database resident connection pooling, this is the number of persistent connections to the Connection Broker.

#### Syntax

    unsigned int getBusyConnections() const=0;

### 13.29.4 getBusyOption()

Returns the behavior of the stateless connection pool when all the connections in the pool are busy, and when the number of connections have reached maximum. The return values are defined for `BusyOption` in Table 13-41.

#### Syntax

    BusyOption getBusyOption()=0;


### 13.29.5 getConnection()

Returns a pointer to the connection object of a `StatelessConnectionPool`.

This method works in an environment with enabled database resident connection pooling.

| Syntax                                                                                                                                                                              | Description                                                                                                                                    |
|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------|
| `Connection *getConnection()=0;`                                                                                                                                                    | Returns a connection that can be authenticated externally.                                                                                     |
| `Connection *getConnection(`<br>`   string &tag="")=0;`                                                                                                                             | Returns an authenticated connection, with a connection pool username and password; `string` support.                                           |
| `Connection* getConnection(`<br>`   const UString &tag)=0;`                                                                                                                         | Returns an authenticated connection, with a connection pool username and password; `UString` support.                                          |
| `Connection *getConnection(`<br>`   const string &userName,`<br>`   const string &password,`<br>`   const string &tag="")=0;`                                                       | Returns a pointer to the connection object from a heterogeneous stateless connection pool; `string` support.                                   |
| `Connection* getConnection(`<br>`   const UString &userName,`<br>`   const UString &password,`<br>`   const UString &tag)=0;`                                                       | Returns a pointer to the connection object from a heterogeneous stateless connection pool; `UString` support.                                  |
| `Connection *getConnection(`<br>`   const string &connectionClass,`<br>`   const Connection::Purity &purity)=0;`                                                                    | Returns a pointer to the connection object from a database resident connection pool; `string` support.                                         |
| `Connection* getConnection(`<br>`   const UString &connectionClass,`<br>`   const Connection::Purity &purity)=0;`                                                                   | Returns a pointer to the connection object from a database resident connection pool; `UString` support.                                        |
| `Connection *getConnection(`<br>`   const string &userName,`<br>`   const string &password,`<br>`   const string &connectionClass,`<br>`   const Connection::Purity &purity)=0;`    | Returns a pointer to the connection object from a database resident connection pool; user name and password authentication; `string` support.  |
| `Connection* getConnection(`<br>`   const UString &userName,`<br>`   const UString &password,`<br>`   const UString &connectionClass,`<br>`   const Connection::Purity &purity)=0;` | Returns a pointer to the connection object from a database resident connection pool; user name and password authentication; `UString` support. |
| `Connection *getConnection(`<br>`   const string &connectionClass,`<br>`   const Connection::Purity &purity,`<br>`   const string &tag)=0;`                                         | Returns a tagged connection object from a database resident connection pool; `string` support.                                                 |
| `Connection* getConnection(`<br>`   const UString &connectionClass,`<br>`   const Connection::Purity &purity,`<br>`   const UString &tag)=0;`                                       | Returns a tagged connection object from a database resident connection pool; `UString` support.                                                |

| Parameter         | Description                                                                                                                                                                                                                                   |
|:------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `userName`        | The database username.                                                                                                                                                                                                                        |
| `password`        | The database password.                                                                                                                                                                                                                        |
| `tag`             | The user defined tag associated with the connection. During the call, the pool is first searched based on the tag provided. If a connection with the specified tag exists it is returned; otherwise a new connection is created and returned. |
| `connectionClass` | The class of connection used by database resident connection pool.                                                                                                                                                                            |
| `purity`          | The purity of connection used by database resident connection pool; either `SELF` or `NEW`.                                                                                                                                                   |

### 13.29.6 getIncrConnections()

Returns the number of incremental connections in the connection pool. This call is useful only in cases of homogeneous connection pools. When using database resident connection pooling, this is the number of persistent connections to the Connection Broker.

#### Syntax

    unsigned int getIncrConnections() const=0;

### 13.29.7 getMaxConnections()

Returns the maximum number of connections in the connection pool. When using database resident connection pooling, this is the number of persistent connections to the Connection Broker.

#### Syntax

    unsigned int getMaxConnections() const=0;

### 13.29.8 getMinConnections()

Returns the minimum number of connections in the connection pool. When using database resident connection pooling, this is the number of persistent connections to the Connection Broker.

#### Syntax

    unsigned int getMinConnections() const=0;

### 13.29.9 getOpenConnections()

Returns the number of open connections in the connection pool. When using database resident connection pooling, this is the number of persistent connections to the Connection Broker.

#### Syntax

    unsigned int getOpenConnections() const=0;

### 13.29.10 getPoolName()

Returns the name of the connection pool.

#### Syntax

    string getPoolName() const=0;

### 13.29.11 getProxyConnection()

Returns a proxy connection from a connection pool.

This method works in an environment with enabled database resident connection pooling.

| Syntax                                                                                                                                                                                                                                      | Description                                                                                                                                            |
|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Connection *getProxyConnection(`<br>`   const string &userName,`<br>`   string roles[],`<br>`   unsigned int numRoles,`<br>`   const string& tag="",`<br>`   Connection::ProxyType `<br>`      proxyType=Connection::PROXY_DEFAULT)=0;`    | Get a proxy connection with role specifications from a connection pool; support for roles and `string` support.                                        |
| `Connection* getProxyConnection(`<br>`   const UString &userName,`<br>`   UString roles[], `<br>`   unsigned int numRoles, `<br>`   const UString &tag, `<br>`   Connection::ProxyType `<br>`      proxyType = Connection::PROXY_DEFAULT);` | Get a proxy connection with role specifications from a connection pool; support for roles and `UString` support.                                       |
| `Connection *getProxyConnection(`<br>`   const string &userName,`<br>`   const string &connectionClass,`<br>`   const Connection::Purity &purity)=0;`                                                                                       | Get a proxy connection from a database resident connection pool; `string` support.                                                                     |
| `Connection *getProxyConnection(`<br>`   const UString &userName,`<br>`   const UString &connectionClass,`<br>`   const Connection::Purity &purity)=0;`                                                                                     | Get a proxy connection from a database resident connection pool; `UString` support.                                                                    |
| `Connection *getProxyConnection(`<br>`   const string &userName,`<br>`   string roles[],`<br>`   unsigned int numRoles,`<br>`   const string &connectionClass,`<br>`   const Connection::Purity &purity)=0;`                                | Get a proxy connection with role specifications from a connection pool; support for roles and database resident connection pooling; `string` support.  |
| `Connection* getProxyConnection(`<br>`   const UString &userName,`<br>`   UString roles[], `<br>`   unsigned int numRoles, `<br>`   const UString &connectionClass,`<br>`   const Connection::Purity &purity)=0;`                           | Get a proxy connection with role specifications from a connection pool; support for roles and database resident connection pooling; `UString` support. |
| `Connection *getProxyConnection(`<br>`   const string &userName,`<br>`   const string& tag="",`<br>`   Connection::ProxyType `<br>`      proxyType=Connection::PROXY_DEFAULT)=0;`                                                           | Get a proxy connection without role specifications from a connection pool; `string` support.                                                           |
| `Connection* getProxyConnection(`<br>`   const UString &userName,`<br>`   const UString &tag,`<br>`   Connection::ProxyType `<br>`   proxyType = Connection::PROXY_DEFAULT)`                                                                | Get a proxy connection without role specifications from a connection pool; `UString` support.                                                          |

| Parameter         | Description                                                                                                                                                                                                                                                      |
|:------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `userName`        | The user name.                                                                                                                                                                                                                                                   |
| `roles`           | The roles to activate on the database server.                                                                                                                                                                                                                    |
| `numRoles`        | The number of roles to activate on the database server.                                                                                                                                                                                                          |
| `tag`             | The user defined tag associated with the connection. During the execution of this call, the pool is first searched based on the tag provided. If a connection with the specified tag exists it is returned; otherwise, a new connection is created and returned. |
| `proxyType`       | The type of proxy authentication to perform; `ProxyType` is defined in [Table 13-11](connection-class.md).                                                                                                                                                       |
| `connectionClass` | The class of connection used by database resident connection pool.                                                                                                                                                                                               |
| `purity`          | The purity of connection used by database resident connection pool; either `SELF` or `NEW`.                                                                                                                                                                      |

### 13.29.12 getStmtCacheSize()

Retrieves the size of the statement cache.

#### Syntax

    unsigned int getStmtCacheSize() const=0;

### 13.29.13 getTimeOut()

Returns the timeout period of a connection in the connection pool.

#### Syntax

    unsigned int getTimeOut() const=0;

### 13.29.14 releaseConnection()

Releases the connection back to the pool with an optional tag.

This method works in an environment with enabled database resident connection pooling.

| Syntax                                                                                   | Description                |
|:-----------------------------------------------------------------------------------------|:---------------------------|
| `void releaseConnection(`<br>`   Connection *connection,`<br>`   const string& tag="");` | Support for `string` tag.  |
| `void releaseConnection(`<br>`   Connection *connection,`<br>`   const UString &tag);`   | Support for `UString` tag. |

| Parameter    | Description                                                                                                              |
|:-------------|:-------------------------------------------------------------------------------------------------------------------------|
| `connection` | The connection to be released.                                                                                           |
| `tag`        | The user defined tag associated with the connection. The default of this parameter is `""`, which untags the connection. |

### 13.29.15 setBusyOption()

Specifies the behavior of the stateless connection pool when all the connections in the pool are busy, and when the number of connections have reached maximum.

#### Syntax

    void setBusyOption(
       BusyOption busyOption)=0;

| Parameter    | Description                                              |
|:-------------|:---------------------------------------------------------|
| `busyOption` | Valid values are defined in `BusyOption` in Table 13-41. |

### 13.29.16 setPoolSize()

Sets the maximum, minimum, and incremental number of pooled connections for the connection pool.

#### Syntax

    void setPoolSize(
       unsigned int maxConn=1,
       unsigned int minConn=0,
       unsigned int incrConn=1)=0;

| Parameter  | Description                                                       |
|:-----------|:------------------------------------------------------------------|
| `maxConn`  | The maximum number of connections in the connection pool.         |
| `minConn`  | The minimum number of connections, in homogeneous pools only.     |
| `incrConn` | The incremental number of connections, in homogeneous pools only. |

### 13.29.17 setTimeOut()

Sets the time out period of a connection in the connection pool. OCCI terminates any connections related to this connection pool that have been idle for longer than the timeout period specified.

If this attribute is not set, the least recently used connection is timed out when pool space is required. Oracle only checks for timed out connections when it releases a connection back to the pool.

#### Syntax

    void setTimeOut(
       unsigned int connTimeOut=0)=0;

| Parameter     | Description                            |
|:--------------|:---------------------------------------|
| `connTimeOut` | The time out period, given in seconds. |

### 13.29.18 setStmtCacheSize()

Enables or disables statement caching. A nonzero value enables statement caching, with a cache of specified size. A zero value disables caching.

If the user changes the cache size of individual connections and subsequently returns the connection back to the pool with a tag, the cache size does not revert to the one set for the pool. If the connection is untagged, the cache size is reset to equal the cache size specified for the pool.

#### Syntax

    void setStmtCacheSize(
       unsigned int cacheSize)=0;

| Parameter   | Description                     |
|:------------|:--------------------------------|
| `cacheSize` | The size of the statement cache |

### 13.29.19 terminateConnection()

Closes the connection and removes it from the pool.

This method works in an environment with enabled database resident connection pooling.

#### Syntax

    void terminateConnection(
       Connection *connection)=0;

| Parameter    | Description                     |
|:-------------|:--------------------------------|
| `connection` | The connection to be terminated |
