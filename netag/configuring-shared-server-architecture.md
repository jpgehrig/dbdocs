## 11 Configuring a Shared Server Architecture

When client load causes a strain on memory and other system resources, database administrators can alleviate load issues by starting shared server resources. The [shared server](glossary.md) architecture enables a database server to allow many client processes to share very few server processes, so the number of users that can be supported is increased. With the shared server architecture, many client processes connect to a [dispatcher](glossary.md). The dispatcher directs multiple incoming network session requests to a common queue. An idle shared server process from a shared pool of server processes picks up a request from the queue. This means a small pool of server processes can serve a large number of clients. This is useful when a system is overloaded or has limited memory.

- About Dispatchers
- Enabling Session Multiplexing
- Configuring Clients for Environments with Both Shared and Dedicated Servers

**See Also:**

[Oracle Database Administrator's Guide](../admin/managing-processes.md) for additional information about shared server configuration

**Parent topic:** [Configuration and Administration of Oracle Net Services](part-II-config-and-admin-of-oracle-net-services.md)

### 11.1 About Dispatchers

Shared memory resources for dispatchers, virtual circuits, and shared servers are preconfigured enable shared servers at runtime. Database administrators can start dispatchers and shared servers with the SQL `ALTER SYSTEM` statement without having to restart the instance. When shared server mode is turned on, a dispatcher is started automatically on the TCP/IP protocol even if the DISPATCHERS parameter has not been set. Using a shared server is equivalent to setting the DISPATCHERS parameter in the database initialization parameter file as follows:

    DISPATCHERS="(PROTOCOL=tcp)"

Configure the DISPATCHERS parameter directly if either of the following conditions apply:

- You need to configure a protocol other than TCP/IP.

- You want to configure one or more of the optional dispatcher attributes, such as multiplexing.

You can specify the following attributes for the DISPATCHERS parameter. The `PROTOCOL` attribute is required, and the others are optional. The `ADDRESS` attribute is used to set a specify port number, such as when using a firewall.

- `ADDRESS`

- `CONNECTIONS`

- `DESCRIPTION`

- `DISPATCHERS`

- `LISTENER`

- `MULTIPLEX`

- `PROTOCOL` (required)

- `SERVICE`

- `SESSIONS`

You change the dispatcher configuration using the SQL statement `ALTER SYSTEM`. You do not need to restart the instance after setting the parameters.

- Grouping Services by Dispatcher
- Monitoring Dispatchers

**See Also:**

[Oracle Database Administrator's Guide](../admin/managing-processes.md) for additional information about configuring dispatchers

**Parent topic:** Configuring a Shared Server Architecture

#### 11.1.1 Grouping Services by Dispatcher

An Oracle database can be represented by multiple service names. A pool of dispatchers can be allocated exclusively for clients requesting a particular service. This way, the mission critical requests may be given more resources and in effect increase their priority.

For example, the following initialization parameter file shows two dispatchers. The first dispatcher services requests for clients requesting `sales.us.example.com.` The other dispatcher services requests only for clients requesting `adminsales.us.example.com`.

    SERVICE_NAMES=sales.us.example.com
    INSTANCE_NAME=sales
    DISPATCHERS="(PROTOCOL=tcp)"
    DISPATCHERS="(PROTOCOL=tcp)(SERVICE=adminsales.us.example.com)"

**Note:**

You must manually start services on pluggable databases.

**Parent topic:** About Dispatchers

#### 11.1.2 Monitoring Dispatchers

Use the following views to check configurations and monitor dispatchers:

- V\$QUEUE: Contains information about the shared server message queues. This view is only available to the `SYS` user, and users who have `SELECT ANY TABLE` system privilege, such as `SYSTEM`.

- V\$DISPATCHER: Provides information about the dispatcher processes, including name, network address, status, various usage statistics, and index number.

- V\$DISPATCHER_CONFIG: Provides configuration information about the dispatchers.

- V\$DISPATCHER_RATE: Provides rate statistics for the dispatcher processes.

**See Also:**

- [Oracle Database Performance Tuning Guide](../tgdba/configuring-database-for-performance.md) and [Oracle Database Reference](../refrn/dynamic-performance-views.md) for additional information these views

- [Oracle Database Administrator's Guide](../admin/managing-processes.md) for additional information about shared server configuration

- [Oracle Database Reference](../refrn/DISPATCHERS.md) for additional information about configuring the DISPATCHERS parameter and supported attributes

- [Oracle Database SQL Reference](../sqlrf/SQL-Statements-ALTER-LIBRARY-to-ALTER-SESSION.md) for additional information about the `ALTER` `SYSTEM` statement

**Parent topic:** About Dispatchers

### 11.2 Enabling Session Multiplexing

Session multiplexing, available with Oracle Connection Manager, enables multiple client sessions to funnel through a single protocol connection. For example, several client processes can connect to one dispatcher by way of a single connection from Oracle Connection Manager.

Oracle Connection Manager allows communication by users to the dispatcher by way of a shared connection. At any one time, users might need the connection, while other client processes linked to the dispatcher by way of the connection manager process are idle. Session multiplexing is beneficial because it maximizes use of the dispatcher process connections.

Session multiplexing is also useful for database link connections between dispatchers. The limit on the number of sessions for each dispatcher is operating system specific.

To enable session multiplexing, set the attribute `MULTIPLEX` in the DISPATCHERS parameter to `on` or an equivalent value.

    DISPATCHERS="(PROTOCOL=tcp)(MULTIPLEX=on)"

**See Also:**

"[Enabling Session Multiplexing for Oracle Connection Manager](configuring-oracle-connection-manager.md)" for configuration details

**Parent topic:** Configuring a Shared Server Architecture

### 11.3 Configuring Clients for Environments with Both Shared and Dedicated Servers

If a shared server is configured on the server side, and a client connection request arrives when no dispatchers are registered, then the request is processed by a dedicated server process. If you want a particular client always to use a dispatcher, then configure `(``SERVER``=shared)` in the `CONNECT_DATA` section of the connect descriptor. For example:

    sales=
    (DESCRIPTION=
      (ADDRESS=(PROTOCOL=tcp)(HOST=sales-server)(PORT=1521))
      (CONNECT_DATA=
         (SERVICE_NAME=sales.us.example.com)
         (SERVER=shared)))

If the `(SERVER=shared)` attribute is configured and a dispatcher is not available, then the client connection request is rejected, and a message is sent to the client.

If the database is configured for a shared server and a particular client requires a dedicated server, then you can configure the client to use a dedicated server in one of the following ways:

- You can configure a network service name with a connect descriptor that contains `(SERVER=dedicated)` in the `CONNECT_DATA` section. For example:

      sales=
      (DESCRIPTION=
        (ADDRESS=(PROTOCOL=tcp)(HOST=sales-server)(PORT=1521))
        (CONNECT_DATA=
           (SERVICE_NAME=sales.us.example.com)
           (SERVER=dedicated)))

- You can configure the client profile file, `sqlnet.ora`, with `USE_DEDICATED_SERVER=on`. This adds `(SERVER=dedicated)` to the `CONNECT_DATA` section of the connect descriptor the client uses.

  **Note:**

  If `USE_DEDICATED_SERVER` is set to `ON`, then existing `(SERVER=``value``)` entries in connect descriptors are overwritten with `(SERVER=dedicated)`.

**See Also:**

- "[About the Advanced Connect Data Parameters](enabling-advanced-features.md)" to set the SERVER parameter

- "[Routing Connection Requests to a Process](configuring-profiles.md)" to set the USE_DEDICATED_SERVER parameter

- [Oracle Call Interface Programmer's Guide](../lnoci/session-and-connection-pooling.md) and [Oracle Database Administrator's Guide](../admin/managing-processes.md)

**Parent topic:** Configuring a Shared Server Architecture
