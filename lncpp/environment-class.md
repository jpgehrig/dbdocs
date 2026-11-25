The Environment class provides an OCCI environment to manage memory and other resources for OCCI objects.

The application can have multiple OCCI environments. Each environment would have its own heap and thread-safety mutexes.

Table 13-17 Enumerated Values Used by Environment Class

| Attribute | Options                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|:----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Mode`    | • `DEFAULT` is used for creating an Environment object; it has no thread safety or object support.<br>• `OBJECT` is for creating an Environment object; it uses object features.<br>• `SHARED` is for creating an Environment object.<br>• `NO_USERCALLBACKS` is for creating an Environment object; it does not support user callbacks.<br>• `THREADED_MUTEXED` is a thread safe mode for creating an Environment object, mutexed internally by OCCI.<br>• `THREADED_UNMUTEXED` is a thread safe mode for creating an Environment object; the client is responsible for mutexing.<br>• `EVENTS` supports registration for event notification used in Oracle Database Advanced Queuing.<br>• `USE_LDAP` supports registration with LDAP. |

Table 13-18 Summary of Environment Methods

| Method                                    | Summary                                                                                          |
|:------------------------------------------|:-------------------------------------------------------------------------------------------------|
| createConnection()                        | Establishes a connection to the specified database.                                              |
| createConnectionPool()                    | Creates a connection pool.                                                                       |
| createEnvironment()                       | Creates an `Environment` object.                                                                 |
| createStatelessConnectionPool()           | Creates a stateless connection pool.                                                             |
| enableSubscription()                      | Enables subscription notification                                                                |
| disableSubscription()                     | Disables subscription notification                                                               |
| getCacheMaxSize()                         | Retrieves the Cache Max heap size.                                                               |
| getCacheOptSize()                         | Retrieves the cache optimal heap size.                                                           |
| getCacheSortedFlush()                     | Retrieves the setting of the cache sorting flag.                                                 |
| [getClientVersion()](connection-class.md) | Returns the version of the client library.                                                       |
| getCurrentHeapSize()                      | Returns the current amount of memory allocated to all objects in the current environment.        |
| getLDAPAdminContext()                     | Returns the administrative context when using LDAP open notification registration.               |
| getLDAPAuthentication()                   | Returns the authentication mode when using LDAP open notification registration.                  |
| getLDAPHost()                             | Returns the host on which the LDAP server runs.                                                  |
| getLDAPPort()                             | Returns the port on which the LDAP server is listening.                                          |
| getMap()()                                | Returns the Map for the current environment.                                                     |
| getNLSLanguage()                          | Returns the NLS Language for the current environment.                                            |
| getNLSTerritory()                         | Returns the NLS Territory for the current environment.                                           |
| getOCIEnvironment()                       | Returns the OCI environment associated with the current environment.                             |
| getXAConnection()                         | Creates an XA connection to a database.                                                          |
| getXAEnvironment()                        | Creates an XA` Environment` object.                                                              |
| releaseXAConnection()                     | Releases all resources allocated by a getXAConnection() call.                                    |
| releaseXAEnvironment()                    | Releases all resources allocated by a getXAEnvironment() call.                                   |
| setCacheMaxSize()                         | Specifies the maximum size for the client-side object cache as a percentage of the optimal size. |
| setCacheOptSize()                         | Specifies the optimal size for the client-side object cache in bytes.                            |
| setCacheSortedFlush()                     | Specifies whether to sort cache in table order before flushing.                                  |
| setLDAPAdminContext()                     | Specifies the administrative context for the LDAP client.                                        |
| setLDAPAuthentication()                   | Specifies the LDAP authentication mode.                                                          |
| setLDAPHostAndPort()                      | Specifies the LDAP server host and port.                                                         |
| setLDAPLoginNameAndPassword()             | Specifies the login name and password when connecting to an LDAP server.                         |
| setNLSLanguage()                          | Specifies the NLS Language for the current environment.                                          |
| setNLSTerritory()                         | Specifies the NLS Territory for the current environment.                                         |
| terminateConnection()                     | Closes the connection pool and free all related resources.                                       |
| terminateConnectionPool()                 | Closes the connection pool and free all related resources.                                       |
| terminateEnvironment()                    | Destroys the environment.                                                                        |
| terminateStatelessConnectionPool()        | Closes the stateless connection pool and free all related resources.                             |

### 13.14.1 createConnection()

This method establishes a connection to the database specified.

| Syntax                                                                                                                                                                                                                       | Description                                                                                                                                           |
|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Connection * createConnection(`<br>`   const string &userName,`<br>`   const string &password,`<br>`   const string &connectString="")=0;`                                                                                  | Creates a default connection; if the `userName` and `password` are `NULL`, the connection may be authenticated externally.                            |
| `Connection * createConnection(`<br>`   const UString &userName,`<br>`   const UString &password,`<br>`   const UString &connectString)=0;`                                                                                  | Creates a connection (Unicode support). The client `Environment` should be initialized in` OCCIUTIF16` mode.                                          |
| `Connection * createConnection(`<br>`   const string &userName,`<br>`   const string &password,`<br>`   const string &connectString,`<br>`   const string &connectionClass,`<br>`   const Connection::Purity &purity)=0;`    | Creates a connection for database resident connection pooling.                                                                                        |
| `Connection * createConnection(`<br>`   const UString &userName,`<br>`   const UString &password,`<br>`   const UString &connectString,`<br>`   const UString &connectionClass`<br>`   const Connection::Purity &purity)=0;` | Creates a connection for database resident connection pooling (Unicode support). The client `Environment` should be initialized in` OCCIUTIF16` mode. |

