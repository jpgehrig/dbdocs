The instructions in this section describe how to configure the network if the gateway is utilizing the SNA or TCP/IP communication protocol.

The gateway must be defined to the Oracle Net Listener, and a service name must be defined for accessing the gateway. To do this, perform the following steps:

1.  Add an entry for the gateway to the `listener.ora` file:
    - If you are using SNA:

          (SID_DESC=
               (SID_NAME=PGA)
               (ORACLE_HOME=/oracle/pga/12.2)
               (PROGRAM=pg4asrv)
          )

      where: `/oracle/pga/12.2 `is your gateway Oracle home and `PGA` is the gateway SID name.

    - Or, if you are using TCP/IP:

          (SID_DESC=
               (SID_NAME=PGA)
               (ORACLE_HOME=/oracle/pga/12.2)
               (PROGRAM=pg4t4ic)
          )

      where: `/oracle/pga/12.2` is the gateway Oracle home and `PGA` is the gateway SID name.
2.  Add a service name for the gateway to the `tnsnames.ora` file on the system where your Oracle database is located. The service name is specified in the `USING` parameter of the database link defined for accessing the gateway from the Oracle database. For example, if you are using the IPC protocol adapter and your gateway `sid` is PGA, then add the following entry to `tnsnames.ora`:
        pgaipc=
                (DESCRIPTION =
                        (ADDRESS = (PROTOCOL = ipc) (KEY=key))
                        (CONNECT_DATA = (SID=PGA))
                        (HS=)
                )

    In this example, `key `is the IPC key defined in the `listener.ora` file for the IPC protocol. You can use the IPC protocol only if the Oracle database and the gateway are on the same system.

    If you are using the TCP/IP protocol adapter, and if your gateway `sid` is PGA, then add the following entry to `tnsnames.ora`:

        pgatcp=
                (DESCRIPTION =
                      (ADDRESS = (PROTOCOL= TCP)(Host= gateway)(Port= port))
                        (CONNECT_DATA = (SID=PGA))
                        (HS=)
                )

    In this example, `port` is the TCP port defined in the `listener.ora` file for the TCP protocol, and `gateway` is the TCP/IP host name of the system where the gateway is located.

    **Note:**

    For the following cases:

    - If your gateway and Oracle database are not on the same system,

    - If the gateway and the Oracle database are on the same system but the Oracle database Listener is different than the gateway listener

    You must define the Oracle database to PGAU by adding a service name to `tnsnames.ora` on the system where your gateway is located. For example:

        ora_server =
           (DESCRIPTION=
             (ADDRESS =
               (PROTOCOL= TCP)
               (PORT= port)
               (HOST= ora_srv)
              )
              (CONNECT_DATA= (SID= ora_server))
           )

    In this example:

    - `port` is the TCP port defined in the Oracle database `listener.ora` for the TCP protocol;

    - `ora_srv` is the TCP/IP host name of the system where the Oracle database is located; and

    - `ora_server` is the SID of the Oracle database.

    Ensure that you start the defined listener(s).

    **See Also:**

    [Oracle Database Net Services Administrator's Guide](../netag/index.md) for more information about configuring the network

Example 5-1 Proceed with Configuring the Communication Package for the Gateway

If your communication protocol is SNA, you must now configure the SNA communication package profiles for APPC connections.

Configure the profiles to define LU6.2 conversations with the OLTP. Refer to the appropriate chapter from the following list to read about the SNA communication package or the TCP/IP package for your platform.

- For Linux for Intel Pentium-based 32-bit systems, refer to [Configuring the SNA Communication Package on Linux](appc-gateway-config-sna-linux.md) .

- For AIX-Based Systems, refer to [Configuring the SNA Communication Package on AIX-Based Systems](appc-gateway-config-sna-aix.md).

<!-- -->

- For Solaris Operating System (SPARC 64-bit), refer to [Configuring the SNA Communication Package on Solaris](appc-gateway-config-sna-solaris.md) .

In addition, if your communication protocol is SNA, refer to "[Sample listener.ora file for a Gateway Using SNA](appc-gateway-initialization-parameters-sna.md)" and "[Sample tnsnames.ora file for a Gateway Using SNA](appc-gateway-initialization-parameters-sna.md)" in [Gateway Initialization Parameters for SNA Protocol](appc-gateway-initialization-parameters-sna.md).

If your communication protocol is TCP/IP, refer to "[Sample listener.ora File for a Gateway Using TCP/IP](appc-gateway-initialization-parameters-tcp-ip.md)" and "[Sample tnsnames.ora File for a Gateway Using TCP/IP](appc-gateway-initialization-parameters-tcp-ip.md)" in [Gateway Initialization Parameters for TCP/IP Communication Protocol](appc-gateway-initialization-parameters-tcp-ip.md) .
