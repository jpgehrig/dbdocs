## 4 Protocol Address Configuration

Learn how to configure connections for Oracle Database instances and clients.

A network object is identified by a protocol address. When a connection is made, the client and the receiver of the request (listener or Oracle Connection Manager) are configured with identical protocol addresses. The client uses this address to send the connection request to a particular network object location, and the recipient "listens" for requests on this address, and grants a connection based on its address information matching the client information.

- Protocol Addresses
  The protocol address is comprised of `ADDRESS` and `ADDRESS_LIST` elements.
- Protocol Parameters
  The listener and Oracle Connection Manager are identified by protocol addresses.
- Recommended Port Numbers
  Oracle recommends that you use the default port numbers for client and Oracle Connection Manager connections.
- Port Number Limitations
  Understand limitations for port numbers. If it is necessary to configure a listener to use a system port number (in the 1 to 1024 range), then use the procedure described here to configure the listener.

### 4.1 Protocol Addresses

The protocol address is comprised of `ADDRESS` and `ADDRESS_LIST` elements.

- ADDRESS
  The `ADDRESS` networking parameter specifies the protocol address under the `ADDRESS_LIST` or `DESCRIPTION` parameter.
- ADDRESS_LIST
  The `ADDRESS_LIST` networking parameter specifies the number of protocol addresses sharing common characteristics.

**Parent topic:** Protocol Address Configuration

#### 4.1.1 ADDRESS

The `ADDRESS` networking parameter specifies the protocol address under the `ADDRESS_LIST` or `DESCRIPTION` parameter.

##### Purpose

To define a protocol address.

##### Usage Notes

Put this parameter under an `ADDRESS_LIST` or `DESCRIPTION` parameter. A `DESCRIPTION` is used in a `tnsnames.ora` or a `listener.ora` file.

##### Example

    (ADDRESS=
     (PROTOCOL=tcp)
     (HOST=sales-server)
     (PORT=1521))

**Related Topics**

- Protocol Parameters
- [Oracle Database Global Data Services Concepts and Administration Guide](../gsmug/global-data-services-admin.md)

**Parent topic:** Protocol Addresses

#### 4.1.2 ADDRESS_LIST

The `ADDRESS_LIST` networking parameter specifies the number of protocol addresses sharing common characteristics.

##### Purpose

To define a list of protocol addresses that share common characteristics.

##### Usage Notes

This parameter is not mandatory when specifying multiple addresses.

##### Example

    (ADDRESS_LIST=
      (LOAD_BALANCE=on)
      (ADDRESS=
       (PROTOCOL=tcp)
       (HOST=sales-server)
       (PORT=1521))
      (ADDRESS=
       (PROTOCOL=tcp)
       (HOST=hr-server)
       (PORT=1521)))

**Parent topic:** Protocol Addresses

### 4.2 Protocol Parameters

The listener and Oracle Connection Manager are identified by protocol addresses.

The following table lists the parameters used by the Oracle protocol support:

Table 4-1 Protocol-Specific Parameters

| Protocol           | Parameter  | Description                                                                                                                                                                                                                                                                                                                |
|:-------------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| IPC                | `PROTOCOL` | Specify `ipc` as the value.                                                                                                                                                                                                                                                                                                |
| IPC                | `KEYPATH`  | On UNIX variants, IPC protocol uses the UNIX domain socket and this socket creates an internal file for client/server communication. The parameter `keypath` specifies the location where this file is created. If `keypath` is used, then use the same value of version greater than 18 on the client and listener sides. |
| IPC                | `KEY`      | Specify a unique name for the service. Oracle recommends using the service name or the [Oracle system identifier (SID)](glossary.md) of the service.<br>Example:<br>`(PROTOCOL=ipc)(KEY=sales)`                                                                                                                            |
| Named Pipes        | `PROTOCOL` | Specify `nmp` as the value.                                                                                                                                                                                                                                                                                                |
| Named Pipes        | `SERVER`   | Specify the name of the Oracle server.                                                                                                                                                                                                                                                                                     |
| Named Pipes        | `PIPE`     | Specify the pipe name used to connect to the database server. This is the same `PIPE` keyword specified on server with Named Pipes. This name can be any name.<br>Example:<br>`(PROTOCOL=nmp)(SERVER=sales)(PIPE=dbpipe0)`                                                                                                 |
| SDP                | `PROTOCOL` | Specify `sdp` as the value.                                                                                                                                                                                                                                                                                                |
| SDP                | `HOST`     | Specify the host name or IP address of the computer.                                                                                                                                                                                                                                                                       |
| SDP                | `PORT`     | Specify the listening port number.<br>Example:<br>`(PROTOCOL=sdp)(HOST=sales-server)(PORT=1521)`<br>`(PROTOCOL=sdp)(HOST=192.0.2.204)(PORT=1521)`                                                                                                                                                                          |
| TCP/IP             | `PROTOCOL` | Specify `tcp` as the value.                                                                                                                                                                                                                                                                                                |
| TCP/IP             | `HOST`     | Specify the host name or IP address of the computer.                                                                                                                                                                                                                                                                       |
| TCP/IP             | `PORT`     | Specify the listening port number.<br>Example:<br>`(PROTOCOL=tcp)(HOST=sales-server)(PORT=1521)`<br>`(PROTOCOL=tcp)(HOST=192.0.2.204)(PORT=1521)`                                                                                                                                                                          |
| TCP/IP with TLS    | `PROTOCOL` | Specify `tcps` as the value.                                                                                                                                                                                                                                                                                               |
| TCP/IP with TLS    | `HOST`     | Specify the host name or IP address of the computer.                                                                                                                                                                                                                                                                       |
| TCP/IP with TLS    | `PORT`     | Specify the listening port number.<br>Example:<br>`(PROTOCOL=tcps)(HOST=sales-server)(PORT=2484)`<br>`(PROTOCOL=tcps)(HOST=192.0.2.204)(PORT=2484)`                                                                                                                                                                        |
| Exadirect          | `PROTOCOL` | Specify `exadirect` as the value.                                                                                                                                                                                                                                                                                          |
| Exadirect          | `HOST`     | Specify the IP address of the InfiBand interface.                                                                                                                                                                                                                                                                          |
| Exadirect          | `PORT`     | Specify the listening port number.<br>Example:<br>`(PROTOCOL=exadirect)(HOST=sales-server)(PORT=2484)`<br>`(PROTOCOL=tcps)(HOST=192.0.2.204)(PORT=1522)`                                                                                                                                                                   |
| Websocket          | `PROTOCOL` | Specify `ws` as the value; use this protocol only to serve as web server backend database server.                                                                                                                                                                                                                          |
| Websocket          | `HOST`     | Specify the host name or IP address of the computer.                                                                                                                                                                                                                                                                       |
| Websocket          | `PORT`     | Specify the listening port number.<br>Example:<br>`(protocol=ws)(host=sales-server)(port=1524)`                                                                                                                                                                                                                            |
| Secure Websocket   | `PROTOCOL` | Specify `ws` as the value; use this protocol on the client side to connect to a webserver with websocket protocol support. The web server should be configured to make a websocket connection to the database listener. Wallet should be configured in `sqlnet.ora`.<br>Use `SQLNET.URI` for mapping on web server.        |
| Secure Websocket   | `HOST`     | Specify the host name or IP address of the web server with websocket support.                                                                                                                                                                                                                                              |
| Secure Websocket   | `PORT`     | Specify the listening port number.<br>Example:<br>`(protocol=wss)(host=sales-server)(port=1524)`                                                                                                                                                                                                                           |