| Parameter         | Description                                                                                         |
|:------------------|:----------------------------------------------------------------------------------------------------|
| `userName`        | The name of the user with which to connect.                                                         |
| `password`        | The password of the user.                                                                           |
| `connectString`   | The database to which the connection is made.                                                       |
| `purity`          | The purity of the connection used for database resident connection pooling; either `SELF` or `NEW`. |
| `connectionClass` | The connection class used for database resident connection pooling.                                 |

### 13.14.2 createConnectionPool()

Creates a connection pool based on the parameters specified.

| Syntax                                                                                                                                                                                                                                                              | Description                                                                                                       |
|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------|
| `ConnectionPool* createConnectionPool(`<br>`   const string &poolUserName,`<br>`   const string &poolPassword,`<br>`   const string &connectString = "",`<br>`   unsigned int minConn = 0,`<br>`   unsigned int maxConn = 1,`<br>`   unsigned int incrConn = 1)=0;` | Creates a default connection pool.                                                                                |
| `ConnectionPool* createConnectionPool(`<br>`   const UString &poolUserName,`<br>`   const UString &poolPassword,`<br>`   const UString &connectString,`<br>`   unsigned int minConn = 0,`<br>`   unsigned int maxConn = 1,`<br>`   unsigned int incrConn = 1)=0;`   | Creates a connection pool (Unicode support). The client `Environment` should be initialized in `OCCIUTIF16` mode. |

| Parameter       | Description                                                                                                                                                                                                                                                                      |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `poolUserName`  | The pool user name.                                                                                                                                                                                                                                                              |
| `poolPassword`  | The pool password.                                                                                                                                                                                                                                                               |
| `connectString` | The connection string for the server                                                                                                                                                                                                                                             |
| `minConn`       | The minimum number of connections in the pool. The minimum number of connections are opened by this method. Additional connections are opened only when necessary. Generally, `minConn` should be set to the number of concurrent statements the application is expected to run. |
| `maxConn`       | The maximum number of connections in the pool. Valid values are 1 and greater.                                                                                                                                                                                                   |
| `incrConn`      | The increment by which to increase the number of connections to be opened if the current number of connections is less than `maxConn`. Valid values are 1 and greater.                                                                                                           |

### 13.14.3 createEnvironment()

Creates an `Environment` object. It is created with the specified memory management functions specified in the `setMemMgrFunctions()` method. If no memory manager functions are specified, then OCCI uses its own default functions. An `Environment` object must eventually be closed to free all the system resources it has acquired.

If the `Mode` is specified is either `THREADED_MUTEXED `or T`HREADED_UNMUTEXED` as defined in Table 13-17, then all three memory management functions must be thread-safe.

