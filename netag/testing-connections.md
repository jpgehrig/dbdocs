## 15 Testing Connections

After you have configured the network, you should connect and test each component to ensure that the network is functioning properly. Oracle Net Services provides tools to help you test the listener, database, and Oracle Connection Manager.

- Testing the Network
  This is the recommended sequence for testing the network.
- Using the TNSPING Utility to Test Connectivity from the Client
  The `TNSPING` utility determines whether the listener for a service on an Oracle Net network can be reached successfully.
- Using the TRCROUTE Utility to Test Connectivity from the Client
  The Trace Route Utility (`TRCROUTE`), in Linux and UNIX environments, enables administrators to discover the path or route a connection takes from a client to a server.

**Parent topic:** [Testing and Troubleshooting Oracle Net Services](part-III-test-and-troubleshoot-oracle-net-services.md)

### 15.1 Testing the Network

This is the recommended sequence for testing the network.

1.  Start and test each listener. To start the listener, use the procedure described in [Starting Oracle Net Listener and the Oracle Database Server](quick-start-oracle-net-services.md).

    To test a listener, initiate a connection from a client to any active database controlled by that listener.

2.  Start and test each Oracle Connection Manager, if included in your network. To start Oracle Connection Manager, use the procedure described in [Starting Oracle Connection Manager](quick-start-oracle-net-services.md).

    To test Oracle Connection Manager, initiate a connection from a client to any active database that has been registered with Oracle Connection Manager.

3.  Test the server with a loopback test or Oracle Net Manager.

    A loopback test uses Oracle Net to go from the database server back to itself, bypassing the Interprocess Communication (IPC). Performing a successful loopback verifies that Oracle Net is functioning on the database server. The following procedure describes how to perform a loopback test using Oracle Net Manager:

    1.  Start Oracle Net Manager.

        **See Also:**

        [Using Oracle Net Manager to Configure Oracle Net Services](managing-oracle-net-services.md)

    2.  In the navigator, expand Directory or Local, and then select Service Naming.

    3.  Select the network service name or database service.

    4.  Choose Command, and then select Test Net Service.

        Testing assumes the listener and database are running. If they are not, then see [Starting Oracle Net Listener and the Oracle Database Server](quick-start-oracle-net-services.md) to start components.

        During testing, a Connection Test dialog box appears, providing status and test results. A successful test results in the following message:

            The connection test was successful.

        If the test was successful, then proceed to step 3.e.

        If the test was not successful, then use the error message to determine further action. For example, if the error message is the following:

            Attempting to connect using userid:  scott
            The test did not succeed.
            ORA-28000: the account is locked

            There may be an error in the fields entered,
            or the server may not be ready for a connection.

        Change the user name to an account known to be unlocked. To change the user name, click Change Login. You are prompted for the password.

    5.  Click Close to close the Connect Test dialog box.

4.  Test client with a connection.

    To test several different clients in your network, initiate a connection to a database server from each of them using the following command:

        CONNECT username@connect_identifier

**Parent topic:** Testing Connections

### 15.2 Using the TNSPING Utility to Test Connectivity from the Client

The `TNSPING` utility determines whether the listener for a service on an Oracle Net network can be reached successfully.

If you can connect successfully from a client to a server (or a server to another server) using the TNSPING utility, then it displays an estimate of the round trip time (in milliseconds) it takes to establish a SQLNET connection to the Oracle listener corresponding to the server.

If it fails, then it displays a message describing the error that occurred. This enables you to see the network error that is occurring without the overhead of a database connection.

Use the following command to test connectivity:

    tnsping net_service_name count

In the preceding command, the following arguments are used:

- net_service_name must exist in `tnsnames.ora` file or the name service in use, such as NIS.

- count determines how many times the program attempts to reach the server. This argument is optional.

If the network service name specified is a database name, then TNSPING attempts to contact the corresponding listener. It does not actually determine whether the database is running. Use SQL\*Plus to attempt a connection to the database.

The following are some examples of TNSPING.

**Note:**

Different platforms may have different interfaces, but the program accepts the same arguments. Invoke TNSPING for the display of the proper interface requirements.

The following is an example of checking a listener for a database using a network service name of `sales` using the `TNSPING` command.

Example 15-1 Checking a Listener with TNSPING

    TNSPING sales

This produces the following message:

    TNS Ping Utility for Linux: Version 19.0.0.0.0 - Production on 21-JAN-2019

    Copyright (c) 1997, 2019 Oracle Corporation.  All rights reserved.

    Used parameter files:
    Used TNSNAMES adapter to resolve the alias
    Attempting to contact (DESCRIPTION = (ADDRESS_LIST = (ADDRESS = (PROTOCOL =
    TCP)(HOST = sales-server)(PORT = 1521))) (CONNECT_DATA = (SERVICE_NAME =
    sales.us.example.com)))
    OK (10 msec)

