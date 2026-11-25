You can set the parameter `USE_SHARED_SOCKET` to `true` to enable the use of shared sockets.

If this parameter is set to `true`, the network listener passes the socket descriptor for client connections to the database thread. As a result, the client does not establish a new connection to the database thread and database connection time improves. Also, all database connections share the port number used by the network listener, which can be useful if you are setting up third-party proxy servers.

This parameter only works in the dedicated server mode in a TCP/IP environment. If this parameter is set, you cannot use the Oracle database listener to spawn Oracle Database. To spawn a dedicated server for an instance of Oracle Database not associated with the same Oracle home as the listener and have shared socket enabled, you must also set parameter `USE_SHARED_SOCKET` for both Oracle homes.

**Parent topic:** [Overview of Optional Configuration Parameters](overview-of-optional-configuration-parameters.md)