| Syntax                                                                                                                                                                                                                                                                                                                                                                                                                                                   | Description                                                                                                                                                                   |
|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `static Environment * createEnvironment(`<br>`   Mode mode = DEFAULT,`<br>`   void *ctxp = 0,`<br>`   void *(*malocfp)(void *ctxp,`<br>`                    size_t size) = 0,`<br>`   void *(*ralocfp)(void *ctxp, `<br>`                    void *memptr,`<br>`                    size_t newsize) = 0,`<br>`   void (*mfreefp)(void *ctxp,`<br>`                   void *memptr) = 0);`                                                                | Creates a default environment.                                                                                                                                                |
| `static Environment * createEnvironment(`<br>`   const string &charset,`<br>`   const string &ncharset,`<br>`   Mode mode = DEFAULT,`<br>`   void *ctxp = 0,`<br>`   void *(*malocfp)(void *ctxp,`<br>`                    size_t size) = 0,`<br>`   void *(*ralocfp)(void *ctxp, `<br>`                    void *memptr,`<br>`                    size_t newsize) = 0,`<br>`   void (*mfreefp)(void *ctxp,`<br>`                   void *memptr) = 0);` | Creates an environment with the specified character set and `NCHAR` character set ids (Unicode support). The client `Environment` should be initialized in `OCCIUTIF16` mode. |

| Parameter  | Description                                                                                                         |
|:-----------|:--------------------------------------------------------------------------------------------------------------------|
| `mode`     | Values are defined as part of `Mode` in Table 13-17: `DEFAULT`, `THREADED_MUTEXED`, `THREADED_UNMUTEXED`, `OBJECT`. |
| `ctxp`     | Context pointer for user-defined memory management function.                                                        |
| `size`     | The size of the memory allocated by user-defined memory allocation function.                                        |
| `newsize`  | The new size of the memory to be reallocated.                                                                       |
| `memptr`   | The existing memory that must be reallocated to new size.                                                           |
| `malocfp`  | User-defined memory allocation function.                                                                            |
| `ralocfp`  | User-defined memory reallocation function.                                                                          |
| `mfreefp`  | User-defined memory free function.                                                                                  |
| `charset`  | Character set id that replaces the one specified in `NLS_LANG`.                                                     |
| `ncharset` | Character set id that replaces the one specified in `NLS_NCHAR`.                                                    |

### 13.14.4 createStatelessConnectionPool()

Creates a `StatelessConnectionPool` object with specified pool attributes.

| Syntax                                                                                                                                                                                                                                                                                                                                                                             | Description            |
|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------------|
| `StatelessConnectionPool* createStatelessConnectionPool(`<br>`   const string &poolUserName,`<br>`   const string &poolPassword,`<br>`   const string connectString="",`<br>`   unsigned int maxConn=1,`<br>`   unsigned int minConn=0,`<br>`   unsigned int incrConn=1,`<br>`   StatelessConnectionPool::PoolType`<br>`      pType=StatelessConnectionPool::HETEROGENEOUS);`      | Support for `string`.  |
| `StatelessConnectionPool* createStatelessConnectionPool(`<br>`   const UString &poolUserName,`<br>`   const UString &poolPassword,`<br>`   const UString &connectString,`<br>`   unsigned int maxConn = 1,`<br>`   unsigned int minConn = 0,`<br>`   unsigned int incrConn = 1,`<br>`   StatelessConnectionPool::PoolType `<br>`   pType=StatelessConnectionPool::HETEROGENEOUS);` | Support for `UString`. |

| Parameter       | Description                                                                                                                                                                                                                                                                                                |
|:----------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `poolUserName`  | The pool user name.                                                                                                                                                                                                                                                                                        |
| `poolPassword`  | The pool password.                                                                                                                                                                                                                                                                                         |
| `connectString` | The connection string for the server.                                                                                                                                                                                                                                                                      |
| `maxConn`       | The maximum number of connections that can be opened the pool; additional sessions cannot be open.                                                                                                                                                                                                         |
| `minConn`       | The number of connections initially created in a pool. This parameter is considered only if the `PoolType` is set to `HOMOGENEOUS`, as defined in [Table 13-41](statelessconnectionpool-class.md) .                                                                                                        |
| `incrConn`      | The number of connections by which to increment the pool if all open connections are busy, up to a maximum open connections specified by `maxConn` parameter. This parameter is considered only if the `PoolType` is set to `HOMOGENEOUS`, as defined in [Table 13-41](statelessconnectionpool-class.md) . |
| `pType`         | The `PoolType` of the connection pool, defined in [Table 13-41](statelessconnectionpool-class.md) .                                                                                                                                                                                                        |

### 13.14.5 enableSubscription()

Enables subscription notification.