To determine whether the listener for the `sales` database is available, and to specify that TNSPING try to connect eight times and then give up, use the following syntax:

    tnsping sales 8

This command produces the following message:

    TNS Ping Utility for Linux: Version 19.0.0.0.0 - Production on 21-JAN-2019

    Copyright (c) 1997, 2019 Oracle Corporation.  All rights reserved.

    Used parameter files:

    Used TNSNAMES adapter to resolve the alias
    Attempting to contact (DESCRIPTION = (ADDRESS_LIST = (ADDRESS = (PROTOCOL =
    TCP)(HOST = sales-server)(PORT = 1521))) (CONNECT_DATA = (SERVICE_NAME =
    sales.us.example.com)))
    OK (10 msec)
    OK (0 msec)
    OK (10 msec)
    OK (0 msec)
    OK (10 msec)
    OK (10 msec)
    OK (10 msec)
    OK (0 msec)

The following is an example of TNSPING attempting to check using an invalid network service name.

Example 15-2 Checking an Invalid Net Service Name with TNSPING

    tnsping badname

This attempt produces the following message:

    TNS Ping Utility for Linux: Version 19.0.0.0.0 - Production on 21-MAY-2019

    Copyright (c) 1997, 2019 Oracle Corporation.  All rights reserved.

    Used parameter files:

    TNS-03505: Failed to resolve name

The following is an example of output when using TNSPING to check a name that is valid, but resolves to an address where no listener is located, for example, the listener may not be started.

Example 15-3 Checking Valid Net Service Name but No Listener with TNSPING

    tnsping sales

    TNS Ping Utility for Linux: Version 19.0.0.0.0 - Production on 21-JAN-2019

    Copyright (c) 1997, 2019 Oracle Corporation.  All rights reserved.

    Used parameter files:
    Used TNSNAMES adapter to resolve the alias
    Attempting to contact (DESCRIPTION = (ADDRESS_LIST = (ADDRESS = (PROTOCOL =
    TCP)(HOST = sales-server)(PORT = 1521))) (CONNECT_DATA = (SERVICE_NAME =
    sales.us.example.com)))
    TNS-12541: TNS:no listener

**Parent topic:** Testing Connections

### 15.3 Using the TRCROUTE Utility to Test Connectivity from the Client

The Trace Route Utility (`TRCROUTE`), in Linux and UNIX environments, enables administrators to discover the path or route a connection takes from a client to a server.

If `TRCROUTE` encounters a problem, then it returns an error stack to the client instead of a single error. These additional error messages make troubleshooting easier.

`TRCROUTE` is different from `TNSPING` in that it travels as a special type of connect packet, and is routed as such. As it travels toward its destination, the `TRCROUTE` connect packet collects the TNS addresses of every node it travels through. If an error occurs, then `TRCROUTE` collects error information that shows where the error occurred. The `TRCROUTE` displays the information collected on the client screen. You can redirect the `TRCROUTE` output to a file, and print it.

The `TRCROUTE` uses minimal resources. It gathers information in the connect data of a special connect packet. Standard connect packets are not affected.

The server is not affected by `TRCROUTE`. The listener receives and processes the `TRCROUTE` connect packet. It returns the information to the client by putting it into a refuse packet. The server does not need to start any new processes or deal with dummy connections.

To use the `TRCROUTE` utility, enter the following command:

    trcroute net_service_name

The following example shows a successful trace route packet that traveled from a client to a listener:

Example 15-4 Successful Trace Route

    trcroute sales

    Trace Route Utility for Linux: Version 19.0.0.0.0 - Production on 21-JAN-2019

    Copyright (c) 1999, 2019 Oracle Corporation.  All rights reserved.

    Route of TrcRoute:
    ------------------

    Node: Client            Time and address of entry into node:
    -------------------------------------------------------------
    09-NOV-2012 21:48:48 ADDRESS= PROTOCOL=TCP  HOST=10.150.21.136  PORT=14001

    Node: Server            Time and address of entry into node:
    -------------------------------------------------------------
    09-NOV-2012 21:48:05 ADDRESS= PROTOCOL=TCP  HOST=10.150.21.136  PORT=14001

The following example shows an unsuccessful trace route packet that could not reach the listener because the listener was not up:

Example 15-5 Trace Route with Error

    trcroute sales

    Trace Route Utility for Linux: Version 19.0.0.0.0 - Production on 21-JAN-2019

    Copyright (c) 1999, 2019 Oracle Corporation.  All rights reserved.

    Route of TrcRoute:
    ------------------

    Node: Client            Time and address of entry into node:
    -------------------------------------------------------------
    25-FEB-2012 14:43:05 ADDRESS= PROTOCOL=TCP  HOST=sales-server  PORT=1521

    TNS-12543: TNS:unable to connect to destination
    TNS-12541: TNS:no listener
    TNS-12560: TNS:protocol adapter error
    TNS-03601: Failed in route information collection

**Parent topic:** Testing Connections
