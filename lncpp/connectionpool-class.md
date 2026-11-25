The ConnectionPool class represents a pool of connections for a specific database.

Table 13-13 Summary of ConnectionPool Methods

| Method                  | Summary                                                                                                                                            |
|:------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|
| createConnection()      | Creates a pooled connection.                                                                                                                       |
| createProxyConnection() | Creates a proxy connection.                                                                                                                        |
| getBusyConnections()    | Returns the number of busy connections in the connection pool.                                                                                     |
| getIncrConnections()    | Returns the number of incremental connections in the connection pool.                                                                              |
| getMaxConnections()     | Returns the maximum number of connections in the connection pool.                                                                                  |
| getMinConnections()     | Returns the minimum number of connections in the connection pool.                                                                                  |
| getOpenConnections()    | Returns the number of open connections in the connection pool.                                                                                     |
| getPoolName()           | Returns the name of the connection pool.                                                                                                           |
| getStmtCacheSize()      | Retrieves the size of the statement cache.                                                                                                         |
| getTimeOut()            | Returns the time out period for a connection in the connection pool.                                                                               |
| setErrorOnBusy()        | Specifies that a `SQLException` should be generated when all connections in the connection pool are busy and no further connections can be opened. |
| setPoolSize()           | Sets the minimum, maximum, and incremental number of pooled connections for the connection pool.                                                   |
| setStmtCacheSize()      | Enables or disables statement caching.                                                                                                             |
| setTimeOut()            | Sets the time out period, in seconds, for a connection in the connection pool.                                                                     |
| terminateConnection()   | Destroys the connection.                                                                                                                           |

### 13.11.1 createConnection()

Creates a pooled connection.

| Syntax                                                                                               | Description                                                                                                                |
|:-----------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------|
| `Connection* createConnection(`<br>`   const string &userName,`<br>`   const string &password)=0;`   | Creates a pooled connection. If the `userName` and `password `are both `NULL`, the connection is externally authenticated. |
| `Connection* createConnection(`<br>`   const UString &username,`<br>`   const UString &password)=0;` | Creates a globalization enabled pooled connection.                                                                         |

| Parameter  | Description                                 |
|:-----------|:--------------------------------------------|
| `userName` | The name of the user with which to connect. |
| `password` | The password of the user.                   |

### 13.11.2 createProxyConnection()

Creates a proxy connection from the connection pool.

| Syntax                                                                                                                                                                                                     | Description                                                         |
|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------|
| `Connection* createProxyConnection(`<br>`   const string &name,`<br>`   Connection::ProxyType `<br>`      proxyType=Connection::PROXY_DEFAULT)=0;`                                                         | Creates a proxy connection.                                         |
| `Connection* createProxyConnection(`<br>`   const UString &name,`<br>`   Connection::ProxyType `<br>`      proxyType=Connection::PROXY_DEFAULT)=0;`                                                        | Creates a globalization enabled proxy connection.                   |
| `Connection* createProxyConnection(`<br>`   const string &name,`<br>`   string roles[],`<br>`   int numRoles,`<br>`   Connection::ProxyType `<br>`      proxyType=Connection::PROXY_DEFAULT)=0;`           | Creates a proxy connection for several roles.                       |
| `Connection* createProxyConnection(`<br>`   const UString &name,`<br>`   string roles[],`<br>`   unsigned int numRoles,`<br>`   Connection::ProxyType `<br>`      proxyType=Connection::PROXY_DEFAULT)=0;` | Creates a globalization enabled proxy connection for several roles. |

| Parameter   | Description                                                                                                                                                                        |
|:------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `name`      | The user name to connect with.                                                                                                                                                     |
| `roles`     | The roles to activate on the database server.                                                                                                                                      |
| `numRoles`  | The number of roles to activate on the database server.                                                                                                                            |
| `proxyType` | The type of proxy authentication to perform, `ProxyType`, defined in [Table 13-11](connection-class.md). Valid values are:<br>• `PROXY_DEFAULT` representing a database user name. |

### 13.11.3 getBusyConnections()

Returns the number of busy connections in the connection pool. When using database resident connection pooling, this is the number of persistent connections to the Connection Broker.

#### Syntax

    unsigned int getBusyConnections() const=0;

### 13.11.4 getIncrConnections()

Returns the number of incremental connections in the connection pool. When using database resident connection pooling, this is the number of persistent connections to the Connection Broker.

#### Syntax

    unsigned int getIncrConnections() const=0;

### 13.11.5 getMaxConnections()

Returns the maximum number of connections in the connection pool. When using database resident connection pooling, this is the number of persistent connections to the Connection Broker.

#### Syntax

    unsigned int getMaxConnections() const=0;

### 13.11.6 getMinConnections()

Returns the minimum number of connections in the connection pool. When using database resident connection pooling, this is the number of persistent connections to the Connection Broker.

#### Syntax

    unsigned int getMinConnections() const=0;

### 13.11.7 getOpenConnections()

Returns the number of open connections in the connection pool. When using database resident connection pooling, this is the number of persistent connections to the Connection Broker.

#### Syntax

    unsigned int getOpenConnections() const=0;

### 13.11.8 getPoolName()

Returns the name of the connection pool.

#### Syntax

    string getPoolName() const=0;

### 13.11.9 getStmtCacheSize()

Retrieves the size of the statement cache.

#### Syntax

    unsigned int getStmtCacheSize() const=0;

### 13.11.10 getTimeOut()

Returns the time out period of a connection in the connection pool.

#### Syntax

    unsigned int getTimeOut() const=0;

### 13.11.11 setErrorOnBusy()

Specifies that a `SQLException` is to be generated when all connections in the connection pool are busy and no further connections can be opened.

#### Syntax

    void setErrorOnBusy()=0;

### 13.11.12 setPoolSize()

Sets the minimum, maximum, and incremental number of pooled connections for the connection pool.

#### Syntax

    void setPoolSize(
       unsigned int minConn = 0,
       unsigned int maxConn = 1,
       unsigned int incrConn = 1)=0;

| Parameter  | Description                                                    |
|:-----------|:---------------------------------------------------------------|
| `minConn`  | The minimum number of connections for the connection pool.     |
| `maxConn`  | The maximum number of connections for the connection pool.     |
| `incrConn` | The incremental number of connections for the connection pool. |

### 13.11.13 setStmtCacheSize()

Enables or disables statement caching. A nonzero value enables statement caching, with a cache of specified size. A zero value disables caching.

#### Syntax

    void setStmtCacheSize(
       unsigned int cacheSize)=0;

| Parameter   | Description                      |
|:------------|:---------------------------------|
| `cacheSize` | The size of the statement cache. |

### 13.11.14 setTimeOut()

Sets the time out period for a connection in the connection pool. OCCI terminates any connections related to this connection pool that have been idle for longer than the time out period specified.

If this attribute is not set, the least recently used sessions are timed out when pool space is required. Oracle only checks for timed out sessions when it releases a session back to the pool.

#### Syntax

    void setTimeOut(
       unsigned int connTimeOut = 0)=0;

| Parameter     | Description                              |
|:--------------|:-----------------------------------------|
| `connTimeOut` | The timeout period in number of seconds. |

### 13.11.15 terminateConnection()

Terminates the pooled connection or proxy connection.

#### Syntax

    void terminateConnection(
       Connection *connection)=0;

| Parameter    | Description                                             |
|:-------------|:--------------------------------------------------------|
| `connection` | The pooled connection or proxy connection to terminate. |