#### Syntax

    void enableSubscription(
       const aq::Subscription &sub);

| Parameter | Description       |
|:----------|:------------------|
| `sub`     | The Subscription. |

### 13.14.6 disableSubscription()

Disables subscription notification.

#### Syntax

    void disableSubscription(
       Subscription &subscr);

| Parameter | Description       |
|:----------|:------------------|
| `subscr`  | The Subscription. |

### 13.14.7 getCacheMaxSize()

Retrieves the maximum size of the cache.

#### Syntax

    unsigned int getCacheMaxSize() const;

### 13.14.8 getCacheOptSize()

Retrieves the Cache optimal heap size.

#### Syntax

    unsigned int getCacheOptSize() const;

### 13.14.9 getCacheSortedFlush()

Retrieves the current setting of the cache sorting flag; `TRUE` or `FALSE`.

#### Syntax

    bool getCacheSortedFlush() const;

### 13.14.10 getCurrentHeapSize()

Returns the amount of memory currently allocated to all objects in this environment.

#### Syntax

    unsigned int getCurrentHeapSize() const;

### 13.14.11 getLDAPAdminContext()

Returns the administrative context when using LDAP open notification registration.

#### Syntax

    string getLDAPAdminContext() const;

### 13.14.12 getLDAPAuthentication()

Returns the authentication mode when using LDAP open notification registration.

#### Syntax

    unsigned int getLDAPAuthentication() const;

### 13.14.13 getLDAPHost()

Returns the host on which the LDAP server runs.

#### Syntax

    string getLDAPHost() const;


### 13.14.14 getLDAPPort()

Returns the port on which the LDAP server is listening.

#### Syntax

    unsigned int getLDAPPort() const;

### 13.14.15 getMap()

Returns a pointer to the map for this environment.

#### Syntax

    Map *getMap() const;

### 13.14.16 getNLSLanguage()

Returns the NLS Language for the current environment.

#### Syntax

    string getNLSLanguage() const;

### 13.14.17 getNLSTerritory()

Returns the NLS Territory for the current environment.

#### Syntax

    string getNLSTerritory() const;

### 13.14.18 getOCIEnvironment()

Returns a pointer to the OCI environment associated with this environment.

#### Syntax

    OCIEnv *getOCIEnvironment() const;

### 13.14.19 getXAConnection()

Returns a pointer to an OCCI Connection object that corresponds to the one opened by the XA library.

#### Syntax

    Connection* getXAConnection(
       const string &dbname);

| Parameter | Description                                                                                                                    |
|:----------|:-------------------------------------------------------------------------------------------------------------------------------|
| `dbname`  | The database name; same as the optional `dbname` provided in the Open String (and used in connection to the Resource Manager). |

### 13.14.20 getXAEnvironment()

Returns a pointer to an OCCI Environment object that corresponds to the one opened by the XA library.

#### Syntax

    Environment *getXAEnvironment(
       const string &dbname);

| Parameter | Description                                                                                                                    |
|:----------|:-------------------------------------------------------------------------------------------------------------------------------|
| `dbname`  | The database name; same as the optional `dbname` provided in the Open String (and used in connection to the Resource Manager). |

### 13.14.21 releaseXAConnection()

Release/deallocate all resources allocated by the getXAConnection() method.

#### Syntax

    void releaseXAConnection(
       Connection* conn);

| Parameter | Description                                              |
|:----------|:---------------------------------------------------------|
| `conn`    | The connection returned by the getXAConnection() method. |

### 13.14.22 releaseXAEnvironment()

Release/deallocate all resources allocated by the getXAEnvironment() method.

#### Syntax

    void releaseXAEnvironment(
       Environment* env);

| Parameter | Description                                                |
|:----------|:-----------------------------------------------------------|
| `env`     | The environment returned by the getXAEnvironment() method. |

### 13.14.23 setCacheMaxSize()

Sets the maximum size for the client-side object cache as a percentage of the optimal size. The default value is 10%.

#### Syntax

    void setCacheMaxSize(
       unsigned int maxSize);

| Parameter | Description                                     |
|:----------|:------------------------------------------------|
| `maxSize` | The value of the maximum size, as a percentage. |

### 13.14.24 setCacheOptSize()

Sets the optimal size for the client-side object cache in bytes. The default value is 8MB.

#### Syntax

    void setCacheOptSize(
       unsigned int optSize);