**Parent topic:** Protocol Address Configuration

### 4.3 Recommended Port Numbers

Oracle recommends that you use the default port numbers for client and Oracle Connection Manager connections.

Table 4-2 Recommended Port Numbers

| Port | Description                                                                                                                                                                              |
|:-----|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1521 | Default listening port for client connections to the listener.<br>This port number can change to the officially registered port number of 2483 for TCP/IP, and 2484 for TCP/IP with TLS. |
| 1521 | Default and officially registered listening port for client connections to Oracle Connection Manager.                                                                                    |
| 1830 | Default and officially registered listening port for administrative commands to Oracle Connection Manager.                                                                               |

**Parent topic:** Protocol Address Configuration

### 4.4 Port Number Limitations

Understand limitations for port numbers. If it is necessary to configure a listener to use a system port number (in the 1 to 1024 range), then use the procedure described here to configure the listener.

Oracle allows port numbers from 1 to 65535. However, the port numbers below 1024 (the **well-known ports** or **system ports**) are typically reserved. Normally, only privileged processes can listen for TCP connections on ports below 1024.

If you need to configure a listener to listen on a port number less than 1024, then complete the following procedure:

**Note:**

This procedure is a guideline. Your operating system can require a different procedure.

1.  Use Oracle Net Configuration Assistant or Oracle Net Manager to configure the listener with protocol addresses and other configuration parameters.

2.  Log in as the `root` user on the machine that has the listener.

3.  Set file ownership and access permissions for the listener executable (`tnslsnr`) and the dependent shared libraries, so that these files can be modified only by the `root` user.

4.  Starting with the `root` directory, ensure that the permissions of the individual directories found in the path names to these files share the same ownership and access permissions.

5.  Start the listener as the `root` user.

6.  Enter the following command at the system prompt:

        tnslsnr listener_name -user user -group group

    In the preceding command, the following options are used:

    Table 4-3 tnslsnr Utility Options

    | Options         | Description                                                                                                                                                                                                                       |
    |:----------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `listener_name` | Specify the name of the listener that you want to configure. If omitted, then the default name `LISTENER` is used.                                                                                                                |
    | `user`          | Specify the user whose privileges you want the listener to use when super user (`root`) privileges are not needed. After performing the privileged operations, the listener gives up `root` privileges irreversibly.              |
    | `group`         | Specify the group whose privileges you want the listener to use when super user (`root`) group privileges are not needed. After performing the privileged operations, the listener gives up `root` group privileges irreversibly. |

    During this step, the listener changes from `root` to the user and group privileges that you specify. All operations are done with the specified user and group privileges, except the system calls necessary to listen on configured endpoints. The listener reverts to the `root` user to listen on reserved addresses, such as TCP ports less than 1024.

    After the listener starts listening on all of its endpoints configured in the `listener.ora` file, it switches to the specified user and group irreversibly. At that point. the listener gives up the `root` privilege that it initially had. The `-user` and `-group` command line arguments only accept user and group identifiers specified in numeric form.

    For example, to run a listener called `mylsnr` with `root` privileges, and to have it use privileges of the Oracle user with the user identifier (UID) of `37555`, and with OSDBA group `dba` membership, with a group identifier (GID) of 16, enter the following command at the operating system prompt:

        tnslsnr mylsnr -user 37555 -group 16

7.  After the listener starts, you can administer it with the Listener Control utility.

    **Caution:**

    - Oracle recommends that the user under whose privileges the listener process runs is the `oracle` user, or a similarly privileged user with whose privileges the listener process normally runs on the operating system.

    - Do not leave the listener process running as the `root` user. Running processes as the super user is a security vulnerability.

**Parent topic:** Protocol Address Configuration
