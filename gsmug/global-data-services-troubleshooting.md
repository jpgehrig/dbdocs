The following topics provide information about tools and solutions for troubleshooting the GDS issues you might encounter.

### Troubleshooting Oracle Error Codes

This section contains information for troubleshooting specific Oracle error messages you might encounter, such as:

#### ORA-01045: user GSMADMIN_INTERNAL lacks CREATE SESSION privilege; logon denied

The user `GSMADMIN_INTERNAL` is an internal only user, it should never be unlocked or used for any database login. No direct modifications should be made on the Global Data Services schema objects unless directed by Oracle Technical Support.

#### ORA-12514: TNS:listener does not currently know of service requested in connect descriptor

The global service may be down. Verify that the pool databases are up and the service is started.

The global service may be disabled. Ensure that the pool databases are up and the service is enabled and started.

The GDS pool database may be down. Ensure that the GDS pool databases are up and the service is enabled and started.

#### ORA-12516: TNS:listener could not find available handler with matching protocol stack

The GDS pool database's local listener may be down. Ensure that the GDS pool database local listener is running.

#### ORA-12541: TNS:no listener

All global service managers may be down. Verify that the global service managers are running.

#### GSM-45034: Connection to GDS catalog is not established

The GDS catalog database or its listener may be down. Verify that the GDS catalog database and its local listener are running.

#### GSM-45054: GSM error or NET-40006: unable to start GSM

The GDS catalog database or its listener may be down. Verify that the GDS catalog database and its local listener are running.

### Solutions for General Issues

This section contains information for solving some general issues you might encounter, such as:

#### Connecting to GDS Configuration Databases When No Global Service Managers Are Running

You need multiple address lists; the first list should be exclusively regional global service manager listeners, the second list contains global service manager listeners of the buddy region and the third list contains local listeners.

You can always connect through a global service manager while it is up, and only fail over to local listeners when all global service manager listeners are down.

##### Template:

    (DESCRIPTION=
      (FAILOVER=on)
      (ADDRESS_LIST=
        (LOAD_BALANCE=ON)
        (ADDRESS=(global_protocol_address_information))
        (ADDRESS=(global_protocol_address_information))
        (ADDRESS=(global_protocol_address_information))
       )
      (ADDRESS_LIST=
        (LOAD_BALANCE=ON)
        (ADDRESS=(global_protocol_address_information))
        (ADDRESS=(global_protocol_address_information))
        (ADDRESS=(global_protocol_address_information))
       )
      (ADDRESS_LIST=
        (LOAD_BALANCE=ON)
        (ADDRESS=(local_protocol_address_information))
        (ADDRESS=(local_protocol_address_information))
       )
      (CONNECT_DATA=
       (SERVICE_NAME=global_service_name)
       (REGION=region_name)))

##### Example:

    (DESCRIPTION=
         (FAILOVER=on)
         (ADDRESS_LIST=
           (LOAD_BALANCE=ON)
           (ADDRESS=(HOST=gsmhost1)(PORT=1523)(PROTOCOL=TCP))
           (ADDRESS=(HOST=gsmhost2)(PORT=1523)(PROTOCOL=TCP))
           (ADDRESS=(HOST=gsmhost3)(PORT=1523)(PROTOCOL=TCP))
          )
         (ADDRESS_LIST=
           (LOAD_BALANCE=ON)
           (ADDRESS=(HOST=gsmhost4)(PORT=1523)(PROTOCOL=TCP))
           (ADDRESS=(HOST=gsmhost5)(PORT=1523)(PROTOCOL=TCP))
           (ADDRESS=(HOST=gsmhost6)(PORT=1523)(PROTOCOL=TCP))
          )
         (ADDRESS_LIST=
           (LOAD_BALANCE=ON)
           (ADDRESS=(HOST=server1)(PORT=1521)(PROTOCOL=TCP))
          )
         (CONNECT_DATA=
          (SERVICE_NAME=sales_read_service.dbpoolora.oradbcloud)
          (REGION=WEST)))

**Note:**

In the case of an Oracle RAC enabled GDS database, the third address list contains the local Oracle RAC database's SCAN listeners.

#### Connecting to Catalog Databases When No Global Service Managers Are Running

Local listener enables access to the GDS catalog database even when global service managers are down.

This access may be needed for any DB Administration/maintenance activities on the catalog database when global service managers are not running.

### Obtaining the Running Status of Global Data Services Components

The `status` command can be used to obtain the running status of the GDS components.

    GDSCTL>status gsm

    GDSCTL>status service

    GDSCTL>status database

### Viewing Static Configuration Information for Global Data Services Components

The `gdsctl config` command can be used to obtain the static configuration information of various GDS components.

    GDSCTL>config

    GDSCTL>config gsm

    GDSCTL>config region

    GDSCTL>config gdspool

    GDSCTL>config database

    GDSCTL>config service

    GDSCTL>config invitednode

### Enabling and Disabling Tracing on a Global Service Manager

You can enable tracing using the `set trace_level` command.

    GDSCTL>set trace_level -gsm gsm_name SUPPORT

The `SUPPORT` option provides trace with troubleshooting information for Oracle Support Services. The other options are `ADMIN` and `USER`.

To disable tracing:

    GDSCTL>set trace_level -gsm gsm_name OFF

### Using Global Service Manager Log and Trace Files

The exact location of a given global service manager's log and trace files can be obtained using the `status gsm` command as shown in the following example.

    GDSCTL>status gsm

    Alias                     MYGSM
    Version                   12.1.0.0.2
    Start Date                13-OCT-2012 12:20:16
    Trace Level               support
    Listener Log File         /scratch/oracle/diag/gsm/myhost/mygsm/alert/log.xml
    Listener Trace File       /scratch/oracle/diag/gsm/myhost/mygsm/trace/ora_1829_
     47542149303936.trc
    Endpoint summary          (ADDRESS=(HOST=myhost.com)(PORT=1571)(PROTOCOL=tcp))
    GSMOCI Version            0.1.7
    Mastership                N
    Connected to GDS catalog  Y
    Process Id                1833
    Number of reconnections   0
    Pending tasks.     Total  0
    Tasks in  process. Total  0
    Regional Mastership       TRUE
    Total messages published  34261
    Time Zone                 -07:00
    Orphaned Buddy Regions:   None
    GDS region                east
    Network metrics:
       Region: euro RTT:34 Bandwidth:40

In this example `myhost` is the global service manager host name and `mygsm` is the name of the global service manager.

The text based listener log can be found in `/scratch/oracle/diag/gsm/``hostname``/``gsm_name``/trace` directory. The file is called `alert_gsm*.log` (for example, `alert_gsm1.log`)

### Using SYS_CONTEXT Parameters in a GDS Environment

For a session established using a connection to a global service, some parameters of namespace USERENV have values that are different from values set when connecting to a local service on the same database. The different values for a global service are set to make the database pool appear to clients as a single database with many instances. This was done to provide backward compatibility with pre-12c clients which expect multiple instances of a service to exist only on an Oracle RAC database.

When a client connects to a global service, GDS sets the following in the session context differently.

- DB_UNIQUE_NAME and DB_DOMAIN are set to \<gdspool_name\>.\<config_name\>

- INSTANCE is set to a system generated number \<inst_num\> which is unique within a GDS configuration

- INSTANCE_NAME is set to \<gdspool_name\>%\<virtual_instance_num\>

- SERVICE_NAME is set to \<region_name\>%\<service_name\>