| Parameter | Description                              |
|:----------|:-----------------------------------------|
| `optSize` | The value of the optimal size, in bytes. |

### 13.14.25 setCacheSortedFlush()

Sets the cache flushing protocol. By default, objects in cache are flushed in the order they are modified; `flag=FALSE`. To improve server-side performance, set `flag=TRUE`, so that the objects in cache are sorted in table order before flushing from client cache.

#### Syntax

    void setCacheSortedFlush(
       bool flag);

| Parameter | Description                                                   |
|:----------|:--------------------------------------------------------------|
| `flag`    | `FALSE` (default): no sorting; `TRUE`: sorting in table order |

### 13.14.26 setLDAPAdminContext()

Sets the administrative context of the client. This is usually the root of the Oracle RDBMS LDAP schema in the LDAP server.

#### Syntax

    void setLDAPAdminContext(
       const string &ctx);

| Parameter | Description        |
|:----------|:-------------------|
| `ctx`     | The client context |

### 13.14.27 setLDAPAuthentication()

Specifies the authentication mode. Currently the only supported value is 0x1: Simple authentication; username/password authentication.

#### Syntax

    void setLDAPAuthentication(
       unsigned int mode);

| Parameter | Description             |
|:----------|:------------------------|
| `mode`    | The authentication mode |

### 13.14.28 setLDAPHostAndPort()

Specifies the host on which the LDAP server is running, and the port on which it is listening for requests.

#### Syntax

    void setLDAPHostAndPort(
       const string &host,
       unsigned int port);

| Parameter | Description       |
|:----------|:------------------|
| `host`    | The host for LDAP |
| `port`    | The port for LDAP |

### 13.14.29 setLDAPLoginNameAndPassword()

Specifies the login distinguished name and password used when connecting to an LDAP server.

#### Syntax

    void setLDAPLoginNameAndPassword(
       const string &login,
       const &passwd);

| Parameter | Description        |
|:----------|:-------------------|
| `login`   | The login name     |
| `passwd`  | The login password |

### 13.14.30 setNLSLanguage()

Specifies the NLS Language for the current environment. The setting is effective for the connections created after this method has been called. The setting overrides the value set through the process environment variable `NLS_LANG`.

#### Syntax

    void setNLSLanguage(
       const string &lang);

| Parameter | Description                             |
|:----------|:----------------------------------------|
| `lang`    | The language of the current environment |

### 13.14.31 setNLSTerritory()

Specifies the NLS Territory for the current environment. The setting is effective for the connections created after this method has been called. The setting overrides the value set through the process environment variable `NLS_LANG`.

#### Syntax

    void setNLSTerritory(
       const string &Terr);

| Parameter | Description                              |
|:----------|:-----------------------------------------|
| `Terr`    | The territory of the current environment |

### 13.14.32 terminateConnection()

Closes the connection to the environment, and frees all related system resources.

#### Syntax

    void terminateConnection(
       Connection *connection);

| Parameter    | Description                                            |
|:-------------|:-------------------------------------------------------|
| `connection` | A pointer to the connection instance to be terminated. |

### 13.14.33 terminateConnectionPool()

Closes the connections in the connection pool, and frees all related system resources.

#### Syntax

    void terminateConnectionPool(
       ConnectionPool *poolPointer);

| Parameter     | Description                                                 |
|:--------------|:------------------------------------------------------------|
| `poolPointer` | A pointer to the connection pool instance to be terminated. |

### 13.14.34 terminateEnvironment()

Closes the environment, and frees all related system resources.

#### Syntax

    void terminateEnvironment(
       Environment *env);

| Parameter | Description               |
|:----------|:--------------------------|
| `env`     | Environment to be closed. |

### 13.14.35 terminateStatelessConnectionPool()

Destroys the specified `StatelessConnectionPool`.

#### Syntax

    void termimnateStatelessConnectionPool(
       StatelessConnectionPool* poolPointer,
       StatelessConnectionPool::DestroyMode mode=StatelessConnectionPool::DEFAULT);

| Parameter     | Description                                                                                         |
|:--------------|:----------------------------------------------------------------------------------------------------|
| `poolPointer` | The `StatelessConnectionPool` to be destroyed.                                                      |
| mode          | `DestroyMode` as defined [Table 13-41](statelessconnectionpool-class.md): `DEFAULT` or `SPF_FORCE`. |
