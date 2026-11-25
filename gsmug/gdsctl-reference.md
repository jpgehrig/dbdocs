This appendix includes a complete reference of the Global Data Services utility (`GDSCTL`) commands for use with a Global Data Services or Oracle Sharding configuration.

### add brokerconfig

Adds an Oracle Data Guard broker configuration to a Global Data Services pool.

#### Syntax

    add brokerconfig -connect connect_identifier
                     [-pwd password]
                     [-gdspool gdspool_name]
                     [-region region_name]
                     [-savename]
                     [-force]

#### Options

Table C-1 GDSCTL add brokerconfig Options

| Option                          | Description                                                                                                                                                                                                                                                                                                                         |
|:--------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-connect ``connect_identifier` | Specify an Oracle Net connect descriptor or net service name that resolves to a connect descriptor for a database in the broker configuration.                                                                                                                                                                                      |
| `-force`                        | If specified, the existing GDS configuration is deleted. Deletes an existing, running SDB, and should only be used if you want to get rid of the entire SDB.                                                                                                                                                                        |
| `-gdspool ``gdspool_name`       | The pool to which the databases of the Oracle Data Guard broker configuration are to be added.<br>If the specified Global Data Services pool already contains databases or another configuration, GDSCTL returns an error.                                                                                                          |
| `-pwd ``password`               | The password for the GSMUSER. If `-pwd` is not specified, then you are prompted for the password.                                                                                                                                                                                                                                   |
| `-region ``region_name`         | The Global Data Services region to which the databases belong. If you specify a region, then all the databases are added to that region. If you do not specify a region, then all databases are added with a region of UNASSIGNED. If the region is UNASSIGNED, then you must use the modify database command to change the region. |
| `-savename`                     | Specify this option to store a net service name specified with the `-connect` option in the Global Data Services catalog, rather than the connect descriptor mapped to that net service name.                                                                                                                                       |

#### Usage Notes

- You must connect to the Global Data Services catalog database as a user with the pool administrator privileges, the GSMUSER database account, using the connect command before running the `add brokerconfig` command. You should use the `CONNECT` command to connect to the GSMUSER for the database that you are adding the broker configuration for.

- If a GDS pool already has databases or another configuration, an error is returned. If `-region` is specified, it defines only the region of primary database. If there is more than one region in catalog, GDS region property of standbys will be unassigned. The user will have to use modify database to specify GDS region.

#### Examples

Add the Oracle Data Guard broker configuration for the DB1 database to the Global Data Services pool MYREADERFARM and the WEST region.

    GDSCTL> add brokerconfig -connect 192.168.1.1:1521:sid -region west -gdspool myreaderfarm

#### Exceptions or Error Codes

GDSCTL returns the errors listed below if you use this command incorrectly.

Table C-2 GDSCTL add brokerconfig Exceptions or Error Codes

| Exception     | Description                                                                                                                                                                                                                                                    |
|:--------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ERROR-44866` | A pool can only contain one Data Guard broker configuration. If a Global Data Services pool already contains an Oracle Data Guard broker configuration, then GDSCTL returns error 44866 because a database must be added using Oracle Data Guard in this case. |

### add cdb

Add a cdb to the shard catalog.

#### Syntax

    add cdb -connect connect_identifier
             [-pwd gsmrootuser_pwd]
             [-savename]
             [-cpu_threshold cpu]
             [-disk_threshold disk]
             [-rack rack_id]
             [-force]

#### Options

Table C-3 GDSCTL add cdb Options

| Option                          | Description                                                                                                                                                                                                                                                                                  |
|:--------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-connect ``connect_identifier` | Specify an Oracle Net connect descriptor or net service name that resolves to a connect descriptor for the database being added as the shard.                                                                                                                                                |
| `-pwd ``gsmrootuser_pwd`        | Enter the GSMROOTUSER password. If not specified, the user is prompted for the password.                                                                                                                                                                                                     |
| `-savename`                     | Store in the shard catalog a net service name specified with the `-connect` option rather than the connect descriptor mapped to that net service name.                                                                                                                                       |
| `-force`                        | If specified, the existing GDS and sharding configuration on the shard and in the shard catalog with information about this shard will be rewritten.                                                                                                                                         |
| `-cpu_threshold ``cpu`          | Specify the CPU Utilization percentage threshold.                                                                                                                                                                                                                                            |
| `-disk_threshold ``disk`        | Specify the average latency in milliseconds of a synchronous single-block read.                                                                                                                                                                                                              |
| `-rack ``rack_id`               | Specify an identifier of a rack (hardware cabinet), or another physical grouping of nodes with similar availability characteristics. If specified, GDS will enforce that databases that contain replicated data are not placed in the same rack. If this is not possible an error is raised. |

#### Usage Notes

`ADD CDB` adds metadata about a CDB to a sharding catalog. This command is only necessary if you intend to deploy a PDB as a shard with the `-cdb` option in the `ADD SHARD` command. CDBs can support multiple PDB shards from different sharded databases; however, this support is limited to only one PDB shard from a given sharded database for each CDB.

#### Examples

Adds a CDB called db11 to the shard catalog.

    GDSCTL> add cdb -connect db11 -pwd gsmrootuser_pwd

### add credential

Adds a credential which can be used by the remote scheduler agent to execute shard jobs.

#### Syntax

    add credential -credential credential_name
                   -osaccount account_name
                   -ospassword password
                  [-windows_domain domain_name]

#### Options

Table C-4 GDSCTL add credential Options

| Option                          | Description                                                                                      |
|:--------------------------------|:-------------------------------------------------------------------------------------------------|
| `-credential ``credential_name` | Specify the name of the credential to add.                                                       |
| `-osaccount ``account_name`     | Specify the operating system account which will be used for remote jobs.                         |
| `-ospassword ``password`        | Specify the corresponding password for the account.                                              |
| `-windows_domain ``domain_name` | If a Windows account has been specified, specify the corresponding domain name for that account. |

#### Usage Notes

This command adds a credential which will be used to execute jobs on sharded hosts in response to administrative commands. The operating system account may be any valid account on the remote host which is in the OSDBA group; the account does not need to be enabled for interactive login unless it is used for other purposes. A specific non-interactive account may be created for use with the remote scheduler, if desired. The OS password must be a valid and current password for the specified account.

If the specified credential already exists, the command returns an error.

#### Examples

Add a credential named east_region_cred.

    GDSCTL> add credential –credential east_region_cred –osaccount agent_user
     –ospassword password

### add database

Adds databases to a Global Data Services region and Global Data Services pool.

#### Syntax

    add database -connect connect_identifier
                [-region region_name]
                [-gdspool gdspool_name]
                [-pwd password]
                [-savename]
                [-cpu_threshold cpu]
                [-disk_threshold disk]

#### Options

Table C-5 GDSCTL add database Options

| Option                          | Description                                                                                                                                                                                   |
|:--------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-connect ``connect_identifier` | Specify an Oracle Net connect descriptor or net service name that resolves to a connect descriptor for the database being added.                                                              |
| `-cpu_threshold ``cpu`          | Specifies CPU Utilization percentage threshold.                                                                                                                                               |
| `-disk_threshold ``disk`        | Specifies the average latency in milliseconds of a synchronous single-block read.                                                                                                             |
| `-gdspool ``gdspool_name`       | The Global Data Services pool to which the database belongs.                                                                                                                                  |
| `-pwd ``password`               | The password for the GSMUSER. If `-pwd` is not specified, then you are prompted for the password.                                                                                             |
| `-region ``region_name`         | The Global Data Services region to which the database belongs.                                                                                                                                |
| `-savename`                     | Specify this option to store a net service name specified with the `-connect` option in the Global Data Services catalog, rather than the connect descriptor mapped to that net service name. |

#### Usage Notes

- You must connect to the Global Data Services catalog database as a user with the pool administrator privileges, using the connect command before running this command.

- If `-savename` is not specified, then GDSCTL replaces what you specify for the net service name with the full connection string before saving the configuration to the catalog.

- The default for GDSCTL is for `autovncr` to be enabled for the catalog. If `autovncr` has been disabled for the catalog, before configuring Global Data Services pools and adding databases to the Global Data Services configuration, the nodes where those databases run must be part of the valid node checking for registration (VNCR) list for database registration. Use the add invitednode (add invitedsubnet) command to define the valid nodes.

#### Example

Adds database DB1 to the WEST region and Global Data Services pool MYREADERFARM.

    GDSCTL> add database -connect 127.0.0.1:1521:db1 -region west -gdspool
       myreaderfarm

Adds a database using `myalias` instead of the IP address connection string.

    GDSCTL> add database -connect myalias -gdspool myreaderfarm

#### Exceptions or Error Codes

GDSCTL returns the errors listed below if you use this command incorrectly.

Table C-6 GDSCTL add database Exceptions or Error Codes

| Exception     | Description                                                                                                                                                                                                                                                                                                                                             |
|:--------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ERROR-44866` | If a pool already contains an Oracle Data Guard broker configuration, then GDSCTL returns an error; you must add databases using Oracle Data Guard in this case. That is, if a pool contains an Oracle Data Guard broker configuration, then additional databases can only be added to the pool by adding them to that Data Guard broker configuration. |
| `ERROR-44868` | If the database being added is part of a Oracle Data Guard broker configuration, then GDSCTL returns an error; you must use the add brokerconfig command in this case.                                                                                                                                                                                  |

### add file

Adds the contents of a file to the catalog which can be used by subsequent GDSCTL commands.

#### Syntax

    add file -file file_name
             -source local_filename

#### Options

Table C-7 GDSCTL add file Options

| Option                     | Description                                                                                  |
|:---------------------------|:---------------------------------------------------------------------------------------------|
| `-file ``file_name`        | Specify the name of the file object to add.                                                  |
| `-source ``local_filename` | Specify an operating system file name specifying a file local to the machine running GDSCTL. |

#### Usage Notes

This command creates a named file object in the catalog and associates the contents of an operating system file with that object by opening the file and storing its contents in the catalog. If the contents of the operating system file change, the MODIFY FILE command can be used to reload the contents into the catalog.

If the specified file object already exists, the command returns an error.

#### Examples

Add a file named `east_region_db_params` from the local source file `/tmp/dbca_params.txt`

    GDSCTL> add file -file east_region_db_params -source /tmp/dbca_params.txt

### add gdspool

Adds a Global Data Services pool to the Global Data Services framework.

#### Syntax

    add gdspool -gdspool gdspool_name_list
               [-users user_list]

#### Options

Table C-8 GDSCTL add gdspool Options

| Option                         | Description                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:-------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-gdspool ``gdspool_name_list` | A comma-delimited list of Global Data Services pool names.<br>A Global Data Services pool must have a unique name within its GDS configuration. If you do not specify a name for the pool when you create it, then the name defaults to `oradbpool`. The pool name can be up to 30 bytes long and can be any valid identifier (an alphabetical character followed by zero or more alphanumeric ASCII characters or the underscore (\_)). |
| `-users ``user_list`           | A comma-delimited list of users that are granted the pool administrator role.                                                                                                                                                                                                                                                                                                                                                            |

#### Usage Notes

- A default GDS pool, DBPOOLORA, will be created automatically when a GDS catalog is created using create gdscatalog.

- You must connect to the Global Data Services catalog database as a user with the Global Data Services administrator privileges, using the connect command before running this command.

- The default for GDSCTL is for `autovncr` to be enabled for the catalog. If `autovncr` has been disabled for the catalog, then before configuring Global Data Services pools and adding databases to the Global Data Services configuration, the nodes where those databases run must be part of the valid node checking for registration (VNCR) list for database registration. Use the add invitednode (add invitedsubnet) command to define the valid nodes.

#### Example

Add a Global Data Services pool named MYREADERFARM to the configuration:

    GDSCTL> add gdspool -gdspool myreaderfarm

### add gsm

Adds a global service manager to the Global Data Services framework.

#### Syntax

    add gsm -gsm gsm_name
            -catalog connect_id
           [-pwd password]
           [-wpwd password]
           [-region region_name]
           [-localons ons_port]
           [-remoteons ons_port]
           [-listener listener_port]
           [-endpoint gmsendpoint]
           [-remote_endpoint remote_endpoint]
           [-trace_level level]

#### Options

Table C-9 GDSCTL add gsm Options

| Option                               | Description                                                                                                                                                                                                                                                                           |
|:-------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-catalog ``connect_id`              | Specify the connect identifier for the Global Data Services catalog database. If a network service name is specified, it must be resolvable by the local naming method to a connect descriptor that allows the global service manager being added to connect to the catalog database. |
| `-endpoint ``gsmendpoint`            | Specifies the protocol address that the global services manager listens on for client connection requests. If you use this option, the value that you specify overrides the default endpoint.                                                                                         |
| `-gsm ``gsm_name`                    | Specify the name of the global service manager that you want to add. If you do not specify a name, then GDSCTL uses the current global service manager name for the session (specified with the command set gsm.                                                                      |
| `-listener ``listener_port`          | Specify the listener port. The default port is 1522.                                                                                                                                                                                                                                  |
| `-localons ``ons_port`               | Specify the local ONS port. If you do not specify this option, then GDSCTL uses the default ONS port (which is 6123 on most platforms).                                                                                                                                               |
| `-pwd ``password`                    | Specify the password for the `GSMCATUSER`. If you do not specify a password, then you are prompted to enter one.                                                                                                                                                                      |
| `-region ``region_name`              | Specify the region to which the global service manager belongs. The value for `region_name` must match the name of an existing Global Data Services region. If you do not specify a region, then GDSCTL adds the global service manager without assigning a region.                   |
| `-remote_endpoint ``remote_endpoint` | Specifies the protocol address that is used by the global service manager to receive database registration requests and communicate with other global service managers in the configuration. If you use this option, the value that you specify overrides the default endpoint.       |
| `-remoteons ``ons_port`              | Specify the remote ONS port. If you do not specify this option, then GDSCTL uses the default ONS port (which is 6234 on most platforms).                                                                                                                                              |
| `-trace_level ``level`               | Specify the global service manager trace level (to be used as directed by Oracle Support Services).                                                                                                                                                                                   |
| `-wpwd` `password`                   | Specify a password to protect the global service manager wallet. If a wallet password is not specified, a system-generated password is used instead. Note that if a password is specified with this option, the wallet cannot be modified without supplying that password.            |

#### Usage Notes

- You must specify the Global Data Services catalog database when using this command.

- You must run this command, locally, on the computer where you want to add the global service manager.

- You must have operating system privileges on the computer where you want to add the global service manager to run this command.

- When you run this command, GDSCTL connects to the Global Data Services catalog as the GSMCATUSER user and prompts you for the GSMCATUSER password.

#### Example

Add a global service manager named gsm1, specifying the location of the Global Data Services catalog database, DB1.

    GDSCTL> add gsm -gsm gsm1 -catalog 127.0.0.1:1521:db1

### add invitednode (add invitedsubnet)

Adds host address or subnet information to the valid node checking for registration (VNCR) list in the catalog, before starting the first global service manager, by establishing a direct connection to the Global Data Services catalog database.

#### Syntax

    add {invitednode | invitedsubnet}
                [-group group_name]
                [-catalog catalog_dbname [-user user_name/password]]
              vncr_id

#### Options

Table C-10 GDSCTL add invitednode (add invtitedsubnet) Options

| Option                               | Description                                                                                                                                                                                                                                                                                                                                                                                              |
|:-------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-catalog ``catalog_dbname`          | Specify the Global Data Services catalog database net alias or connect string. If you enter an invalid address or connect string, then GDSCTL uses the pre-established connection created with the connect command.                                                                                                                                                                                      |
| `-group ``group_name`                | Specify an alias which defines a group of invited nodes. This alias can be referenced in other commands related to invited nodes.                                                                                                                                                                                                                                                                        |
| `-user ``user_name``[/``password``]` | Specify the user credentials for the Global Data Services administrator in the catalog database. If you do not specify a user or a password, then GDSCTL prompts you this information.                                                                                                                                                                                                                   |
| `vncr_id`                            | Specify the list of nodes that can register with the global service manager. The list can include host names or CIDR notation for IPv4 and IPv6 addresses. The wildcard format (\*) is supported for IPv4 addresses. The presence of a host name in the list results in the inclusion of all IP addresses mapped to the host name. The host name should be consistent with the public network interface. |

#### Usage Notes

- You must connect to the Global Data Services catalog database as a user with the pool administrator privileges, using the connect command before running this command.

- The default for GDSCTL is that `autovncr` is enabled for the catalog. If `autovncr` has been disabled for the catalog, before configuring Global Data Services pools and adding databases to the Global Data Services configuration, then the nodes where those databases run must be part of the valid node checking for registration (VNCR) list for database registration. Use the add invitednode (add invitedsubnet) command to define the valid nodes.

- VNCR enables or denies access from specified IP addresses to Oracle services. See [Oracle Database Net Services Administrator's Guide](../netag/index.md) for more information about VNCR.

#### Examples

Add the netmask 255.255.255.248 to the catalog.

    GDSCTL> add invitednode 255.255.255.248

Add the server east1.example.com to the catalog in the alias group EAST_SRV.

    GDSCTL> add invitednode east1.example.com

Add the server east2.example.com to the catalog in the alias group EAST_SRV.

    GDSCTL> add invitednode east2.example.com

### add region

Adds a region to a Global Data Services framework or an Oracle Sharding configuration.

#### Syntax

    add region -region region_list
              [-buddy region_name]

#### Options

Table C-11 GDSCTL add region Options

| Option                  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|:------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-buddy ``region_name`  | Specify the name of the buddy region.                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `-region ``region_list` | Specify a comma-delimited list of Global Data Services region names.<br>A Global Data Services region should have a name that is unique within the corresponding Global Data Services configuration. If no name is specified at the first region creation time, the default name, oraregion, is given to the region. The region name can be up to 30 characters long and can be any valid identifier - an alphabetical character followed by zero or more alphanumeric ASCII characters or underscore (\_). |

#### Usage Notes

- When the Global Data Services catalog is created using the create gdscatalog command, the default REGIONORA region is created automatically.

- You must connect to the Global Data Services catalog database as a user with the Global Data Services administrator privileges, using the command connect before running this command

#### Example

Add two Global Data Services regions, EAST and WEST to the current configuration:

    GDSCTL> add region -region east,west

### add service

Adds a global service to a Global Data Services pool.

#### Syntax

    add service
               [-gdspool gdspool_name]
               -service service_name
               (-preferred_all | (-preferred dbname_list [-available dbname_list]))
               [-locality {ANYWHERE | LOCAL_ONLY [-region_failover]}]
               [-role {PRIMARY | PHYSICAL_STANDBY [-failover_primary] |
                  LOGICAL_STANDBY | SNAPSHOT_STANDBY}]
               [-lag {lag_value | ANY}]
               [-notification {TRUE | FALSE}]
               [-rlbgoal {SERVICE_TIME | THROUGHPUT}]
               [-dtp {TRUE | FALSE}]
               [-sql_translation_profile stp_name]
               [-clbgoal {SHORT | LONG}]
               [-tafpolicy {BASIC | NONE | PRECONNECT}]
               [-policy policy]
               [-failovertype {NONE | SESSION | SELECT | TRANSACTION | AUTO}]
               [-failovermethod {NONE | BASIC}]
               [-failoverretry failover_retries]
               [-failoverdelay failover_delay]
               [-edition edition_name]
               [-commit_outcome {TRUE | FALSE}]
               [-retention retention_seconds]
               [-session_state {DYNAMIC | STATIC | AUTO}]
               [-replay_init_time replay_init_time]
               [-pdbname pdbname]
               [-drain_timeout]
               [-stop_option  {NONE,IMMEDIATE, TRANSACTIONAL}]
               [-failover_restore {NONE|LEVEL1|AUTO}]
               [-table_family family]

#### Options

Table C-12 GDSCTL add service Options

| Option                                                                                               | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:-----------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-available ``dbname_list`                                                                           | Specify a comma-delimited list of available databases on which the service runs if the preferred databases are not available. You cannot specify a list of available instances, only databases. You can use the modify service command with the `-server_pool` parameter to specify instance-level preferences.<br>The list of available databases must be mutually exclusive with the list of preferred databases.<br>You cannot use this option with the `-preferred_all` option.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-clbgoal {SHORT | LONG}`                                                                            | Connection Load Balancing Goal. Use a value of `SHORT` for this parameter for run-time load balancing, or if using an integrated connection pool. Use a value of `LONG` for this parameter for long running connections, such as batch jobs, that you want balanced by the number of sessions for each node for the service.<br>The default value for this option, if not specified, is `SHORT`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-commit_outcome {TRUE | FALSE}`                                                                     | Enable Transaction Guard; when set to `TRUE`, the commit outcome for a transaction is accessible after the transaction's session fails due to a recoverable outage.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `—drain_timeout`                                                                                     | Set drain time in seconds.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `-dtp {TRUE | FALSE}`                                                                                | Indicates whether Distributed Transaction Processing should be enabled for this service. This service can either be a service in a policy-managed database or a preferred service on a single node in an administrator-managed database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `-edition ``edition_name`                                                                            | Specify the initial session edition of the service.<br>When an edition is specified for a service, all subsequent connections that specify the service use this edition as the initial session edition. However, if a session connection specifies a different edition, then the edition specified in the session connection is used for the initial session edition.<br>GDSCTL does not validate the specified edition name. During connection, the connect user must have `USE` privilege on the specified edition. If the edition does not exist or if the connect user does not have `USE` privilege on the specified edition, then an error is raised.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `-failover_primary`                                                                                  | If you set the `-role` option to `PHYSICAL_STANDBY`, then you can use this option to enable the service for failover to the primary database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `-failoverdelay ``failover_delay`                                                                    | For Application Continuity and TAF, this parameter specifies the time delay (in seconds) between reconnect attempts for each incident at failover.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `-failovermethod {NONE | BASIC}`                                                                     | TAF failover method (for backward compatibility only).<br>If the failover type (`-failovertype`) is set to a value other than `NONE`, then you should choose `BASIC` for this parameter.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `-failoverretry ``failover_retries`                                                                  | For Application Continuity and TAF, this parameter determines the number of attempts to connect after an incident.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `-failovertype {NONE | SESSION | SELECT | TRANSACTION}`                                              | Specify the failover type.<br>To enable Application Continuity for Java, set this parameter to `TRANSACTION`. To enable Transparent Application Failover (TAF) for OCI, set this parameter to `SELECT` or `SESSION`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `-gdspool ``gdspool_name`                                                                            | Specify the name of the Global Data Services pool to which you want to add a service. If the pool name is not specified and there is only one `gdspool` with access granted to the user, then this the `gdspool` with access granted is used as the default `gdspool`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `-lag {``lag_value`` | ANY}`                                                                         | Specify the lag for the service in seconds. You can use the keyword `ANY` to indicate that there is no upper threshold on the lag time. This parameter specifies the maximum lag that a provider of this service may have. The service cannot be provided by a database whose lag exceeds this value.<br>The default value for `lag`, if not specified, is `ANY`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `-locality {ANYWHERE | LOCAL_ONLY}`                                                                  | Specify the service region locality. If you do not specify this option, then GDSCTL uses the default value of `ANYWHERE` for the service.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `-notification {TRUE | FALSE}`                                                                       | Enable Fast Application Notification (FAN) for OCI connections.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `-pdbname ``pdb_name`                                                                                | Specify the pluggable database name.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `-policy {AUTOMATIC | MANUAL}`                                                                       | Specify the management policy for the service.<br>If you specify `AUTOMATIC` (the default), then the service automatically starts when the database restarts, either by a planned restart or after a failure. Automatic restart is also subject to the service role.<br>If you specify `MANUAL`, then the service is never automatically restarted upon planned restart of the database. A `MANUAL` setting does not prevent the global service manager from monitoring the service when it is running and restarting it if a failure occurs.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `-preferred ``dbname_list`                                                                           | Specify a comma-delimited list of preferred databases on which the service runs. You cannot specify preferred instances, only databases. You can use the modify service command to specify instance-level preferences.<br>The list of preferred databases must be mutually exclusive with the list of available databases.<br>You cannot use this option with the `-preferred_all` option.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `-preferred_all`                                                                                     | Specifies that all the databases in the Global Data Services pool are preferred databases. Any databases you later add to the pool are configured as preferred databases for this service.<br>You cannot use this option with the `-preferred` and `-available` options.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `-region_failover`                                                                                   | Indicates that the service is enabled for region failover. You can only use this option when you specify `LOCAL_ONLY` for the `-locality` option.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `-replay_init_time ``replay_init_time`                                                               | For Application Continuity, this parameter specifies the time (in seconds) after which replay cannot be initiated. The default value is 300 seconds.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `-retention ``retention_seconds`                                                                     | If commit_outcome is set to `TRUE`, then this parameter determines the amount of time (in seconds) that the commit outcome is retained in the database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `-rlbgoal {SERVICE_TIME | THROUGHPUT}`                                                               | Run-time Load Balancing Goal (for the Load Balancing Advisory). Set this parameter to `SERVICE_TIME` to balance connections by response time. Set this parameter to `THROUGHPUT` to balance connections by throughput.<br>If you do not use this option, then the value defaults to `SERVICE_TIME` for the run-time load balancing goal.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `-role {[PRIMARY] | [PHYSICAL_STANDBY] [-failover_primary] | [LOGICAL_STANDBY] |[SNAPSHOT_STANDBY]}` | Specify the database role that the database must be for this service to start on that database. This applies only to Global Data Services pools that contain an Oracle Data Guard broker configuration.<br>See Also: [Oracle Data Guard Concepts and Administration](../sbydb/introduction-to-oracle-data-guard-concepts.md) for more information about database roles                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `-service ``service_name`                                                                            | Specify the name of the global service.<br>The service name specified in the `add service` command can be domain qualified (for example, sales.example.com) or not (for example, sales). If the specified name is not domain qualified, the service is created with the default domain name `<GDS_pool_name>.<GDS_configuration_name>`, however the shorter non-domain qualified name can be used with subsequent `gdsctl` commands to manage the service. If the specified name is domain qualified, the full domain qualified service name must be used in all subsequent `gdsctl` commands used to manage the service.<br>A global service name must be unique within a GDS pool and when qualified by domain, must also be unique within a GDS configuration. A global service cannot be created at a database if a local or global service with the same name already exists at that database.<br>A global service name can contain alphanumeric characters, underscore (\_), and period (.). The first character must be alphanumeric. The maximum length of a global service name is 64 characters. The maximum length of a domain qualified global service name is 250 characters.<br>An Oracle Net connect descriptor used to connect to a global service must contain a domain qualified service name. |
| `-session_state {DYNAMIC | STATIC}`                                                                  | For Application Continuity, this parameter specifies whether the session state that is not transactional is changed by the application. A setting of `DYNAMIC` is recommended for most applications.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `-sql_translation_profile ``stp_name`                                                                | Use this option to specify a SQL translation profile for a service that you are adding after you have migrated applications from a non-Oracle database to an Oracle database.<br>This option corresponds to the SQL translation profile parameter in the `DBMS_SERVICE` service attribute.<br>Notes:<br>• Before using the SQL translation feature, you must migrate all server-side application objects and data to the Oracle database.<br>• Use the command config service to display the SQL translation profile.<br>See Also: [Oracle Database SQL Translation and Migration Guide](../drdaa/SQL-translation-framework-overview.md) for more information about SQL translation                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `—stop_option`                                                                                       | Set the default stop option to `NONE`, `IMMEDIATE`, or `TRANSACTIONAL`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `-table_family``family`                                                                              | Specifies the name of the table family as a property of the service. This parameter takes one of the table family values (root table schema.name) as shown in the `CONFIG TABLE FAMILY` output.<br>If the schema name or the table name is case-sensitive, use two-level quotes (single quotes outside, double quotes inside) around the whole string, for example, '"TESTUSER1.Customers6"'. No quotes are needed if neither name is case sensitive.<br>If this parameter is not specified, but there is currently only one table family, the service created with the `add service` command is automatically associated with that table family.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `-tafpolicy {BASIC | NONE }`                                                                         | TAF policy specification (for administrator-managed databases only).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |

#### Usage Notes

Database-specific options cannot be set at this level. The `modify service` command must be used to set database-specific options.

One of `-preferred_all` or `-preferred` must be specified. If `-preferred_all` is specified, then all databases in the pool are preferred for this global service (databases inserted into the pool will also have this global service added).

In Oracle Sharding, note that when there is no `table_family` parameter specified, the service is not associated with any table family, and the value of the property is set to NULL. This is the case for user-defined and composite sharding, where there is always only one table family, and can also be the case when there is only one table family in system-managed sharding. When a table family is deleted (that is, the root table of the table family is dropped) the `table_family` property of the service is reset to NULL.

#### Examples

Add a service named `sales_report` to the Global Data Services pool MYREADERFARM with a value of ANYWHERE for the locality.

    GDSCTL> add service -gdspool myreaderfarm -service sales_report -locality ANYWHERE

Add a service named `daily_sales_rept` to the Global Data Services pool MYDGPOOL with preferred instance set to DB1 and the available instances set to DB3 and DB4. The service should use the basic transaction failover policy.

    GDSCTL> add service -gdspool mydgpool -s daily_sales_rept -preferred db1
      -available db3,db4 -tafpolicy BASIC

In a system-managed sharded database, the table family ID parameter is specified as a property of the service.

    GDSCTL> add service –gdspool shdpool –table_family sales.customer -service sales –preferred_all -locality ANYWHERE

**See Also:**

[Creating a Global Service](global-data-services-admin.md)

### add shard

Add a shard to the shard catalog.

#### Syntax

    add shard -connect connect_identifier
             [-pwd password]
             [-savename]
             [-region region_name]
             [-force]
             [-cdb cdb_name]
             [-cpu_threshold cpu]
             [-disk_threshold disk]
             [{-shardgroup shardgroup_name | -shardspace shardspace_name}]
             [-deploy_as {PRIMARY | STANDBY | ACTIVE_STANDBY}]
             [-rack rack_id]
             [-replace old_db_name]
             [-gg_service (http|https):ogg_host:sm_port/GGHOME_directory]

#### Options

Table C-13 GDSCTL add shard Options

| Option                                                                | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|:----------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-connect ``connect_identifier`                                       | Specify an Oracle Net connect descriptor or net service name that resolves to a connect descriptor for the database being added as the shard.                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `-pwd ``password`                                                     | Enter the GSMUSER password. If not specified, the user is prompted for the password.                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `-savename`                                                           | Store in the shard catalog a net service name specified with the `-connect` option rather than the connect descriptor mapped to that net service name.                                                                                                                                                                                                                                                                                                                                                                                                          |
| `-region ``region_name`                                               | Specify the GDS region that this shard belongs to. This parameter is only valid for user-defined sharding. For other sharing methods it is specified per shardgroup.                                                                                                                                                                                                                                                                                                                                                                                            |
| `-force`                                                              | If specified, the existing GDS and sharding configuration on the shard and in the shard catalog with information about this shard will be rewritten.                                                                                                                                                                                                                                                                                                                                                                                                            |
| `-cdb ``cdb_name`                                                     | If this parameter is used, the shard must be a PDB and the CDB must already exist in the catalog.                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `-cpu_threshold ``cpu`                                                | Specify the CPU Utilization percentage threshold.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `-disk_threshold ``disk`                                              | Specify the average latency in milliseconds of a synchronous single-block read.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `{-shardgroup ``shardgroup_name`` | -shardspace ``shardspace_name``}` | Specify the name of the shardgroup or shardspace that this shard is being added to.<br>Use `-shardspace` when using this command in a user-defined sharding configuration. Use `-shardgroup` with system-managed and composite sharding configurations.                                                                                                                                                                                                                                                                                                         |
| `-deploy_as {PRIMARY | STANDBY | ACTIVE_STANDBY}`                     | Specify the role that is assigned to a shard added to the shardgroup after deployment. This parameter is only used with Data Guard replication. The specified role will be assigned to the shard database after deployment. The valid values are:<br>• `PRIMARY` – the shard should be deployed as the primary database<br>• `STANDBY` – the shard should be deployed as a Data Guard standby (mounted)<br>• `ACTIVE_STANDBY` – the shard should be deployed as an Active Data Guard standby<br>If the parameter is not specified, the default value is STANDBY |
| `-rack ``rack_id`                                                     | Specify an identifier of a rack (hardware cabinet), or another physical grouping of nodes with similar availability characteristics. If specified, GDS will enforce that databases that contain replicated data are not placed in the same rack. If this is not possible an error is raised.                                                                                                                                                                                                                                                                    |
| `—replace ``old_db_name`                                              | This parameter specifies db_unique_name of the old shard when replacing it. The existing parameters of the `ADD SHARD` command (such as `connect`) must refer to attributes for the new (replacement) shard.<br>This parameter is not supported in an Oracle GoldenGate environment.                                                                                                                                                                                                                                                                            |
| `-gg_service (http|https):``ogg_host:sm_port/deployment`              | This parameter is mandatory for Oracle GoldenGate replication and specifies the URI for the GoldenGate Admin Server that will manage the GoldenGate replication at this shard. The format will be as follows Example:<br>`shard1.example.com:9005/shard1`.                                                                                                                                                                                                                                                                                                      |

#### Usage Notes

Before running `add shard`, you must validate the shard by running the `validateShard` procedure as described in [Using Oracle Sharding](../shard/sharding-lifecycle-management.md)

- The shard will become part of the sharded database after a `DEPLOY` command is executed, except in the case of `-replace`.

- Any databases added to a sharding configuration using `ADD SHARD` must not have ever been deployed as a shard in another configuration (unless `-replace` is specified). Re-adding a previously deployed shard will cause the `ADD SHARD` command to succeed, but the shard will be unable to successfully deploy and register with the shard director (GSM) when the `DEPLOY` command is eventually run.

- `ADD SHARD` only registers the database (shard) with GDS. Replication is not configured on a newly added database and data from other databases is not distributed to it until `DEPLOY` is run.

- With Data Guard replication, a shard can be added as a standby to a preexisting Data Guard configuration. There is no need to re-shard the data. It is expected that the shard being added is in a the correct state for configuration; the standbys should be cloned from the primary and have the same DBID. When you run `DEPLOY`, the existing primary and standby databases are matched with each other, using the DBID to form a broker configuration. If the broker has not been configured, it is configured, otherwise it is validated that it has been configured correctly. Once the broker is configured, Data Guard does its work, and it should be able to perform catch-up on the standbys if needed before bringing them online.

- See [Working with Oracle GoldenGate Sharding](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/gsmug&id=GGSAU-GUID-2C059382-7753-4EFA-B313-A6E0DAF7EA1C) in the Fusion Middleware Using the Oracle GoldenGate Microservices Architecture guide for more information about using Oracle GoldenGate with Oracle Sharding.

- When using the- replace parameter, see [Using Oracle Sharding](../shard/sharding-lifecycle-management.md) for more information about its usage.

#### Examples

Add the shard to shardgroup GROUP1 of the DB11 database.

    GDSCTL> add shard –connect db11 –shardgroup group1

Replace shard SH1 with database DB11.

    GDSCTL> add shard –replace sh1 –connect db11

### add shardgroup

Add a shardgroup to a shardspace.

#### Syntax

    add shardgroup -shardgroup shardgroup_name
                  [-region region_name]
                  [-shardspace shardspace_name]
                  [-deploy_as {PRIMARY | STANDBY | ACTIVE_STANDBY}]
                  [-repfactor number]

#### Options

Table C-14 GDSCTL add shardgroup Options

| Option                                            | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|:--------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-shardgroup ``shardgroup_name`                   | Specify the name of the shardgroup. The name must be unique across all shardspaces.<br>The shardgroup name can be up to 30 characters long and can be an alphabetical character followed by zero or more alphanumeric ASCII characters or an underscore (\_).                                                                                                                                                                                                                         |
| `-region ``region_name`                           | Specify the name of the region. If not specified, a default region will be used.                                                                                                                                                                                                                                                                                                                                                                                                      |
| `-shardspace ``shardspace_name`` `                | Specify the name of the shardspace to which to add the shardgroup.                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `-deploy_as {PRIMARY | STANDBY | ACTIVE_STANDBY}` | Specify the role that is assigned to a shard added to the shardgroup after deployment. This parameter is only used with Data Guard replication. The valid values are:<br>If the parameter is not specified, the default value is `STANDBY`<br>• `PRIMARY` – the shard should be deployed as the primary database<br>• `STANDBY` – the shard should be deployed as a Data Guard standby (mounted)<br>• `ACTIVE_STANDBY` – the shard should be deployed as an Active Data Guard standby |
| `-repfactor ``number`                             | Specify the replication factor - the number of replicas for each piece of data stored in this shardgroup. This parameter can only be used with Oracle GoldenGate replication and is mandatory unless the default value of replication factor was specified in `CREATE SHARDCATALOG` command. This parameter does not apply to user-defined sharding because GoldenGate does not support that sharding methods.                                                                        |

#### Usage Notes

This command can only be used with system-managed or composite sharding, not user-defined sharding.

See [Working with Oracle GoldenGate Sharding](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/gsmug&id=GGSAU-GUID-2C059382-7753-4EFA-B313-A6E0DAF7EA1C) in the Fusion Middleware Using the Oracle GoldenGate Microservices Architecture guide for more information about using Oracle GoldenGate with Oracle Sharding.

#### Examples

Add the GROUP1 shardgroup in the WEST region within the GOLD shardspace.

    GDSCTL> add shardgroup -shardgroup group1 -region west –shardspace gold

### add shardspace

Add a shardspace to the shard catalog.

#### Syntax

    add shardspace -shardspace shardspace_name
                  [-chunks number]
                  [-protectmode dg_protection_mode]

#### Options

Table C-15 GDSCTL add shardspace Options

| Option                              | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|:------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-shardspace ``shardspace_name`` `  | Specify the name of the shardspace.<br>The shardspace name can be up to 30 characters long and can be an alphabetical character followed by zero or more alphanumeric ASCII characters or an underscore (\_).                                                                                                                                                                                                                                                                                                     |
| `-chunks ``number`                  | Specify the number of unique chunks in the shardspace. The value of `-chunks` must be greater than 2 times the size of the largest shardgroup in any shardspace.<br>This parameter does not apply to user-defined sharding. All shardgroups in a shardspace have the same number of chunks. If this parameter is not specified, the default number of chunks is determined at the time of execution of the first `DEPLOY` command and is 120 per database of the shardgroup with the biggest number of databases. |
| `-protectmode ``dg_protection_mode` | Specify the Data Guard protection mode: `MAXPROTECTION`, `MAXAVAILABILITY`,or `MAXPERFORMANCE` (default). This parameter does not apply to Oracle GoldenGate replication.                                                                                                                                                                                                                                                                                                                                         |

#### Usage Notes

The command is applicable to user-defined sharding, composite sharding that assumes multiple shardspaces, and system managed sharding when there are no other shardspaces present in the current configuration.

#### Examples

Add the GOLD shardspace with Data Guard MAXAVAILABILITY protection mode.

    GDSCTL> add shardspace –shardspace gold –protectmode maxavailability

### config

Displays the configuration data for all components defined for the configuration.

#### Syntax

    config [-support]

#### Options

Table C-16 GDSCTL config Options

| Option     | Description                                                                       |
|:-----------|:----------------------------------------------------------------------------------|
| `-support` | If specified, GDSCTL output displays additional information for support purposes. |

#### Usage Notes

When using the command, it does not matter if the components (except for the catalog database) are started. The configuration data displayed is retrieved from the catalog database.

#### Example

Display the configuration data for all components defined for the configuration.

    GDSCTL> config

### config cdb

Displays properties of a specified CDB.

#### Syntax

    config cdb [-cdb cdb_name]

#### Options

Table C-17 GDSCTL config cdb Options

| Option            | Description                  |
|:------------------|:-----------------------------|
| `-cdb ``cdb_name` | Specify the name of the cdb. |

#### Examples

Display information about CDB called cdb1.

    GDSCTL> config cdb -cdb cdb1

    Name: tstsdbyb
    Connection string: (DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)(HOST=cdb1host)(PORT=1521))
    (CONNECT_DATA=(SERVICE_NAME=cdb1.example.com)))
    SCAN address:
    ONS remote port: 0
    Disk Threshold, ms: 20
    CPU Threshold, %: 75
    Version: 18.0.0.0
    Rack:

### config chunks

Displays properties of a specified chunk.

#### Syntax

    config chunks [-support]
                ( [-shard shd] | [-shardgroup sh] | [-show_reshard] | [-cross_shard] )
                ( [-chunk chunk_id] | [-key key [-superkey superkey] )

#### Options

Table C-18 GDSCTL config chunks Options

| Option                 | Description                                                                |
|:-----------------------|:---------------------------------------------------------------------------|
| `-chunk ``chunk_id`    | Specify a numeric chunk ID.                                                |
| `-cross_shard`         | Show cross-shard placement.                                                |
| `-key ``key`           | Sharding key                                                               |
| `-shard ``shd`         | The name of the shard.                                                     |
| `-shardgroup ``sh`     | The name of the shardgroup.                                                |
| `-show_reshard`        | Display information about ongoing chunk management operations.             |
| `-superkey ``superkey` | Sharding super key. This is only needed for the composite sharding method. |
| `-support`             | If specified, GDSCTL output displays additional information.               |

#### Usage Notes

The `config chunks` command lists all of the database shards and the chunks that they contain. Some chunks are listed more than once if there are standbys that contain replicated chunks.

#### Examples

The output from `config chunks` is shown below.

    GDSCTL> config chunks

    Chunks
    ------------------------
    Database                      From      To
    --------                      ----      --
    sh1a                          1         10
    sh1b                          1         10

### config credential

Displays remote credentials currently available for shard jobs.

#### Syntax

    config credential [-support]

#### Options

Table C-19 GDSCTL config credential Options

| Option     | Description                                                  |
|:-----------|:-------------------------------------------------------------|
| `-support` | If specified, GDSCTL output displays additional information. |

#### Usage Notes

This command displays all existing remote credentials that can be used to execute sharding jobs.

#### Examples

Display credentials.

    GDSCTL> config credential

    Name            Username Windows domain
    --------------- -------- --------------
    CREDENTIAL_ONE  OraUser
    CREDENTIAL_TWO  OraUser2

### config database

Displays the static configuration data stored in the catalog for the specified database.

#### Syntax

    config database [-support]
                    [-database db_name]

#### Options

Table C-20 GDSCTL config database Options

| Syntax                | Description                                                                                                                                                                     |
|:----------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-database ``db_name` | Specify the name of a database. If you do not specify a database name, then GDSCTL displays the configuration data for all databases in the Global Data Services configuration. |
| `-support`            | GDSCTL output displays additional support information.                                                                                                                          |

#### Usage Notes

You must connect to the catalog database as a user with the pool administrator privileges, using the connect command before running this command

#### Examples

Display the static configuration data stored in the catalog for all the databases in the Global Data Services configuration.

    GDSCTL> config database

The `gdsctl config database` command returns information similar to the following:

    Name     Pool     Status     Region
    ----     ----     ------     ------
    dbcat    sales    Ok         east
    dbcat1   sales    Ok         west
    dbcat3   sales    Ok         west

### config file

Displays file objects currently available that can be specified in GDSCTL commands.

#### Syntax

    config file [-support]
                [-file file_name]

#### Options

Table C-21 GDSCTL config file Options

| Option              | Description                                                  |
|:--------------------|:-------------------------------------------------------------|
| `-file ``file_name` | The name of the file object.                                 |
| `-support`          | If specified, GDSCTL output displays additional information. |

#### Usage Notes

If the specified file object does not exist, the command returns an error.

#### Example

Display the list of files defined in the catalog database.

    GDSCTL> config file
    Name
    ------
    dbcfg1

### config gdspool

Displays the static configuration data that is stored in the catalog for the specified database pool.

#### Syntax

    config gdspool [-support]
                   [-gdspool gdspool_name]

#### Options

Table C-22 GDSCTL config gdspool Options

| Syntax                    | Description                                                                                                                                          |
|:--------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------|
| `-gdspool ``gdspool_name` | Specify the name of a database pool. If you do not specify a database pool name, then GDSCTL displays the configuration data for all database pools. |
| `-support`                | GDSCTL output displays additional support information.                                                                                               |

#### Usage Notes

You must connect to the catalog database as a user with the pool administrator privileges, using the connect command before running this command

#### Example

Display the static configuration data stored in the catalog for all Global Data Services pools.

    GDSCTL> config gdspool

The `gdsctl config gdspool` command returns output similar to the following:

    Name          Broker
    ----          ------
    dbpoolora     No
    mkt           No
    sales         No
    marketing     No

The following command shows the configuration detail of Global Data Services pool `marketing`.

    GDSCTL> config gdspool -gdspool marketing

The above example returns output similar to the following:

    GDS Pool administrators
    ------------------------

    Databases
    ------------------------
    dbcat2
    dbcat1
    dbcat3


    Services
    ------------------------
    sales_report
    sales_analysis
    sales_estimation
    sales_peragent
    sales_global

### config gsm

Displays the static configuration data stored in the catalog for the specified global service manager.

#### Syntax

    config gsm [-gsm gsm_name]
               [-support]

#### Options

Table C-23 GDSCTL config gsm Options

| Syntax            | Description                                                                                                                                                                                         |
|:------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-gsm ``gsm_name` | Specify the name of a global service manager. If you do not specify a global service manager name, then GDSCTL displays the static configuration data for all global service managers in the cloud. |
| `-support`        | If specified, GDSCTL output displays additional information.                                                                                                                                        |

#### Usage Notes

You must connect to the catalog database as a user with the Global Data Services administrator privileges, using the connect command before running this command

#### Example

Display the static configuration data stored in the catalog for the global service manager `mygsm`:

    GDSCTL> config gsm -gsm mygsm

The `gdsctl config gsm` command returns output similar to the following:

    Name: mygsm
    Endpoint 1: (ADDRESS=(HOST=stcal.us.hq.com)(PORT=1523)(PROTOCOL=tcp))
    Endpoint 2: (ADDRESS=(HOST=stcal.us.hq.com)(PORT=1523)(PROTOCOL=tcp))
    Local ONS port: 6123
    Remote ONS port: 6234
    Region: east
    Buddy
    ------------------------

### config region

Displays the static configuration data for the specified region.

#### Syntax

    config region [-region region_name]
                  [-support]

#### Options

Table C-24 GDSCTL config region Options

| Syntax               | Description                                                  |
|:---------------------|:-------------------------------------------------------------|
| `-region ``gsm_name` | Specify the name of a global service manager.                |
| `-support`           | If specified, GDSCTL output displays additional information. |

#### Example

Displays the static configuration data for the specified region.

    GDSCTL> config region -region east

Displays the following output:

    Name                          Buddy
    ----                          -----
    east

### config sdb

Displays the static configuration data stored in the catalog for the sharded database.

#### Syntax

    config sdb [-support]

#### Options

Table C-25 GDSCTL config sdb Options

| Option     | Description                                                  |
|:-----------|:-------------------------------------------------------------|
| `-support` | If specified, GDSCTL output displays additional information. |

#### Examples

The output for `config sdb` is similar to the following.

    GDSCTL> config sdb

    GDS Pool administrators
    ------------------------

    Replication Type
    ------------------------
    Data Guard

    Shard type
    ------------------------
    System-managed

    Shard spaces
    ------------------------
    shardspaceora

    Services
    ------------------------
    oltp_ro_srvc
    oltp_rw_srvc

### config service

Displays the static configuration data stored in the Global Data Services catalog for the specified services that are located in a database pool.

#### Syntax

    config service [-gdspool gdspool_name]
                   [-service service_name]
                   [-support]

#### Options

Table C-26 GDSCTL config service Options

| Syntax                    | Description                                                                                                                                                                                           |
|:--------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-gdspool ``gdspool_name` | Specify the name of the database pool that contains the services. If the name is not specified, and there is only one `gdspool` with access granted to the user, it is used as the default `gdspool`. |
| `-service ``service_name` | Specify a comma-delimited list of service names. If you do not use this option, then GDSCTL displays the configuration data for all services in the specified database pool.                          |
| `-support`                | If specified, GDSCTL output displays additional information.                                                                                                                                          |

#### Usage Notes

You must connect to the catalog database as a user with the pool administrator privileges, using the connect command before running this command

#### Examples

Show all the services in the user's Global Data Services pool:

    GDSCTL> config service

The `gdsctl config service` command returns information similar to the following:

    Name        Network name                  Pool     Started Preferred all
    ----        ------- ----                  ----     ------- --------- ---
    sales_svc1  sales_svc1.sales.oradbcloud   sales    Yes     Yes
    sales_svc2  sales_svc2.sales.oradbcloud   sales    NO      Yes
    sales_svc3  sales_svc3.sales.oradbcloud   sales    Yes     Yes
    mkt_svc1    mkt_svc1.mkt.oradbcloud       mkt      NO     Yes

Display the static configuration data stored in the Global Data Services catalog for `sales`:

    GDSCTL> config service -service sales

    Name: sales
    Network name: sales.sdhdpool.oradbcloud
    Pool: shdpool
    Started: Yes
    Preferred all: Yes
    Locality: ANYWHERE
    Region Failover: No
    Role: NONE
    Primary Failover: No
    Lag: ANY
    Runtime Balance: SERVICE_TIME
    Connection Balance: LONG
    Notification: Yes
    TAF Policy: NONE
    Policy: AUTOMATIC
    DTP: No
    Failover Method: NONE
    Failover Type: NONE
    Failover Retries:
    Failover Delay:
    Edition:
    PDB:
    Commit Outcome:
    Retention Timeout:
    Replay Initiation Timeout:
    Session State Consistency:
    SQL Translation Profile:
    Stop option: NONE
    Drain timeout:
    Table Family: sales.customer

    Supported services
    ------------------------
    Database          Preferred Status
    --------          --------- ------
    shdb              Yes       Enabled
    shdc              Yes       Enabled

### config shard

Displays properties of a specified shard.

#### Syntax

    config shard -shard shard_name
                [-support]

#### Options

Table C-27 GDSCTL config shard Options

| Option                | Description                                            |
|:----------------------|:-------------------------------------------------------|
| `-shard ``shard_name` | Specify the name of the shard.                         |
| `-support`            | GDSCTL output displays additional support information. |

#### Examples

    GDSCTL> config shard

    Name   Shard Group Status State    Region Availability
    ----   ----------- ------ -----    ------ ------------
    den17b dbs1        Ok     Deployed east   ONLINE
    den17c dbs2        Ok     Deployed east   READ ONLY

The State column in the results can have the following values:

- Created: Indicates that `add shard` or `create shard` was run, but `deploy` has not yet been run for that shard.

- Replicated: Indicates that `deploy` was run and the Data Guard broker configuration was created. No other metadata (chunks, for example) are on the shard and the shard has not yet registered with the shard director

- Sharded: Indicates that the database has successfully registered with the shard director. Creates chunk metadata for new shards, but does not start any automatic rebalancing. To manually get from Replicated to Sharded and beyond, run `GDSCTL sync -database <shard_name>`.  This is what is happening internally in this step.

- Deployed: Indicates that all DDL catchup is completed and the shard is ready for operations. At this point, any scheduled chunk moves are begun in the background. A shard can be Deployed without having been rebalanced because rebalancing is a background operation.

### config shardgroup

Displays properties of a specified shardgroup.

#### Syntax

    config shardgroup [-shardgroup shardgroup_name]
                      [-support]

#### Options

Table C-28 GDSCTL config shardgroup Options

| Option                          | Description                                            |
|:--------------------------------|:-------------------------------------------------------|
| `-shardgroup ``shardgroup_name` | Specify the name of the shardgroup.                    |
| `-support`                      | GDSCTL output displays additional support information. |

#### Examples

The `config shardgroup` command generates the following output.

    GDSCTL> config shardgroup –shardgroup northeast

    Shard Group Chunks Region Shard space
    ----------- ------ ------ -----------
    dbs1        10     east   shd1
    dbs2        10     east   shd1

By specifying a shardgroup, you get the following output.

    GDSCTL> config shardgroup -shardgroup dbs1

    Shard Group: dbs1
    Chunks: 10
    Replicas:
    Region: east
    Shard space: shd1
    Shards
    ------------------------
    Shard  Chunks
    -----  ------
    den17b 10

### config shardspace

Displays properties of a specified shardspace.

#### Syntax

    config shardspace [-shardspace shardspace_name]
                      [-support]

#### Options

Table C-29 GDSCTL config shardspace Options

| Option                          | Description                                                               |
|:--------------------------------|:--------------------------------------------------------------------------|
| `-shardspace ``shardspace_name` | Specify the name of the shardspace. Optional for system-managed sharding. |
| `-support`                      | GDSCTL output displays additional support information.                    |

#### Usage Notes

The output varies depending on whether the command is issued on a shardspace configured in a user-defined SDB.

#### Examples

The `config shardspace` command generates the following output

    GDSCTL> config shardspace

    Shard space Chunks
    ----------- ------
    shd1        10

When a shardspace is specified, the output is returned in the following format.

    GDSCTL> config shardspace -shardspace silver

    Shard Group Region Role
    ----------- ------ ----
    dbs1        east   Primary
    dbs2        east   Standby
    PROTECTION_MODE Chunks
    --------------- ------
    MaxProtection   10

### config table family

Displays information about all table families in the sharded database.

#### Syntax

    config table family

#### Examples

The `config table family` command generates the following output

    GDSCTL> config table family

    Schema   Name        ID      Shard Type
    ------   -----       -----   ----------
    sales    customer    1       System
    hr       department  25      System

### config vncr

Displays the static configuration data stored in the catalog for valid node checking for registration (VNCR).

#### Syntax

    config vncr [-group group_name]
                [-support]

#### Options

Table C-30 GDSCTL config vncr Options

| Syntax                | Description                                                                                       |
|:----------------------|:--------------------------------------------------------------------------------------------------|
| `-group ``group_name` | A group alias that defines a group of VNCRs.<br>The same alias can be used in multiple ADD calls. |
| `-support`            | GDSCTL output displays additional support information.                                            |

#### Usage Notes

You must connect to the catalog database as a user with the pool administrator privileges, using the connect command before running this command

#### Example

The `config vncr` command returns information similar to the following:

    GDSCTL> config vncr

    Name          Group ID
    ----          --------
    192.0.2.1     group_name

### configure

Sets the GDSCTL parameters.

#### Syntax

    configure [-gsmport port]
              [-timeout seconds]
              [-show]
              [-driver {THIN | OCI}]
              [-resolve {IP | HOSTNAME | QUAL_HOSTNAME}]
              [-log {ALL|OFF|INFO|FINE|FINER|FINEST|SEVERE|WARNING}]
              [-log_file log_file]
              [-gsm gsm_name]
              [-showtime ON|OFF]
              [-verbose ON|OFF]
              [-save_config]
              [-gsmdebug (1|0)]
              [-spool]
              [-width]

#### Options

Table C-31 GDSCTL configure Options

| Syntax                                                               | Description                                                                  |
|:---------------------------------------------------------------------|:-----------------------------------------------------------------------------|
| `-driver THIN | OCI`                                                 | Oracle JDBC driver.                                                          |
| `-gsm ``gsm_name`                                                    | Set current global service manager.                                          |
| `-gsmdebug (1|0)`                                                    | Global service manager debug mode.                                           |
| `-gsmport ``port`                                                    | Default global service manager port.                                         |
| `-log {ALL | OFF | INFO | FINE | FINER | FINEST | SEVERE | WARNING}` | Set the logging level. The default is `OFF`.                                 |
| `-log_file ``log_file`                                               | Set the location of the log file. The default is `$TNS_ADMIN/GDSTL.log`.     |
| `-resolve IP | HOSTNAME| QUAL_HOSTNAME`                              | Default host resolution for global service manager endpoint.                 |
| `-save_config`                                                       | Store configuration changes to GSM.ORA.                                      |
| `-show`                                                              | Show the configuration.                                                      |
| `-showtime ON|OFF`                                                   | Print time stamps.                                                           |
| `-spool`                                                             | Enable spooling. Warning: prints security-sensitive information to log file. |
| `-timeout ``second``s`                                               | Global service manager requests timeout in seconds.                          |
| `-verbose ON|OFF`                                                    | Enable or disable verbose output. The default value is ON.                   |
| `-width`                                                             | Console width in number of characters (default 80).                          |

#### Example

Set the `mygsm` driver to OCI:

    configure -driver OCI mygsm

### connect

Specifies the credentials to administer a global service management environment. Credentials must be specified to perform certain operations using GDSCTL.

#### Syntax

    connect [user_name[/password]]@connect_identifier

#### Options

Table C-32 GDSCTL connect Options

| Syntax               | Description                                                                                                                                                                                                                       |
|:---------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `connect_identifier` | Specify an Oracle Net connect descriptor or a net service name that maps to a connect descriptor (for example, a list of global service managers).                                                                                |
| `password`           | Specify the password for the specified user. If you do not specify a password, then you are prompted to enter a password. The password is obscured when entered.                                                                  |
| `user_name`          | Specify the name of the user to connect as. The user that you specify must have either the Global Data Services administrator or the pool administrator role. If you specify no user name, then you are prompted for a user name. |

#### Usage Notes

You must connect to the catalog database as a user with either the Global Data Services administrator or the pool administrator privileges, depending on which command you want to run after you connect

**WARNING:**

Specifying a password as a connect command option is a security risk. You can avoid this risk by omitting the password, and entering it only when the system prompts for it.

#### Examples

Connect as the `gsmadmin` user to the private cloud:

    GDSCTL> connect gsmadmin@mycloud
    Enter password:

Connect using a connect descriptor, without specifying a user name and password:

    GDSCTL> connect (DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)(HOST=myhost)(PORT=1521)))
    Enter username:

### create catalog

The `create catalog` command is deprecated. Use `create gdscatalog` or `create shardcatalog` instead. Creates a Global Data Services catalog for global service management in a specific database.

#### Syntax

    create catalog -database db_name
                  [-user user_name[/password]
                  [-region region_name_list]
                  [-gdspool gdspool_name_list]
                  [-configname confname]
                  [-autovncr {ON | OFF}]
                  [-force]

#### Options

Table C-33 GDSCTL create catalog Options

| Options                              | Description                                                                                                                                                                                                                                                                                                                                                                                  |
|:-------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-autovncr {ON | OFF}`               | This option enables (`ON`) or disables (`OFF`) autovncr mode. The default value is `ON`.<br>See the Usage Notes below for important information about this option.                                                                                                                                                                                                                           |
| `-configname ``confname`             | Specify the name of the GDS configuration. The default configuration name is `ORADBCLOUD`.<br>The configuration name can be up to 32 bytes long and can contain an alphabetical character followed by zero or more alphanumeric ASCII characters, ‘\_', or ‘#' and possibly separated by periods if there are multiple identifiers.                                                          |
| `-database ``db_name`                | Specify the connect identifier for the database in which you want to create catalog.                                                                                                                                                                                                                                                                                                         |
| `-force`                             | Rewrites existing global service manager configuration on catalog database.                                                                                                                                                                                                                                                                                                                  |
| `-gdspool ``gdspool_name_list`       | Specify a comma-delimited list of database pool names. When you use this option, the specified database pools are created as part of the catalog creation. If you do not specify this option, then GDSCTL creates a default database pool named DBPOOLORA.                                                                                                                                   |
| `-region ``region_name_list`         | Specify a comma-delimited list of region names. This command creates each region and adds the regions to the catalog. If you do not specify a region, then a default region named REGIONORA is created.                                                                                                                                                                                      |
| `-user ``user_name``[/``password``]` | Specify a user (and optionally, the password) that has the Global Data Services administrator privileges on the catalog database. If you do not use this option, then GDSCTL prompts you for the name and the password of a user with Global Data Services administrator privileges. If you specify a user name but not the password for the user, then GDSCTL prompts you for the password. |

#### Usage Notes

This command is deprecated in Oracle Database 12c Release 2. Use create gdscatalog or create shardcatalog for your specific environment.

The `create catalog` command generates a pair of PKI public and private keys and stores them in the catalog, along with a fixed string "GSM" that is encrypted with a private key. It uses the `GSMCATUSER` password.

You must have the Global Data Services administrator privileges on the computer where you want to create the Global Data Services catalog.

Auto VNCR is best used in environments with simple private networks where ease of configuration is the most important consideration. To have the highest level of control over which hosts may participate in a GDS configuration, disable Auto VNCR and explicitly add the IP addresses of each database host to the VNCR configuration.

When `—autovncr` is enabled, Oracle attempts to find the host name of the target database when it is validated during `add shard` or `add database` execution. This host is then automatically added to the VNCR list in the catalog as an invited node. This mechanism is not compatible with all network configurations and may not work in the following cases:

- The catalog or global service manager host does not know how to translate the host name discovered on the target database host to an real IP address. This can happen if they have different names in the hosts file or DNS on the catalog or global service manager host, or if they just do not exist on those hosts.

- The target database host has multiple public network addresses, and Oracle chooses an address that is different than the address used when the database registers with the global service manager. This can happen if the host has multiple network cards or has configured virtual network interfaces.

- The database is running Oracle RAC, and other Oracle RAC instances run on a different subnet. This is not a recommended configuration for Oracle RAC. Refer to the Oracle RAC documentation for recommended configurations. With Oracle RAC, Oracle Database connects to a single database host to validate the target, and returns a subnet mask that includes the entire subnet that the host is on. If other instances are on a different subnet, they have no valid VNCR entry, and registration is rejected.

When `—autoVNCR` is not enabled, or, if any of the above cases apply, new hosts should be added manually using add invitednode (add invitedsubnet).

#### Example

Create a Global Data Services catalog for global service management in the database named DB1. Also create the regions EAST and WEST, and the database pool READERFARM.

    GDSCTL> create catalog -database db1 -region west,east -gdspool readerfarm

### create gdscatalog

Creates a Global Data Services catalog for global service management in a specific database.

#### Syntax

    create gdscatalog -database db_name
                     [-user user_name[/password]
                     [-region region_name_list]
                     [-gdspool gdspool_name_list]
                     [-configname confname]
                     [-autovncr {ON | OFF}]
                     [-force]

#### Options

Table C-34 GDSCTL create gdscatalog Options

| Syntax                               | Description                                                                                                                                                                                                                                                                                                                                                                                  |
|:-------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-autovncr {ON | OFF}`               | This option enables (`ON`) or disables (`OFF`) autovncr mode. The default value is `ON`.<br>See the Usage Notes below for important information about this option.                                                                                                                                                                                                                           |
| `-configname ``confname`             | Specify the name of the GDS configuration. The default configuration name is `ORADBCLOUD`.<br>The configuration name can be up to 32 bytes long and can contain an alphabetical character followed by zero or more alphanumeric ASCII characters, ‘\_', or ‘#' and possibly separated by periods if there are multiple identifiers.                                                          |
| `-database ``db_name`                | Specify the connect identifier for the database in which you want to create catalog.                                                                                                                                                                                                                                                                                                         |
| `-force`                             | Rewrites existing global service manager configuration on catalog database.                                                                                                                                                                                                                                                                                                                  |
| `-gdspool ``gdspool_name_list`       | Specify a comma-delimited list of database pool names. When you use this option, the specified database pools are created as part of the catalog creation. If you do not specify this option, then GDSCTL creates a default database pool named DBPOOLORA.                                                                                                                                   |
| `-region ``region_name_list`         | Specify a comma-delimited list of region names. This command creates each region and adds the regions to the catalog. If you do not specify a region, then a default region named REGIONORA is created.                                                                                                                                                                                      |
| `-user ``user_name``[/``password``]` | Specify a user (and optionally, the password) that has the Global Data Services administrator privileges on the catalog database. If you do not use this option, then GDSCTL prompts you for the name and the password of a user with Global Data Services administrator privileges. If you specify a user name but not the password for the user, then GDSCTL prompts you for the password. |

#### Usage Notes

The `create gdscatalog` command generates a pair of PKI public and private keys and stores them in the catalog, along with a fixed string "GSM" that is encrypted with a private key. It uses the `GSMCATUSER` password.

You must have the Global Data Services administrator privileges on the computer where you want to create the Global Data Services catalog.

Auto VNCR is best used in environments with simple private networks where ease of configuration is the most important consideration. To have the highest level of control over which hosts can participate in a GDS configuration, disable Auto VNCR and explicitly add the IP addresses of each database host to the VNCR configuration.

When `—autovncr` is enabled, Oracle attempts to find the host name of the target database when it is validated during `add shard` or `add database` execution. This host is then automatically added to the VNCR list in the catalog as an invited node. This mechanism is not compatible with all network configurations and may not work in the following cases:

- The catalog or global service manager host does not know how to translate the host name discovered on the target database host to an real IP address. This can happen if they have different names in the hosts file or DNS on the catalog or global service manager host, or if they just do not exist on those hosts.

- The target database host has multiple public network addresses, and Oracle chooses an address that is different than the address used when the database registers with the global service manager. This can happen if the host has multiple network cards or has configured virtual network interfaces.

- The database is running Oracle RAC, and other Oracle RAC instances run on a different subnet. This is not a recommended configuration for Oracle RAC. Refer to the Oracle RAC documentation for recommended configurations. With Oracle RAC, Oracle Database connects to a single database host to validate the target, and returns a subnet mask that includes the entire subnet that the host is on. If other instances are on a different subnet, they have no valid VNCR entry, and registration is rejected.

When `—autoVNCR` is not enabled, or, if any of the above cases apply, new hosts should be added manually using add invitednode (add invitedsubnet).

#### Example

Create a Global Data Services catalog for global service management in the database named DB1. Also create the regions EAST and WEST, and the database pool READERFARM.

    GDSCTL> create gdscatalog -database db1 -region west,east -gdspool readerfarm

### create shard

Create a new shard and add it to a shardspace or shardgroup.

#### Syntax

    create shard  [{-shardgroup shardgroup_name | –shardspace shardspace_name}]
                   [-region region_name]
                   [-deploy_as {primary | standby | active_standby}]
                   [-rack rack_id]
                   [-gg_service (http|https):ogg_host:sm_port/deployment
                      -gg_password gg_user_password]
                    -destination destination_name
                   {-credential credential_name |
                      -osaccount account_name
                      -ospassword password
                     [-windows_domain domain_name]}
                   [-dbparam db_parameter_file |
                      -dbparamfile db_parameter_file]
                   [-dbtemplate db_template_file |
                      -dbtemplatefile db_template_file]
                   [-netparam net_parameter_file |
                      -netparamfile net_parameter_file]
                   [-serviceuserpassword pwd]
                   [-sys_password]
                   [-system_password]

#### Options

Table C-35 GDSCTL create shard Options

| Option                                                                | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|:----------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-credential ``credential_name`                                       | The name of the credential object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-dbparam ``db_parameter_file`                                        | Specify a file object containing Database Configuration Assistant (DBCA) parameters to use during database creation on the remote machine.                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `-dbparamfile ``db_parameter_file`                                    | Specify an operating system file name containing Database Configuration Assistant (DBCA) parameters to use during database creation on the remote machine. GDSCTL uses this to open a local file on the machine on which it is running.                                                                                                                                                                                                                                                                                                                         |
| `-dbtemplate ``db_template_file`                                      | Specify a file object containing Database Configuration Assistant (DBCA) database template information to use during database creation on the remote machine.                                                                                                                                                                                                                                                                                                                                                                                                   |
| `-dbtemplatefile ``db_template_file`                                  | Specify an operating system file name containing Database Configuration Assistant (DBCA) database template information to use during database creation on the remote machine. GDSCTL uses this to open a local file on the machine on which it is running.                                                                                                                                                                                                                                                                                                      |
| `-deploy_as {PRIMARY | STANDBY | ACTIVE_STANDBY}`                     | Specify the role that is assigned to a shard added to the shardgroup after deployment. This parameter is only used with Data Guard replication. The specified role will be assigned to the shard database after deployment. The valid values are:<br>• `PRIMARY` – the shard should be deployed as the primary database<br>• `STANDBY` – the shard should be deployed as a Data Guard standby (mounted)<br>• `ACTIVE_STANDBY` – the shard should be deployed as an Active Data Guard standby<br>If the parameter is not specified, the default value is STANDBY |
| `-destination ``destination_name`                                     | The name of the remote executable agent through which the database will be created as listed in the `ALL_SCHEDULER_EXTERNAL_DESTS` view.                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `-gg_password ``gg_user_password`                                     | Specifies the password for the user account that will be created on the shard database that the Oracle GoldenGate replication processes will use. This parameter is mandatory for Oracle GoldenGate replication.                                                                                                                                                                                                                                                                                                                                                |
| `-gg_service ``hostname:port/GGHOME_directory`                        | This parameter is mandatory for Oracle GoldenGate replication and specifies the URI for the GoldenGate Admin Server that will manage the GoldenGate replication at this shard. The format will be as follows Example:<br>`https:shard1.example.com:9005/shard1`.                                                                                                                                                                                                                                                                                                |
| `-netparam ``net_parameter_file`                                      | Specify a file object containing Net Configuration Assistant (NETCA) parameters to use during network listener setup on the remote machine.                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-netparamfile ``net_parameter_file`                                  | Specify an operating system file name containing Net Configuration Assistant (NETCA) parameters to use during network listener setup on the remote machine. GDSCTL uses this to open a local file on the machine on which it is running.                                                                                                                                                                                                                                                                                                                        |
| `-osaccount ``account_name`                                           | Specify the operating system account which will be used for remote jobs                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `-ospassword ``password`                                              | Specify the corresponding password for the account name specified in the `-osaccount` parameter.                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `-rack ``rack_id`                                                     | Specify an identifier of a rack (hardware cabinet), or another physical grouping of nodes with similar availability characteristics. If specified, GDS will enforce that databases that contain replicated data are not placed in the same rack. If this is not possible an error is raised.                                                                                                                                                                                                                                                                    |
| `-region ``region_name`                                               | Specify the GDS region database, catalog, shard, shardgroup, or shard director (global service manager) that this shard belongs to. This parameter is only valid for user-defined sharding. For other sharing methods it is specified per shardgroup.                                                                                                                                                                                                                                                                                                           |
| `-serviceuserpassword ``pwd`                                          | The password for the operating system account under which Windows RDBMS and TNSLSNR services run.                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `{-shardgroup ``shardgroup_name`` | -shardspace ``shardspace_name``}` | Specify the name of the shardgroup or shardspace that this shard is being added to.<br>Use `-shardspace` when using this command in a user-defined sharding configuration. Use `-shardgroup` with system-managed and composite sharding configurations.                                                                                                                                                                                                                                                                                                         |
| `-sys_password`                                                       | SYS account password.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `-system_password`                                                    | SYSTEM account password.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `-windows_domain ``domain_name`                                       | Specify a corresponding domain name for an account if a Windows account has been specified in the `-osaccount` parameter.                                                                                                                                                                                                                                                                                                                                                                                                                                       |

#### Usage Notes

`CREATE SHARD` causes a new database to be created using DBCA and NETCA.

`CREATE SHARD` only registers the database with GDS. The database is not created and replication is not configured on a newly create database, and data from other databases is not distributed to it until `DEPLOY` is executed.

The `—DEPLOY_AS` option can only be specified if a shard is being added to a shardspace. If a shard is being added to a shardgroup, its role will determined by the role of the shardgroup. The role is assigned when the shard gets deployed.

If the `—CREDENTIAL` option is specified, the credential name must have previously been created with the `ADD CREDENTIAL` command. If `—CREDENTIAL` is not specified, then `OSACCOUNT` and `OSPASSWORD` (and optionally `WINDOWS_DOMAIN`) must be specified.

The value for `DBPARAM`, `DBTEMPLATE`, or `NETPARAM` must be the name of a file object as previously specified in the `ADD FILE` command. The file content specified by the -netparam or -netparamfile parameter in CREATE SHARD is a NETCA response file. Examples can be found in \$ORACLE_HOME/assistants/netca. By default, port 1521 is used with a listener name of LISTENER\_shard_name. These values can be changed by modifying a sample response file and specifying it using the -netparam or -netparamfile parameters. The file content specified by the -dbtemplate or -dbtemplatefile parameter in CREATE SHARD is a DBCA template file. Examples of template files can be found in \$ORACLE_HOME/assistants/dbca/templates. If not specified, the General_Purpose.dbc file located in the above directory on the shard destination host will be used. The format of the file contents specified in the -dbparam or -dbparamfile command is a space-delimited list of DBCA command line parameters and values on one or more lines. For example, the following is an example of a valid parameter file: `-gdbName shard1.example.com -initParams sort_area_size=200000`. For a complete list of possible DBCA parameters, run `dbca -help -createDatabase`.

See [Working with Oracle GoldenGate Sharding](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/gsmug&id=GGSAU-GUID-2C059382-7753-4EFA-B313-A6E0DAF7EA1C) in the Fusion Middleware Using the Oracle GoldenGate Microservices Architecture guide for more information about using Oracle GoldenGate with Oracle Sharding.

#### Example

Create a shard.

    GDSCTL> create shard –shardgroup group1 –destination dbdest –credential group1_cred
     –dbparam group1_db_params

### create shardcatalog

Creates a shard catalog for the sharded database.

#### Syntax

    create shardcatalog -database connect_identifier
                       [-user username[/password]]
                       [-region region_name_list]
                       [-configname config_name]
                       [-autovncr {ON | OFF}]
                       [-force]
                       [-sdb sdb_name]
                       [-shardspace shardspace_name_list]
                       [-agent_password password]
                       [-repl DG | OGG}]
                       [-repfactor number]
                       [-sharding {system | composite | user}]
                       [-chunks number]
                       [-protectmode dg_protection_mode]
                       [-agent_port port]

#### Options

Table C-36 GDSCTL create shardcatalog options

| Command Option                          | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:----------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-agent_password ``password`            | Specify the password to be used for remote scheduler agent registration with the catalog database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `-agent_port ``port`                    | Port number for XDB to use. If NULL and no current value is set, then it will default to 8080. Execute on catalog as well.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `-autovncr {ON|OFF}`                    | This option enables (`ON`) or disables (`OFF`) auto VNCR mode. The default value is `ON`.<br>See the Usage Notes below for important information about this option.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-chunks ``number`                      | Specify the default number of unique chunks in a shardspace. The value of `-chunks` must be greater than 2 times the size of the largest shardgroup in any shardspace.<br>This parameter does not apply to user-defined sharding. It will apply to all shardspaces created for composite sharding if the number of chunks is not specified in the `ADD SHARDSPACE` command.<br>All shardgroups in a shardspace have the same number of chunks. If this parameter is not specified, the default number of chunks is determined at the time of execution of the first `DEPLOY` command and is 120 per database of the shardgroup with the biggest number of shards                                                                                 |
| `-configname ``config_name`             | Specify the name of the GDS configuration. This name is used as the virtual DB_DOMAIN of the sharded database. The default configuration name is `ORADBCLOUD`.<br>The configuration name can be up to 32 bytes long and can contain an alphabetical character followed by zero or more alphanumeric ASCII characters, ‘\_', or ‘#' and possibly separated by periods if there are multiple identifiers.                                                                                                                                                                                                                                                                                                                                          |
| `—database ``connect_identifier`        | Specify the connect identifier for the database in which you want to create the catalog.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `-force`                                | Before creating the new catalog, delete an existing shard or GDS catalog on this database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `-protectmode ``dg_protection_mode`     | Specify the Data Guard protection mode: `MAXPROTECTION`, `MAXAVAILABILITY`, or `MAXPERFORMANCE` (default). This parameter does not apply to Oracle GoldenGate replication. For Data Guard replication this parameter applies to any shardspace created without specification of protection mode in the `ADD SHARDSPACE` command.                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-region ``region_name_list`            | Specify a comma-delimited list of region names. This command creates each region and adds the regions to the catalog. If you do not specify a region, then a default region named REGIONORA is created.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `-repl DG|OGG`                          | Specify the technology used to replicate data in the sharded database. Only one value can be specified for this parameter: `DG` for Data Guard and `OGG` for Oracle GoldenGate. The default value is `DG`. This parameter cannot be modified after the catalog has been created.                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-repfactor ``number`                   | Specify the default replication factor (the number of replicas for each piece of data stored in a shardgroup). This parameter can only be used with Oracle GoldenGate replication and system-managed or composite sharding, and this parameter is mandatory in this cases. It does not apply to user-defined sharding because there are no shardgroups in user-defined sharding.<br>The default replication factor specified by this parameter can be overridden for a particular shardgroup by specifying the replication factor in the corresponding `ADD SHARDGROUP` command. The parameter cannot be overridden for automatically created default shardgroups. A non-default shardgroup must be created to customize the replication factor. |
| `-sdb ``sdb_name`                       | Specify the virtual DB_UNIQUE_NAME for the sharded database. The default name is ORASDB.<br>The sharded database (SDB) name can be up to 30 characters long and can be an alphabetical character followed by zero or more alphanumeric ASCII characters or an underscore (\_).                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `-sharding {system | composite | user}` | Specify the sharding type: `SYSTEM`for system-managed (default), `USER` for user-defined, or `COMPOSITE`. This parameter cannot by modified after the catalog has been created. Oracle GoldenGate does not support the user-defined sharding method.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `-shardspace ``shardspace_name_list`    | Specify a comma-delimited list of shardspace names. This option creates specified shardspaces and adds them to the catalog. If you do not specify a shardspace, then a default shardspace named SHARDSPACEORA is created.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `—user ``username[/password]`           | Specify a user (and optionally, the password) that has the administrator privileges on the catalog database. If you do not use this option, then GDSCTL prompts you for the name and the password of a user with administrator privileges. If you specify a user name but not the password for the user, then GDSCTL prompts you for the password.                                                                                                                                                                                                                                                                                                                                                                                               |

#### Usage Notes

The `create shardcatalog` command creates a GDS catalog specifically designed for a sharded database (SDB). This command cannot be used to create a conventional GDS catalog. Execution of this command is the first step required to create an SDB. The command is executed by the user with the GDS administrator or SYSDBA privileges.

Keep the following points in mind when using `create shardcatalog`:

- Only a single sharded database can be created using a shard catalog. A shard catalog cannot be used for a regular GDS configuration.

- Any arbitrary password can be specified for remote agent registration. If one is stipulated and an agent registration password already exists, it will be overridden with the new password. In order to successfully execute the `GDSCTL CREATE SHARD` command, an agent password must be set using `CREATE SHARDCATALOG` or `MODIFY CATALOG`.

- `CHUNKS` defines the default number of unique chunks in a shardspace. It is applied to all shardspaces created for composite sharding if the number of chunks is not specified in the `ADD SHARDSPACE` command.

- This command creates each region and adds the regions to the catalog. If you do not specify a region, then a default region named `REGIONORA` is created.

- The default replication factor specified by `REPFACTOR` can be overridden for a particular shardgroup by specifying the replication factor in the corresponding `ADD SHARDGROUP` command. For automatically created default shardgroups the parameter cannot be overridden. A non-default shardgroup must be created to customize the replication factor.

- The `SHARDSPACE` option creates specified shardspaces and adds them to the catalog. If you do not specify a shardspace, then a default shardspace named `SHARDSPACEORA` is created.

- For Data Guard replication the `PROTECTMODE` parameter applies to any shardspace created without specification of protection mode in the `ADD SHARDSPACE` command.

- Auto VNCR is best used in environments with simple private networks where ease of configuration is the most important consideration. To have the highest level of control over which hosts may participate in a GDS configuration, disable Auto VNCR and explicitly add the IP addresses of each database host to the VNCR configuration.

  When `—autovncr` is enabled, Oracle attempts to find the host name of the target shard when it is validated during `add shard` execution. This host is then automatically added to the VNCR list in the catalog as an invited node. This mechanism is not compatible with all network configurations and may not work in the following cases:

  - The catalog or global service manager host does not know how to translate the host name discovered on the target shard host to an real IP address. This can happen if they have different names in the hosts file or DNS on the catalog or global service manager host, or if they just do not exist on those hosts.

  - The target shard host has multiple public network addresses, and Oracle chooses an address that is different than the address used when the shard registers with the global service manager. This can happen if the host has multiple network cards or has configured virtual network interfaces.

  - The shard is running Oracle RAC, and other Oracle RAC instances run on a different subnet. This is not a recommended configuration for Oracle RAC. Refer to the Oracle RAC documentation for recommended configurations. With Oracle RAC, Oracle Database connects to a single shard host to validate the target, and returns a subnet mask that includes the entire subnet that the host is on. If other instances are on a different subnet, they have no valid VNCR entry, and registration is rejected.

  - See [Working with Oracle GoldenGate Sharding](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/gsmug&id=GGSAU-GUID-2C059382-7753-4EFA-B313-A6E0DAF7EA1C) in the Fusion Middleware Using the Oracle GoldenGate Microservices Architecture guide for more information about using Oracle GoldenGate with Oracle Sharding.

  When `—autoVNCR` is not enabled, or, if any of the above cases apply, new hosts should be added manually using add invitednode (add invitedsubnet).

#### Examples

The following example creates a shard catalog on the mydb database.

    GDSCTL> CREATE SHARDCATALOG –DATABASE mydb

### databases

Displays the status of all databases.

#### Syntax

    {status database | databases} [-gsm gsm_name]
                                  [-database db_name]
                                  [-gdspool gdspool_name]
                                  [-raw|-support|-verbose]

#### Options

Table C-37 GDSCTL databases Options

| Option                    | Description                                                                                                                                                                                                       |
|:--------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-database ``db_name`     | Specify the name of the database on which you want to start the service. If you do not specify this option, then GDSCTL starts the services on all preferred databases.                                           |
| `-gdspool ``gdspool_name` | Specify the name of the database pool in which the services you want to start are located. If not specified and there is only one `gdspool` with access granted to the user, it is used as the default `gdspool`. |
| `-gsm ``gsm_name`         | Specify the name of a global service manager to check. If the name is not specified, then GDSCTL uses the current global service manager name for the session (specified with the GDSCTL `set gsm` command).      |
| `-raw`                    | If specified, GDSCTL output is presented in a raw non-parsed format.                                                                                                                                              |
| `-support`                | If specified, GDSCTL output displays additional information.                                                                                                                                                      |
| `-verbose`                | Enable verbose mode.                                                                                                                                                                                              |

#### Usage Notes

You must connect to the catalog database as a user with the pool administrator privileges, using the command connect before running this command.

#### Example

Display the status of all databases:

    GDSCTL> databases

The `databases` command returns output similar to the following:

    Database: "dbcat1" Registered: Y State: Ok ONS: N. Role: PRIMARY Instances: 1
     Region: east

       Service: "sales_svc2" Globally started: N Started: N
                Scan: Y Enabled: Y Preferred: Y
       Service: "sales_svc1" Globally started: Y Started: Y
                Scan: N Enabled: Y Preferred: Y
       Registered instances:
         sales%11
    Database: "dbcat2" Registered: Y State: Ok ONS: N. Role: PRIMARY Instances: 1
     Region: east
       Service: "sales_svc2" Globally started: N Started: N
                Scan: Y Enabled: Y Preferred: Y
       Service: "sales_svc1" Globally started: Y Started: Y
                Scan: N Enabled: Y Preferred: Y
       Registered instances:
         sales%1

### delete catalog

Deletes the specified catalog.

#### Syntax

    delete catalog [-connect [user/[password]@]conn_str]
                   [-force]

#### Options

Table C-38 GDSCTL delete catalog Options

| Syntax      | Description                                                                                                                                                                                                                                                                                          |
|:------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-connect ` | Specify an Oracle Net connect descriptor or a net service name that maps to a connect descriptor for the database (or shard).<br>If you do not use this option, then GDSCTL deletes the Global Data Services catalog that is used by the global service manager associated with the current session. |
| `-force`    | Silently remove GDS metadata. No warnings are shown.                                                                                                                                                                                                                                                 |

#### Usage Notes

You must have the Global Data Services administrator privileges on the computer where the database resides from which you want to delete the Global Data Services catalog

If `-connect` is not specified, the catalog that belongs to currently connected database (if any) is deleted.

#### Example

Delete the Global Data Services catalog located in the database named DB1.

    GDSCTL> delete catalog -connect db1

### deploy

Deploys the sharded database.

#### Syntax

    deploy [-no_rebalance]

#### Options

Table C-39 GDSCTL deploy Options

| Option          | Description                                               |
|:----------------|:----------------------------------------------------------|
| `-no_rebalance` | Skip automatic chunk migration during incremental deploy. |

#### Usage Notes

This command is executed after one or more shards have been added to the shard catalog. As the result of the command execution, a certain range of data is associated with a newly added database. If a database is part of a Data Guard Broker configuration, a role (primary or standby) is assigned to it. Then replication and/or migration of data to from other databases to newly deployed databases are initiated.

- Deploy runs almost entirely in parallel, and mostly in the background, and will not deploy any shards which do not have all their counterparts in other shardgroups. All undeployed shards that can be deployed are deployed as the result of execution of this command.

- Before configuring replication, this command cross-checks parameters of all databases included into the replication configuration. An error is returned if the cross-check finds inconsistency or ambiguity, for example, no primary shardgroup in a shardspace with Data Guard replication.

- If a `CREATE SHARD` command had previously been issued, these new shards will be created during deployment and added to the shard catalog. If a shard needs to be created, `DEPLOY` runs a job for each database which requires a remote credential (see add credential and create shard). This credential must be valid at the time of deployment.

- The `NO_REBALANCE` option allows to skip automatic rebalancing of chunks across shards during incremental `DEPLOY`. Use the move chunk command to perform manual chunk migration.

#### Examples

Deploy the sharded database.

    GDSCTL> deploy

### disable service

Disables specified global services.

#### Syntax

    disable service [-gdspool gdspool_name]
                    [-service service_name_list]
                    [-database db_name |[-override -connect conn_str [-pwd password]]]

#### Options

Table C-40 GDSCTL disable service Options

| Syntax                         | Description                                                                                                                                                                                                                    |
|:-------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-connect ``conn_str`          | An Oracle Net connect descriptor or net service name that resolves to a connect descriptor for the database (or shard).                                                                                                        |
| `-database ``db_name`          | Specify the name of the database on which to the service is located. If you do not specify this option, then the service is disabled, globally.                                                                                |
| `-gdspool ``gdspool_name`      | Specify the database pool in which the services are located. If not specified and there is only one `gdspool` with access granted to the user, then this one is used as the default `gdspool`.                                 |
| `-override`                    | Skip the GDS catalog (used when the GDS catalog is not available).                                                                                                                                                             |
| `-pwd`                         | The GSMUSER password.                                                                                                                                                                                                          |
| `-service ``service_name_list` | Specify a comma-delimited list of global service names. If you do not use `-service` to specify an individual global service or to specify a list of global services, then all the services in the database pool are disabled. |

#### Usage Notes

You must connect to the catalog database as a user with the pool administrator privileges, using the connect command before running this command

A running service cannot be disabled. If `-override` is specified, the command is executed without going to the GDS catalog. Use this option when the GDS catalog is unavailable. It is not recommended for use under normal operation.

#### Example

Disable and stop the service G_SALES_REPORT on all databases in the database pool READERFARM.

    GDSCTL> disable service -gdspool readerfarm -service g_sales_report -database db1

**See Also:**

[Disabling a Global Service](global-data-services-admin.md)

### enable service

Enables the specified global services.

#### Syntax

    enable service [-gdspool gdspool_name]
                   [-service service_name_list]
                   [-database db_name|[-override -connect conn_str [-pwd password]]]

#### Options

Table C-41 GDSCTL enable service Options

| Syntax                    | Description                                                                                                                                                                                                                    |
|:--------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-connect ``conn_str`     | An Oracle Net connect descriptor or net service name that resolves to a connect descriptor for the database (or shard).                                                                                                        |
| `-database ``db_name`     | Specify the name of the database on which the service is located. If you do not specify this option, then the service is enabled globally.                                                                                     |
| `-gdspool ``gdspool_name` | Specify the GDS pool in which the services are located. If not specified and there is only one gdspool with access granted to the user, it is used as the default gdspool.                                                     |
| `-override`               | Skip the GDS catalog (used when the GDS catalog is not available).                                                                                                                                                             |
| `-pwd`                    | The GSMUSER password.                                                                                                                                                                                                          |
| `-service ``service_name` | Specify a comma-delimited list of global service names. If you do not use `-service` to specify an individual global service or to specify a list of global services, then all the services in the database pool are disabled. |

#### Usage Notes

You must connect to the catalog database as a user with the pool administrator privileges, using the connect command before running this command

`ENABLE SERVICE` will start the global service if it is `preferred_all` or cardinality is not reached.

If `-override` is specified, the command is executed without going to the GDS catalog. Use this option when the GDS catalog is unavailable. It is not recommended for use under normal operation.

#### Example

Enable the service G_SALES_REPORT on the database DB1 in the database pool READERFARM.

    GDSCTL> enable service -gdspool readerfarm -service g_sales_report -database  db1

**See Also:**

[Enabling a Global Service](global-data-services-admin.md)

### exit

Quit GDSCTL utility.

#### Syntax

    quit | exit

### export catalog

Saves the current catalog configuration to a local file.

#### Syntax

    export catalog [-force] source

#### Options

Table C-42 GDSCTL export catalog Options

| Syntax   | Description                                                                                                                                                                                                                                                                           |
|:---------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-force` | If not specified, export will be cancelled if there are ongoing GDS operations.                                                                                                                                                                                                       |
| `source` | Name of a file on the same computer where the command is being executed. The configuration will be saved to this file. If the file already exists, it will be overwritten without a prompt. If the file is not writable (for example the path does not exist), you will get an error. |

#### Usage Notes

You must connect to the catalog database as a user with GDS Administrator privileges before running this command.

It is recommended that you validate the catalog, using the validate catalog command before exporting it.

#### Example

Save the catalog backup to your home directory.

    GDSCTL> export catalog /home/user/cat-201307.backup

### help

Provides a list of the GDSCTL commands supported in the current release. When followed by a command name, it returns the help page associated with the command.

#### Syntax

    help [gdsctl_command]

#### Options

Table C-43 GDSCTL help Options

| Option           | Description                                                                                         |
|:-----------------|:----------------------------------------------------------------------------------------------------|
| `gdsctl_command` | Enter any GDSCTL command name to return a help page with syntax, options, usage notes and examples. |

### import catalog

Restores the catalog configuration from the specified file, created using export catalog command.

#### Syntax

    import catalog [-database catalog_db_name]
                   [-catpwd gsmcatusrpwd]
                   [-user gsmadminname[/password]]
                   source

#### Options

Table C-44 GDSCTL import catalog Options

| Syntax                            | Description                                                                                                                                                                     |
|:----------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-catpwd ``gsmcatusrpwd`          | GSMCATUSER password.                                                                                                                                                            |
| `—database ``catalog_db_name`     | The connect identifier for the database in which to create catalog.                                                                                                             |
| `source`                          | Name of a file on the same computer where the command is being executed. The configuration will be restored from this file. If the file is not readable, you will get an error. |
| `-user ``gsmadminname[/password]` | Credentials of the user that has the GDS administrator privileges on the catalog database.                                                                                      |

#### Usage Notes

If `-database` is not specified, the GDS catalog that the current global service manager is associated with will be used. The `-catpwd` option should be specified in case you need to perform cleanup of databases in the existing catalog that are not found in imported file.

When restoring to a new catalog database, catalog must be created first, using the create gdscatalog command.

You must connect to the catalog database as a user with GDS Administrator privileges before running this command.

The import procedure can be considered finished only when there are no pending requests after import. Use the config command to get the list of pending requests.

#### Example

Load the catalog backup from your home directory.

    GDSCTL> import catalog /home/user/cat-201307.backup

### modify catalog

Modifies the properties of the GDS catalog or shard catalog.

#### Syntax

    modify catalog [-autovncr {ON | OFF}]
                   [-oldpwd oldpassword -newpwd newpassword]
                   [-pwd password -newkeys]
                   [-agent_password password]
                   [-agent_port port]
                   [-region region]
                   [-recover]

#### Options

Table C-45 GDSCTL modify catalog Options

| Syntax                       | Description                                                                                                                      |
|:-----------------------------|:---------------------------------------------------------------------------------------------------------------------------------|
| `-agent_password ``password` | Specify the agent registration password in the catalog for the remote Scheduler agent.                                           |
| `-agent_port ``port`         | Port number for XDB to use. If it is NULL and no current value is set, then it will default to 8080. Execute on catalog as well. |
| `-autovncr {ON | OFF}`       | This option enables (`ON`) or disables (`OFF`) autovncr mode. The default value is `ON`.                                         |
| `-newkeys`                   | Generates a new PKI key pair.                                                                                                    |
| `-newpwd ``newpassword`      | Used along with `-oldpwd`, sets the `GSMCATUSER` password after changing it on the catalog database.                             |
| `-oldpwd ``oldpassword`      | Used along with `-newpwd`, sets the `GSMCATUSER` password after changing it on the catalog database.                             |
| `-pwd ``password`            | Provides the `GSMCATUSER` password to generate the PKI keys when using `-newkeys`.                                               |
| `-recover`                   | Perform catalog recovery to the last consistent state.                                                                           |
| `-region ``region`           | Region that the database, catalog, shard, shardgroup, or global service manager belongs to.                                      |

#### Usage Notes

To use this command, there must be a least one global service manager running and a connection with the catalog database must have already been established (see the connect command).

You must connect to the catalog database as a user with the Global Data Services administrator privileges, using the connect command before running this command.

Auto VNCR is best used in environments with simple private networks where ease of configuration is the most important consideration. To have the highest level of control over which hosts may participate in a GDS configuration, disable Auto VNCR and explicitly add the IP address(es) of each database host to the VNCR configuration.

The `GSMCATUSER` password should be updated regularly for security reasons. Use the following command to perform this operation.

    modify catalog -oldpwd oldpassword -newpwd newpassword

This command fetches the encrypted private key and encryption string, decrypts them using the old password, re-encrypts them with the new password and stores them again.

If the `GSMCATUSER` password is changed, you must execute `MODIFY CATALOG` to update catalog security scheme, with `-newpwd` and `-oldpwd` specified.

The PKI keys must be updated regularly, which is done using `modify catalog -oldpwd` `oldpassword` `-newkeys`. This command generates a new PKI key pair and replaces the corresponding fields in the database.

If you decide to replace the PKI keys, or just after A patchset upgrade on the catalog database, run this command:

    modify catalog -pwd **  -newkeys

An arbitrary password can be stipulated for remote agent registration. If an agent registration password already exists, it will be overridden with the new password. In order to successfully execute the `GDSCTL CREATE SHARD` command, an agent password must be set using the `CREATE SHARDCATALOG` or `MODIFY CATALOG` command.

#### Examples

Turn off autovncr mode for the catalog database.

    connect gsmadmin@mycloud
    GDSCTL> modify catalog -autovcnr off

Specify the remote Scheduler agent registration password.

    connect gsmadmin@mycloud
    GDSCTL> modify catalog –agent_password mypass

Update catalog security scheme.

    GDSCTL> modify catalog -autovncr OFF -oldpwd opwd -newpwd npwd -pwd pwd -newkeys

### modify cdb

Modify cdb attributes.

#### Syntax

    modify cdb -shard cdbname_list
                [-connect connect_identifier]
                [-pwd gsmrootuser_pwd]
                [-scan scan_address [-ons port]]
                [-savename]

#### Options

Table C-46 GDSCTL modify cdb Options

| Option                          | Description                                                                                                                                                                                   |
|:--------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-shard ``cdbname_list`         | Specify a comma-delimited list of cdb names.                                                                                                                                                  |
| `-connect ``connect_identifier` | Specify an Oracle Net connect descriptor or a net service name that maps to a connect descriptor for the database that is being modified.                                                     |
| `-ons ``port`                   | Specify the ONS port.                                                                                                                                                                         |
| `-pwd ``gsmrootuser_pwd`        | Specify the password for GSMROOTUSER.                                                                                                                                                         |
| `-savename`                     | Specify this option to store a net service name specified with the` -connect` option in the Global Data Services catalog, rather than the connect descriptor mapped to that net service name. |
| `-scan ``scan_address`          | Specify the SCAN address for a cluster.                                                                                                                                                       |

#### Usage Notes

Some parameters are not supported after the CDB contains shards or contains shards that have been deployed.

#### Examples

Change a password on a CDB.

    GDSCTL> modify cdb -shard cdb1 -pwd new_gsmrootuser_password

### modify credential

Modifies an existing credential which will be used by the remote Scheduler agent to execute shard jobs.

#### Syntax

    modify credential -credential credential_name
                      -osaccount account_name
                      -ospassword password
                     [-windows_domain domain_name]

#### Options

Table C-47 GDSCTL modify credential Options

| Option                          | Description                                                                                      |
|:--------------------------------|:-------------------------------------------------------------------------------------------------|
| `-credential ``credential_name` | Specify the name of the credential to modify.                                                    |
| `-osaccount ``account_name`     | Specify the operating system account which will be used for remote jobs.                         |
| `-ospassword ``password`        | Specify the corresponding password for the account.                                              |
| `-windows_domain ``domain_name` | If a Windows account has been specified, specify the corresponding domain name for that account. |

#### Usage Notes

This command modifies credentials which will be used to execute jobs on sharded hosts in response to administrative commands.

If the specified credential does not exist, the command returns an error.

#### Examples

Modify a credential named east_region_cred.

    GDSCTL> modify credential –credential east_region_cred –osaccount agent_user
     –ospassword newpass

### modify database

Modifies the configuration parameters of the databases in a GDS pool, such as region, connect identifier, global service manager password, SCAN address, and ONS port.

#### Syntax

    modify database -database db_name_list
                   [-gdspool gdspool_name]
                   [-shard shard_name]
                   [-deploy_as PRIMARY|STANDBY]
                   [-region region_name]
                   [-pwd password]
                   [-connect connect_identifier]
                   [-scan scan_address]
                   [-ons port]]
                   [-savename]
                   [-cpu_threshold cpu]
                   [-disk_threshold disk]
                   [-rack rack_id]
                   [-NETPARAM net_parameter_file | -NETPARAMFILE net_parameter_file]
                   [-DBPARAM db_parameter | -DBPARAMFILE db_parameter_file]
                   [-DBTEMPLATE db_template | -DBTEMPLATEFILE db_template_file]

#### Options

Table C-48 GDSCTL modify database Options

| Option                          | Description                                                                                                                                                                                   |
|:--------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-connect ``connect_identifier` | Specify an Oracle Net connect descriptor or a net service name that maps to a connect descriptor for the database that is being modified.                                                     |
| `-cpu_threshold ``cpu`          | Specifies CPU Utilization percentage threshold.                                                                                                                                               |
| `-database ``dbname_list`       | Specify a comma-delimited list of database names.                                                                                                                                             |
| `-disk_threshold ``disk`        | Specifies the average latency in milliseconds of a synchronous single-block read.                                                                                                             |
| `-gdspool ``gdspool_name`       | Specify the database pool to which the databases belong.                                                                                                                                      |
| `-ons ``port`                   | Specify the ONS port.                                                                                                                                                                         |
| `-pwd ``password`               | Specify the password for the GSMUSER.                                                                                                                                                         |
| `-region ``region_name`         | Specify the region to which the databases belong.                                                                                                                                             |
| `-savename`                     | Specify this option to store a net service name specified with the `-connect` option in the Global Data Services catalog, rather than the connect descriptor mapped to that net service name. |
| `-scan ``scan_address`          | Specify the SCAN address for a cluster.                                                                                                                                                       |

#### Usage Notes

You can multiple databases if the `region` property is specified.

For all parameters except for the GDS region, first the appropriate changes must be done by the database administrator and then the `modify database` command must be run to update the modified parameters in the GDS catalog. Alternatively, you can use the sync database (synchronize database)command for this purpose.

You must connect to the catalog database as a user with the pool administrator privileges, using the connect command before running this command

#### Example

Change the region of databases DB1 and DB3 to EAST.

    GDSCTL> modify database -database db1,db3 -region east

### modify file

Updates the contents of a file in the catalog which can be used by subsequent GDSCTL commands.

#### Syntax

    modify file -file file_name
                -source local_filename

#### Options

Table C-49 GDSCTL modify file Options

| Option                     | Description                                                                                  |
|:---------------------------|:---------------------------------------------------------------------------------------------|
| `-file ``file_name`        | Specify the name of the file object to update.                                               |
| `-source ``local_filename` | Specify an operating system file name specifying a file local to the machine running GDSCTL. |

#### Usage Notes

This command updates a named file object in the catalog by reloading the contents of an operating system file into the catalog.

#### Examples

Update a file named `east_region_db_params` with content from the local source file `/tmp/dbca_params.txt`

    GDSCTL> modify file -file east_region_db_params -source /tmp/dbca_params.txt

### modify gdspool

Modifies the configuration parameters of GDS pools.

#### Syntax

    modify gdspool -gdspool gdspool_name_list
                  [-removeuser user_name | -adduser user_name]

#### Options

Table C-50 GDSCTL modify gdspool Options

| Option                          | Description                                                                                                                                   |
|:--------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------|
| `-adduser ``user_name`          | Specify the user to add to the list of GDS pool administrators. This option grants the pool administrator role to the specified user.         |
| `-gdspool ``database_pool_list` | Specify a comma-delimited list of GDS pool names.                                                                                             |
| `-removeuser ``user_name`       | Specify the user to remove from the list of GDS pool administrators. This option revokes the pool administrator role from the specified user. |

#### Usage Notes

You must connect to the catalog database as a user with the pool administrator privileges, using the connect command before running this command

#### Example

Add PETER to the list of database pool administrators for the pool MYREADERFARM:

    GDSCTL> modify gdspool -gdspool myreaderfarm -adduser peter

### modify gsm

Modifies the configuration parameters of the global service manager. The changes take effect after the global service manager is restarted.

#### Syntax

    modify gsm -gsm gsm_name
              [-catalog connect_id [-pwd password]]
              [-region region_name]
              [-localons ons_port]
              [-remoteons ons_port]
              [-endpoint gmsendpoint [-remote_endpoint remote_endpoint]]
              [-listener listener_port]
              [-wpwd wallet_password]

#### Options

Table C-51 GDSCTL modify gsm Options

| Option                               | Description                                                                                                                                                                                                                                                                              |
|:-------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-catalog ``connect_id`              | Specify the connect identifier for the Global Data Services catalog database. If a network service name is specified, it must be resolvable by the local naming method to a connect descriptor that allows the global service manager being modified to connect to the catalog database. |
| `-endpoint ``gsmendpoint`            | Specify the protocol address that the global services manager listens on for client connection requests. If you use this option, the value you specify overrides the default endpoint.                                                                                                   |
| `-gsm ``gsm_name`                    | Enter the name of the global service manager that you want to modify. If you do not specify a name, then the current global service manager name for the session (specified with the set gsm command) is used.                                                                           |
| `-listener ``listener_port`          | Specify the new listener port.                                                                                                                                                                                                                                                           |
| `-localons ``ons_port`               | Specify the new local ONS port.                                                                                                                                                                                                                                                          |
| `-pwd ``password`                    | Specify the password for the `GSMCATUSER` account. If you do not specify a password, then you are prompted to enter one.                                                                                                                                                                 |
| `-region ``region_name`              | Specify the region to which the global service manager belongs.                                                                                                                                                                                                                          |
| `-remote_endpoint ``remote_endpoint` | Specify the protocol address that is used by the global service manager to receive database registration requests and communicate with other global service managers in the configuration. If you use this option, the value you specify overrides the default endpoint.                 |
| `-remoteons ``ons_port`              | Specify the new remote ONS port.                                                                                                                                                                                                                                                         |
| `-wpwd`                              | Specify the password for the global service manager wallet.                                                                                                                                                                                                                              |

#### Usage Notes

- You must run this command locally on the computer where you want to modify the global service manager.

- This command can be run only by the operating system user who started the global service manager.

- When you run this command, GDSCTL connects to the Global Data Services catalog as the GSMCATUSER user and prompts you for the GSMCATUSER password.

#### Example

Modify the global service manager named `gsm1` so that it is in the EAST region.

    GDSCTL> modify gsm -gsm gsm1 -region east

### modify region

Modifies the configuration parameters for a region.

#### Syntax

    modify region -region region_name_list
                 [-buddy region_name]
                 [-weights weight]

#### Options

Table C-52 GDSCTL modify region Options

| Option                  | Description                                                            |
|:------------------------|:-----------------------------------------------------------------------|
| `-buddy ``region_name`  | Specify the name of the buddy region                                   |
| `-region ``region_list` | Specify a comma-delimited list of region names                         |
| `-weights ``weight`     | Used for static RLB distribution. format: name = value,..,name = value |

#### Usage Notes

You must connect to the catalog database as a user with the Global Data Services administrator privileges, using the connect command before running this command.

To clear buddy region or weight, call `MODIFY REGION` and specify empty quotes as the value. If `WEIGHTS` is specified, dynamic load balancing is replaced by static (not recommended).

#### Example

Modify two regions, EAST and WEST, as follows:

    GDSCTL> modify region -region west -buddy east

### modify service

Modifies the service attributes.

#### Syntax

To add more preferred or available databases to a global service:

    modify service [-gdspool gdspool_name]
                    -service service_name
                   {-preferred db_name_list | -available db_name_list}

To modify the attributes of a global service:

    modify service [-gdspool gdspool_name]
                    -service service_name
                   [-locality {ANYWHERE | LOCAL_ONLY}]
                   [-region_failover]
                   [-role {PRIMARY | PHYSICAL_STANDBY [-failover_primary] |
                           LOGICAL_STANDBY | SNAPSHOT_STANDBY}]
                   [-lag {lag_value | ANY}]
                   [-notification {TRUE | FALSE}]
                   [-rlbgoal {SERVICE_TIME | THROUGHPUT}]
                   [-clbgoal {SHORT | LONG}]
                   [-tafpolicy {BASIC | NONE | PRECONNECT}]
                   [-policy policy]
                   [-failovertype {NONE | SESSION | SELECT | TRANSACTION}]
                   [-failovermethod {NONE | BASIC}]
                   [-dtp {TRUE | FALSE}]
                   [-sql_translation_profile stp_name]
                   [-failoverretry failover_retries]
                   [-failoverdelay failover_delay]
                   [-edition edition_name]
                   [-commit_outcome {TRUE | FALSE}]
                   [-retention retention_seconds]
                   [-session_state {DYNAMIC | STATIC}]
                   [-replay_init_time replay_init_time]]
                   [-table_family family]

To move a global service from one database to another database:

    modify service [-gdspool gdspool_name]
                    -service service_name
                    -old_db db_name
                    -new_db db_name
                   [-force]

To change an available database to a preferred database for a service:

    MODIFY SERVICE [-gdspool gdspool_name]
                    -service service_name
                    -available db_name_list
                    -preferred

To change databases between preferred and available status:

    modify service [-gdspool gdspool_name]
                    -service service_name
                   {-preferred_all |
                    {-modifyconfig -preferred db_name_list [-available db_name_list]}}

To modify properties for a global service that are specific to an Oracle RAC database:

    modify service [-gdspool gdspool_name]
                    -service service_name
                    -database db_name
                   [-server_pool server_pool_name |
                     {-add_instances|-modify_instances} -preferred inst_list
                      -available inst_list |
                      -drop_instances inst_list
                    -cardinality {UNIFORM | SINGLETON}

#### Options

Table C-53 GDSCTL modify service Options

| Option                                                                                                | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-add_instances [-preferred ``comma-delimited-list``] [-available ``comma-delimited-list``]`          | Provides a list of preferred and available instances for the given service on the given database. The provided list over-rides existing assigned instances, if any. Using the –preferred and –available options is optional, but at least one of these must be provided.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `-available ``db_name_list`                                                                           | Specify a comma-delimited list of available databases on which the service runs, if the preferred databases are not available.<br>The list of available instances must be mutually exclusive with the list of preferred instances.<br>If you attempt to add a preferred or available database to a service that was configured with `-preferred_all,` then GDSCTL returns an error.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `-cardinality {UNIFORM | SINGLETON}`                                                                  | Specify the cardinality option for a service running on a policy-managed Oracle RAC database. Services with cardinality set to `UNIFORM` are offered on all database instances. Services with cardinality set to `SINGLETON` are offered on only one database instance.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `-clbgoal {SHORT | LONG}`                                                                             | For connection load balancing goal: set to `SHORT` if using run-time load balancing, set to `LONG` for long running connections such as batch jobs or older SQL\*Forms style.<br>The default value for this option is `SHORT`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `-commit_outcome {TRUE | FALSE}`                                                                      | Enable Transaction Guard; when set to `TRUE`, the commit outcome for a transaction is accessible after the transaction's session fails due to a recoverable outage.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `-database ``db_name`                                                                                 | Specify the name of the database on which you want to modify the service.<br>When `-database` is specified, you must specify exactly one of:<br>• `-server_pool` and/or `-cardinality`. Either is optional, but at least one must appear, both can be used at once.<br>• `-add_instances`, `-modify_instances`, or `-drop_instances`. Exactly one of these three options must be used.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-dtp {TRUE | FALSE}`                                                                                 | Indicates whether Distributed Transaction Processing should be enabled for this service. This ensures that the service is offered at exactly one instance at a time for XA affinity.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `-drop_instances ``inst_list`                                                                         | Provide a list of instances to be removed from the existing assigned instances for a given service on a given database. The provided list of instances will be removed from the existing assigned list.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `-edition ``edition_name`                                                                             | Specify the initial session edition of the service.<br>When an edition is specified for a service, all subsequent connections that specify the service use this edition as the initial session edition. However, if a session connection specifies a different edition, then the edition specified in the session connection is used for the initial session edition.<br>GDSCTL does not validate the specified edition name. During connection, the connect user must have `USE` privilege on the specified edition. If the edition does not exist or if the connect user does not have `USE` privilege on the specified edition, then an error is raised.                                                                                                                                                                                                                                                                                            |
| `-failover_primary`                                                                                   | If you set the `-role` option to `PHYSICAL_STANDBY`, then you can use this option to enable the service for failover to the primary database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `-failoverdelay ``failover_delay`                                                                     | For Application Continuity and TAF, the time delay (in seconds) between reconnect attempts for each incident at failover.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-failovermethod {NONE | BASIC}`                                                                      | TAF failover method (for backward compatibility only).<br>If `failovertype` is set to either `SESSION` or `SELECT`, then choose `BASIC` for this option.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `-failoverretry ``failover_retries`                                                                   | For Application Continuity and TAF, the number of attempts to connect after an incident.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `-failovertype {NONE | SESSION | SELECT | TRANSACTION}`                                               | Specify the failover type.<br>To enable Application Continuity for Java, set this parameter to `TRANSACTION`. To enable Transparent Application Failover (TAF) for OCI, set this parameter to `SELECT` or `SESSION.`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `-force`                                                                                              | If you use this option, then all sessions are disconnected when the service is moved, requiring the sessions using the service to reconnect (potentially to a different instance).<br>If you do not use this option, then the sessions that are connected to a database using this service stay connected, but all new sessions cannot be established to the service.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `-gdspool ``gdspool_name`                                                                             | Specify the name of the database pool to which the service belongs. If not specified and there is only one `gdspool` with access granted to user, it is used as the default `gdspool`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-lag {``lag_value`` | ANY}`                                                                          | Specify the lag for the service in seconds. You can use the keyword `ANY` to indicate that there is no upper threshold on the lag time.<br>The default value for the `-lag` option is `ANY`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `-locality {ANYWHERE | LOCAL_ONLY}`                                                                   | The service region locality. If you do not use this option, then the default value of `ANYWHERE` is used for the service.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-modifyconfig`                                                                                       | Use this option to indicate that you are changing the current list of preferred and available databases for the service. If you use this option, then any databases that are not specified in either the preferred or available list, but were previously assigned, are removed from the list of databases on which the service can run.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `-modify_instances [-preferred ``comma-delimited-list``] [-available ``comma-delimited-list``]`       | The provided `comma-delimited-list` of preferred and available instances is merged with the existing list currently stored in the catalog.<br>If you specify an instance in the `comma-delimited-list` that is not already in the stored list, it is added to the stored list in its correct mode (preferred or available.)<br>If you specify in `comma-delimited-list` an instance that is already in the stored list, then the mode of the instance in the stored list is modified to the provided mode (preferred or available). If the user provided mode is the same as the stored mode, then the mode of the instance will not be changed.<br>Any instances already in the stored list that are not in the provided list remain unchanged in the stored list.<br>Note that an instance cannot be both preferred and available, it can be in one mode only.<br>`–preferred` and `–available` are optional but at least one list must be provided. |
| `-new_db ``database_name`                                                                             | Specify the name of the new database on which the service runs.<br>If you attempt to move a service that was configured with `-preferred_all`, then GDSCTL returns an error.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `-notification {TRUE | FALSE}`                                                                        | Enable Fast Application Notification (FAN) for OCI connections.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `-old_db ``database_name`                                                                             | Specify the name of the old database on which the service runs.<br>If you attempt to move a service that was configured with `-preferred_all`, then GDSCTL returns an error.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `-policy {AUTOMATIC | MANUAL}`                                                                        | Specify the management policy for the service.<br>If you specify `AUTOMATIC` (the default), then the service automatically starts when the database restarts, either by a planned restart or after a failure. Automatic restart is also subject to the service role.<br>If you specify `MANUAL`, then the service is never automatically restarted upon planned restart of the database. A `MANUAL` setting does not prevent the global service manager from monitoring the service when it is running and restarting it if a failure occurs.                                                                                                                                                                                                                                                                                                                                                                                                          |
| `-pdbname ``pdb_name`                                                                                 | Specify the pluggable database name.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `-preferred ``db_name_list`                                                                           | Specify a comma-delimited list of preferred databases on which the service runs. When changing a database from available to preferred, you do not specify a value for the `-preferred` option.<br>The list of preferred instances must be mutually exclusive with the list of available instances.<br>If you attempt to add a preferred or available database to a service that was configured with `-preferred_all`, then GDSCTL returns an error.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `-preferred_all`                                                                                      | Specifies that all the databases in the database pool are preferred databases. Any new databases added to the pool are configured as preferred databases for this service.<br>This option cannot be used with the `-preferred` and `-available` options.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `-region_failover`                                                                                    | Indicates that the service is enabled for region failover. You can only use this option when you specify `LOCAL_ONLY` for the `-locality` option.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `-replay_init_time ``replay_init_time`                                                                | For Application Continuity, this parameter specifies the time (in seconds) after which replay is not initiated. Default value is 300 seconds.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `-retention ``retention_seconds`                                                                      | For Transaction Guard (`commit_outcome` set to `TRUE`), this parameter determines the amount of time (in seconds) that the commit outcome is retained in the database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-rlbgoal {SERVICE_TIME | THROUGHPUT}`                                                                | Run-time Load Balancing Goal. Set this parameter to `SERVICE_TIME` to balance connections by response time. Set this parameter to `THROUGHPUT` to balance connections by throughput.<br>If you do not use this option, then the value defaults to `SERVICE_TIME` for the run-time load balancing goal.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `-role {[PRIMARY] | [PHYSICAL_STANDBY] [-failover_primary] | [LOGICAL_STANDBY] | [SNAPSHOT_STANDBY]}` | Specify the database role that the database must be for this service to start on that database. This applies only to database pools that contain an Oracle Data Guard broker configuration.<br>See Also: [Oracle Data Guard Concepts and Administration](../sbydb/introduction-to-oracle-data-guard-concepts.md) for more information about database roles                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `-server_pool ``server_pool_name`                                                                     | Specify the name of the Oracle RAC server pool in the GDS pool database to which the service belongs (for a policy-managed Oracle RAC database).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `-service ``service_name`                                                                             | Specify the name of the global service.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `-session_state {DYNAMIC | STATIC}`                                                                   | For Application Continuity, this parameter specifies whether the session state that is not transactional is changed by the application. A value of `DYNAMIC` is recommended for most applications.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-sql_translation_profile ``stp_name`                                                                 | Use this option to specify a SQL translation profile for a service that you are adding after you have migrated applications from a non-Oracle database to an Oracle database.<br>This option corresponds to the SQL translation profile parameter in the `DBMS_SERVICE` service attribute.<br>Notes:<br>• Before using the SQL translation feature, you must migrate all server-side application objects and data to the Oracle database.<br>• Use the config service command to display the SQL translation profile.<br>See Also: [Oracle Database SQL Translation and Migration Guide](../drdaa/SQL-translation-framework-overview.md) for more information about SQL translation                                                                                                                                                                                                                                                                    |
| `-table_family``family`                                                                               | Specifies the table family name as a property of the service. This parameter takes one of the table family values (root table schema.name) as shown in the `CONFIG TABLE FAMILY` output.<br>If the schema name or the table name is case-sensitive, use two-level quotes (single quotes outside, double quotes inside) around the whole string, for example, '"TESTUSER1.Customers6"'. No quotes are needed if neither name is case sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `-tafpolicy {BASIC | NONE }`                                                                          | TAF policy specification (for administrator-managed databases only).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |

#### Usage Notes

You must connect to the catalog database as a user with the pool administrator privileges, using the connect command before running this command.

Use this command to:

- Add databases to the preferred or available lists for the service

- Move a service from one database to another database

- Change an available database to a preferred database or a preferred database to an available database

- Modify the high availability attributes of the service

If you want to temporarily move a service from one database to a different database, then use the relocate service command.

#### Examples

Add the database DB3 as a preferred database for the service G_SALES_REPORT in the database pool MYREADERFARM.

    GDSCTL> modify service -gdspool myreaderfarm -service g_sales_report -preferred db3

Modify the service G_DAILY_SALES_REPT in the database pool MYREADERFARM to change the run-time load balancing goal to THROUGHPUT.

    GDSCTL> modify service -gdspool myreaderfarm -service g_daily_sales_rept
      -rlbgoal THROUGHPUT

Move the service G_SALES_REPORT in the database pool MYREADERFARM from the database DB1 to DB4.

    GDSCTL> modify service -gdspool myreaderfarm -service g_sales_report
      -old_db db1 -new_db db4

Upgrade the DB3 database from an available database to a preferred database for the service G_SALES_REPORT in the database pool READFARM.

    GDSCTL> modify service -gdspool readfarm -service g_sales_report
      -available db3 -preferred

Assume the service G_SALES_REPORT currently has the databases DB1 and DB2 assigned as preferred databases, and the database DB3 assigned as an available database. Exchange the preferred and available databases DB1 and DB3, and remove the DB2 database for the service SALES_REPORT in the database pool READFARM.

    GDSCTL> modify service -gdspool readfarm -service g_sales_report -modifyconfig
      -available db3 -preferred db1

Modify the properties of the service G_SALES_REPORT in the database pool READFARM to specify that it should run only in the server pool named SALESPOOL for the policy-managed Oracle RAC database DB1.

    GDSCTL> modify service -gdspool readfarm -service g_sales_report -database db1
    -server_pool salespool

Supply the preferred and available instances for the given service on the given database.

    GDSCTL> modify service –gdspool mypool –service mysvc –database mydb –add_instances
     –preferred inst1,inst2 –available inst3,inst4

In a system-managed sharded database, the table family ID parameter is specified as a property of the service.

    GDSCTL> modify service –GDSPOOL shdpool –table_family sales.customer -service sales

**See Also:**

[Modifying Global Service Attributes](global-data-services-admin.md)

### modify shard

Modify shard attributes.

#### Syntax

    modify shard -shard shname_list
                [-region region_name]
                [-connect connect_identifier]
                [-pwd password]
                [-scan scan_address [-ons port]]
                [-savename]
                [-cpu_threshold cpu]
                [-disk_threshold disk]
                [-destination destination_name]
                [-credential credential_name |
                 [[-osaccount account_name]
                  [-ospassword password]
                  [-windows_domain domain_name]]]

#### Options

Table C-54 GDSCTL modify shard Options

| Option                            | Description                                                                                                                                                                                   |
|:----------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-connect ``connect_identifier`   | Specify an Oracle Net connect descriptor or a net service name that maps to a connect descriptor for the database that is being modified.                                                     |
| `-cpu_threshold ``cpu`            | Specifies CPU Utilization percentage threshold.                                                                                                                                               |
| `-credential ``credential_name`   | Specify the credential to use on the remote machine which specifies the user name and password under which database creation will occur.                                                      |
| `-destination ``destination_name` | Specify the name of the remote executable agent through which the database will be created.                                                                                                   |
| `-disk_threshold ``disk`          | Specifies the average latency in milliseconds of a synchronous single-block read.                                                                                                             |
| `-ons ``port`                     | Specify the ONS port.                                                                                                                                                                         |
| `-osaccount ``account_name`       | Specify the operating system account which will be used for remote jobs.                                                                                                                      |
| `-ospassword ``password`          | Specify the corresponding password for the account specified in `-osaccount`.                                                                                                                 |
| `-pwd ``password`                 | Specify the password for the GSMUSER.                                                                                                                                                         |
| `-region ``region_name`           | Specify the region to which the databases belong.                                                                                                                                             |
| `-savename`                       | Specify this option to store a net service name specified with the` -connect` option in the Global Data Services catalog, rather than the connect descriptor mapped to that net service name. |
| `-scan ``scan_address`            | Specify the SCAN address for a cluster.                                                                                                                                                       |
| `-shard ``shname_list`` `         | Specify a comma-delimited list of shard names.                                                                                                                                                |
| `-windows_domain ``domain_name`   | Specify the corresponding domain name if a Windows account has been specified in `-osaccount`.                                                                                                |

#### Usage Notes

The `REGION` parameter cannot be modified for a shard that belongs to a shardgroup. The modification has to be done at the shardgroup level.

The `DESTINATION` and `CREDENTIAL` parameters are only modifiable when the shard has not yet been deployed, since these parameters only have meaning for the deployment process and are no longer referenced once deployment has completed successfully.

#### Examples

    GDSCTL> modify shard -shard shard1 -ons 23222

### modify shardgroup

Modify shardgroup attributes.

#### Syntax

    modify shardgroup -shardgroup shardgroup_name
                     [-region region_name]
                     [-shardspace shardspace_name]
                     [-repfactor number]
                     [-deploy_as {PRIMARY | STANDBY | ACTIVE_STANDBY}]

#### Options

Table C-55 GDSCTL modify shardgroup Options

| Option                                            | Description                                                                                        |
|:--------------------------------------------------|:---------------------------------------------------------------------------------------------------|
| `-shardgroup ``shardgroup_name`                   | Specify the name of the shardgroup to be modified.                                                 |
| `-region ``region_name`                           | Specify the region the shardgroup resides in.                                                      |
| `-shardspace ``shardspace_name`                   | Specify the shardspace this shardgroup belongs to.                                                 |
| `-repfactor ``number`                             | Specify the number of replicas for each piece of data stored in this shardgroup.                   |
| `-deploy_as {PRIMARY | STANDBY | ACTIVE_STANDBY}` | Specify the initial role for a newly deployed database: `PRIMARY`, `STANDBY`, or `ACTIVE_STANDBY`. |

#### Usage Notes

All shardgroup attributes, except for `DEPLOY_AS`, can only be modified when the shardgroup does not contain any deployed shards. `DEPLOY_AS` can be modified at any time because it does not affect shards that were already added to the shardgroup.

#### Examples

Modify the GROUP1 shardgroup to have a replication factor of 3.

    GDSCTL> modify SHARDGROUP –SHARDGROUP group1 –REPFACTOR 3

### modify shardspace

Modify shardspace parameters.

#### Syntax

    modify shardspace –shardspace shardspace_name
                     [-chunks number]
                     [-protectmode dg_protection_mode]

#### Options

Table C-56 GDSCTL modify shardspace Options

| Option                              | Description                                                                                                                                                                        |
|:------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-shardspace ``shardspace_name`     | Specify the name of the shardspace to be modified.                                                                                                                                 |
| `-chunks ``number`                  | Specify the number of chunks in the shardspace.                                                                                                                                    |
| `-protectmode ``dg_protection_mode` | Specify the Data Guard Protection mode: `MAXPROTECTION`, `MAXAVAILABILITY`, or `MAXPERFORMANCE`. This option can only be executed where Data Guard replication technology is used. |

#### Usage Notes

The number of chunks can only be modified if a shardspace does not contain deployed shards.

#### Examples

Modify the GOLD shardspace to have 6000 chunks.

    GDSCTL> modify shardspace –shardspace gold –chunks 6000

### move chunk

Moves a listed set of chunks from one shard to another shard or multiple shards.

#### Syntax

    move chunk -chunk {chunk_id_list | ALL}
               -source shard_name
              [-target shard_name]
              [-timeout]
              [-verbose]

#### Options

Table C-57 GDSCTL move chunk Options

| Option                             | Description                                                                                                                                                                                                                            |
|:-----------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-chunk {``chunk_id_list`` | ALL}` | Specify a comma-separated list of chunk IDs.<br>If `-chunk ALL` is specified without the `-target` option, all of the chunks are removed from the source shard and distributed to all of the remaining shards in a round-robin manner. |
| `-source ``shard_name`             | Specify the name of the source shard.                                                                                                                                                                                                  |
| `-target ``shard_name`             | Specify the name of the target shard.                                                                                                                                                                                                  |
| `-timeout`                         | Specify a connection retention time-out for the interval between when FAN is sent to the clients and a chunk going into read-only mode or down.                                                                                        |
| `-verbose`                         | Enable verbose output mode.                                                                                                                                                                                                            |

#### Usage Notes

This command can only be used with the system-managed sharding method.

Chunks cannot be moved between shards that belong to different shardgroups.

If `-chunk ALL` is specified without the `-target` option, all of the chunks are removed from the source shard and distributed to all of the remaining shards in a round-robin manner.

#### Examples

Move chunks 3 and 4 from SALE1 to SALE3.

    GDSCTL> move chunk -chunk 3,4 –source sale1 –target sale3

Move all chunks from sale1 and distribute evenly among the remaining shards.

    GDSCTL> move chunk -chunk ALL -source sale1

### quit

Quit GDSCTL utility.

#### Syntax

    quit | exit

### recover shard

Executes all DDL statements on the specified shard (database), starting from the one that was previously executed with errors. The command is intended to perform all skipped DDL changes after database administrator fixes shard issues.

#### Syntax

    recover shard -gdspool pool
                  -shard shard_name
                 [-skip_first|-ignore_first]
                 [-full]

#### Options

Table C-58 GDSCTL recover shard Options

| Option                | Description                                                                                                                    |
|:----------------------|:-------------------------------------------------------------------------------------------------------------------------------|
| `-full`               | Full recovery mode.                                                                                                            |
| `-gdspool ``pool`     | Specify the GDS pool. If not specified and there is only one GDS pool with access granted to user, it will be used by default. |
| `-ignore_first`       | Make first failed DDL statement obsolete.                                                                                      |
| `-shard ``shard_name` | The name of the shard.                                                                                                         |
| `-skip_first`         | Skip the first failed DDL statement.                                                                                           |

#### Usage Notes

Use `SKIP_FIRST` to skip first DDL. This is typically required after manual fix done by database administrator. For example, if `CREATE TABLE` statement fails because of a lack of space, the database administrator fixes the issue and re-executes `CREATE TABLE`. To avoid ORA-39151 (table exists) in `RECOVER SHARD` the database administrator must specify `-SKIP_FIRST`.

Use `IGNORE_FIRST` to mark the first DDL as obsolete. This is required when the wrong DDL statement was specified and failed on all shards. In this case, you need to mark it down as obsolete. `FULL` mode performs a complete recovery, including DDL operations, failed chunk migration, tablespace sets reconstruction, and database parameters.

#### Examples

Recover shard shd1.

    GDSCTL> recover shard -shard shd1

### relocate service

Stops a service on one database and starts the service on a different database.

#### Syntax

    relocate service [-gdspool gdspool_name]
                      -service service_name
                      -old_db db_name
                      -new_db db_name
                     [-force]
                     [-override [-oldpwd oldpassword] [-newpwd newpassword]]

#### Options

Table C-59 GDSCTL relocate service Options

| Option                    | Description                                                                                                                                                                                                                                                                                                                                                       |
|:--------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-force`                  | If you use this option, then all sessions are disconnected when the service is moved, requiring the sessions using the service to reconnect (potentially to a different instance).<br>If you do not use this option, then the sessions that are connected to a database using this service stay connected, but new sessions cannot be established to the service. |
| `-gdspool ``gdspool_name` | Specify the name of the database pool where the service is located. If not specified and there is only one `gdspool` with access granted to user, it is used as the default `gdspool`.                                                                                                                                                                            |
| `-new_db ``db_name`       | Specify the name of the database to which you want to move the service.                                                                                                                                                                                                                                                                                           |
| `-newpwd ``newpassword`   | Specify the password for the GSMUSER in the database to which the service is being relocated (the target database).                                                                                                                                                                                                                                               |
| `-old_db ``db_name`       | Specify the name of the database where the service is currently located.                                                                                                                                                                                                                                                                                          |
| `-oldpwd ``oldpassword`   | Specify the password for the GSMUSER in the source database, or the database where the service is currently located.                                                                                                                                                                                                                                              |
| `-override`               | This option causes the command to execute without updating the global service manager catalog. You can use this option when the catalog database is unavailable.<br>During normal operation, you should not use this option.                                                                                                                                      |
| `-service ``service_name` | Specify the name of the global service you are relocating.                                                                                                                                                                                                                                                                                                        |

#### Usage Notes

Unlike using the modify service command to change the location of a service, this command does not change the underlying configuration. This command temporarily relocates a service to run on another database.

If `-force` is not specified, then the global service must have been started on the old database and not running on the new database prior to command execution. If `-force` is not specified, then sessions already connected to this global service stay connected, but new sessions cannot be established.

If `-override` is specified the command will be executed without going to the GDS catalog. Use this option when the GDS catalog is unavailable. It is not recommended for use under normal operation.

If you attempt to use this command on a service that was previously configured with the `-preferred_all` option, then GDSCTL returns an error.

You must connect to the catalog database as a user with the pool administrator privileges, using the command connect before running this command

#### Example

Relocate the service SALES_REPORT in the READFARM database pool from the DB2 database to the DB3 database.

    GDSCTL> relocate service -gdspool readfarm -service sales_report -old_db db1
     -new_db db3

### remove brokerconfig

Removes an Oracle Data Guard broker configuration from a GDS pool.

#### Syntax

    remove brokerconfig [-gdspool gdspool_name]

#### Options

Table C-60 GDSCTL remove brokerconfig Options

| Syntax                    | Description                                                                                                                                                                                                                        |
|:--------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-gdspool ``gdspool_name` | Specify the GDS pool from which you want to remove the Oracle Data Guard broker configuration (not required, however, if not specified and there is only one GDS pool with access granted to the user, and it is used by default). |

#### Usage Notes

You must connect to the catalog database as a user with the pool administrator privileges, using the command connect before running this command.

If a GDS pool does not contain a Data Guard Broker configuration, an error is returned.

#### Example

Remove the Oracle Data Guard broker configuration from the database pool MYDGPOOL.

    GDSCTL> remove brokerconfig -gdspool myreaderfarm

### remove cdb

Removes one or more CDBs from the shard catalog, but does not destroy it.

#### Syntax

    remove cdb -cdb {cdb_name_list | ALL}
               [-force]

#### Options

Table C-61 GDSCTL remove cdb Options

| Option                            | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|:----------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-cdb {``cdb_name_list`` | ALL} ` | Specify a comma-delimited list of CDB names to remove, or specify `ALL` to remove all CDBs from the catalog.                                                                                                                                                                                                                                                                                                                                                  |
| `-force`                          | Remove one or more specified CDBs, even if they are inaccessible and/or contain PDB shards which may contain chunks. It might result in a lower number of replicas or total unavailability for a certain range of data.<br>**WARNING:**<br>No chunks are moved before removing the CDB which may result in data loss.<br>**WARNING:**<br>Forced removal of a CDB will also cause the removal of all CDBs that are replicas of the CDB being forcibly removed. |

#### Examples

Remove the cdb named cdb1.

    GDSCTL> remove cdb -cdb cdb1

### remove credential

Removes an existing credential.

#### Syntax

    remove credential -credential credential_name

#### Options

Table C-62 GDSCTL remove credential Options

| Option                          | Description                                   |
|:--------------------------------|:----------------------------------------------|
| `-credential ``credential_name` | Specify the name of the credential to remove. |

#### Usage Notes

This command removes an existing credential. When the credential is removed, the catalog may no longer be able to execute jobs on sharded hosts in response to administrative commands.

If the specified credential does not exist, the command returns an error.

#### Examples

Remove a credential named east_region_cred.

    GDSCTL> remove credential –credential east_region_cred

### remove database

Removes databases from a GDS pool.

#### Syntax

    remove database [-gdspool gdspool_name]
                    {-all | -database db_name_list}
                    [-force]

#### Options

Table C-63 GDSCTL remove database Options

| Option                     | Description                                                                                                                                                                                                                                                   |
|:---------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-all`                     | Removes all databases in the database pool.                                                                                                                                                                                                                   |
| `-database ``db_name_list` | Specify a comma-delimited list of database names that you want to remove from the database pool.<br>You cannot specify a database that was added through an Oracle Data Guard broker configuration; you must use Oracle Data Guard to remove these databases. |
| `-gdspool ``gdspool_name`  | Specify the GDS pool name. If not specified, and there is only one GDS pool with access granted to the user, it will be used by default.                                                                                                                      |
| `-force`                   | Removes the database from the catalog even if the database is not available.<br>Using this option can result in global services not being removed from the database.                                                                                          |

#### Usage Notes

You must connect to the catalog database as a user with the pool administrator privileges, using the command connect before running this command.

If a pool already contains a Data Guard Broker configuration, an error is returned because a database must be removed through DGMGRL in this case.

With Oracle Sharding, only an undeployed database can be removed. If a database is offline or inaccessible, it has to be first undeployed with the `-force` option and then removed with the `-force` option.

#### Example

Remove the database DB1 from the global service management configuration.

    GDSCTL> remove database -database db1 -gdspool pool1

### remove file

Removes an existing file object from the catalog.

#### Syntax

    remove file -file file_name

#### Options

Table C-64 GDSCTL remove file Options

| Option              | Description                                                     |
|:--------------------|:----------------------------------------------------------------|
| `-file ``file_name` | Specify the name of the file object to remove from the catalog. |

#### Usage Notes

If the specified file object does not exist, the command returns an error.

#### Examples

Remove a file named `east_region_db_params`.

    GDSCTL> remove file -file east_region_db_params

### remove gdspool

Removes a GDS pool from the current configuration.

#### Syntax

    remove gdspool -gdspool gdspool_name_list

#### Options

Table C-65 GDSCTL remove gdspool Options

| Option                         | Description                                       |
|:-------------------------------|:--------------------------------------------------|
| `-gdspool ``gdspool_name_list` | Specify a comma-delimited list of GDS pool names. |

#### Usage Notes

You must connect to the catalog database as a user with the Global Data Services administrator privileges, using the command connect before running this command.

#### Example

Remove the GDS pools tempreaders and myfarm from the Global Data Services framework.

    GDSCTL> remove gdspool -gdspool tempreaders,myfarm

### remove gsm

Removes a global service manager from the configuration.

#### Syntax

    remove gsm [-gsm gsm_name]

#### Options

Table C-66 GDSCTL remove gsm Options

| Syntax            | Description                                                                                                                                               |
|:------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-gsm ``gsm_name` | Specify the name of the global service manager that you want to remove. If the name is not specified, then the current global service manager is removed. |

#### Usage Notes

The removal of a global service manager requires at least one global service manager to be running to perform cleanup of Global Data Services databases. If there is only one global service manager in the Global Data Services configuration, then it has to be running to be removed.

You must connect to the catalog database as a user with the Global Data Services administrator privileges, using the command connect before running this command.

#### Example

Remove the global service manager named gsm5 from the configuration.

    GDSCTL> remove gsm -gsm gsm5

### remove invitednode (remove invitedsubnet)

Remove host address information from the valid node checking for registration (VNCR) list in the Global Data Services catalog. This command removes either the specified invitednode or all invitednodes that correspond to an alias.

#### Syntax

    remove invitednode {[-group group_name]|vncr_id}

#### Options

Table C-67 GDSCTL remove invitednode (remove invitedsubnet) Options

| Option                | Description                                                                                                                                                                           |
|:----------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-group ``group_name` | Specify an alias which defines a group of VNCRs. This alias can be referenced in other commands related to invited nodes.                                                             |
| `vncr_id`             | The host address information, which can be an IPv4 or IPv6 address, a host name, a netmask, or other identifier for a server. The host address information cannot contain any spaces. |

#### Usage Notes

You must connect to the catalog database as a user with the pool administrator privileges, using the command connect before running this command

#### Examples

Remove the invitednode 198.51.100.22 from the catalog.

    GDSCTL> remove invitednode 198.51.100.22

Remove the VNCR alias group EAST_SRV from the catalog.

    GDSCTL> remove invitednode -group east_srv

### remove region

Removes the specified regions from the global service management framework.

#### Syntax

    remove region -region region_list

#### Options

Table C-68 GDSCTL remove region Options

| Option                  | Description                                    |
|:------------------------|:-----------------------------------------------|
| `-region ``region_list` | Specify a comma-delimited list of region names |

#### Usage Notes

You must connect to the catalog database as a user with the Global Data Services administrator privileges, using the connect command before running this command.

#### Example

Remove the region named SOUTH from the configuration.

    GDSCTL> remove region -region south

### remove service

Removes a service from a database pool.

#### Syntax

    remove service [-gdspool gdspool_name]
                    -service service_name

#### Options

Table C-69 GDSCTL remove service Options

| Option                    | Description                                                                                                                                                                                         |
|:--------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-gdspool ``gdspool_name` | Specify the name of the GDS pool from which you want to remove the service. If not specified and there is only one `gdspool` with access granted to user, then it is used as the default `gdspool`. |
| `-service ``service_name` | Specify the name of the service that you want to remove.                                                                                                                                            |

#### Usage Notes

You must connect to the catalog database as a user with the pool administrator privileges, using the command connect before running this command

#### Example

Remove the service `sales_report` from the database pool MYREADERFARM.

    GDSCTL> remove service -gdspool myreaderfarm -service sales_report

**See Also:**

[Deleting a Global Service](global-data-services-admin.md)

### remove shard

Removes one or more shards from the sharded database.

#### Syntax

    remove shard {-shard {shard_name_list | ALL} |
                     -shardspace shardspace_list |
                     -shardgroup shardgroup_list}
                 [-force]

#### Options

Table C-70 GDSCTL remove shard Options

| Option                               | Description                                                                                                                                                                                                                                                                                                                                                                                                                                |
|:-------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-shard {``shard_name_list`` | ALL}` | Specify a comma-delimited list of shard names to remove, or specify `ALL` to remove all shards from the catalog.                                                                                                                                                                                                                                                                                                                           |
| `-shardspace ``shardspace_list`      | Specify a comma-delimited list of names of shardspaces from which to remove all shards.                                                                                                                                                                                                                                                                                                                                                    |
| `-shardgroup``shardgroup_list`       | Specify a comma-delimited list of names of shardgroups from which to remove all shards.                                                                                                                                                                                                                                                                                                                                                    |
| `-force`                             | Remove one or more specified shards, even if they are inaccessible and/or contain chunks. It might result in a lower number of replicas or total unavailability for a certain range of data.<br>**WARNING:**<br>No chunks are moved before removing the shard which may result in data loss.<br>**WARNING:**<br>Forced removal of a shard will also cause the removal of all shards that are replicas of the shard being forcibly removed. |

#### Examples

Remove the shards from shardgroup GROUP1.

    GDSCTL> remove shard –shardgroup group1

### remove shardgroup

Removes a shardgroup from the shard catalog.

#### Syntax

    remove shardgroup -shardgroup shardgroup_name

#### Options

Table C-71 GDSCTL remove shardgroup Options

| Option                         | Description                                       |
|:-------------------------------|:--------------------------------------------------|
| `-shardgroup``shardgroup_name` | Specify the name of the shardgroup to be removed. |

#### Usage Notes

Only a shardgroup that does not contain any shards can be removed.

#### Examples

Remove the GROUP1 shardgroup.

    GDSCTL> remove shardgroup –shardgroup group1

### remove shardspace

Removes a shardspace from the shard catalog.

#### Syntax

    remove shardspace -shardspace shardspace_name

#### Options

Table C-72 GDSCTL remove shardspace Options

| Option                          | Description                                       |
|:--------------------------------|:--------------------------------------------------|
| `-shardspace ``shardspace_name` | Specify the name of the shardspace to be removed. |

#### Usage Notes

Only a shardspace that does not contain any shards or shardgroups can be removed.

#### Examples

Remove the GOLD shardspace.

    GDSCTL> remove shardspace –shardspace gold

### services

Retrieves information about the services that are registered with the specified global service manager.

#### Syntax

    [status service | services] [-gsm gsm_name]
                                [-service service_name]
                                [-raw | -verbose | -support]

#### Options

Table C-73 GDSCTL services Options

| Option                    | Description                                                                                                                                                                                         |
|:--------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-gsm ``gsm_name`         | Specify the name of a global service manager. If the name is not specified, then GDSCTL uses the current global service manager name for the session (specified with the GDSCTL `set gsm` command). |
| `-raw`                    | If specified, GDSCTL output is presented in a raw, non-parsed format.                                                                                                                               |
| `-service ``service_name` | Specify a fully qualified service name. If the service name is not specified, then the information about all the services registered with the global service manager is retrieved.                  |
| `-support`                | If specified, GDSCTL output displays additional information.                                                                                                                                        |
| `-verbose`                | Enables verbose output mode.                                                                                                                                                                        |

#### Usage Notes

You must run this command on the host where the global service manager for which you want to retrieve service information resides.

You must have the privileges of the user who started the global service manager to run this command.

If `-service` is not specified, then information for all global services is displayed.

#### Example

Display information about the services registered with global service manager `mygsm`:

    GDSCTL> services -gsm mygsm

The `gdsctl services` command returns output similar to the following:

    GDSCTL>services -gsm mygsm
    Service "localsvc.dbpoolora.oradbcloud" has 2 instance(s). Affinity: LOCALPREF
       Instance "dbpoolora%1", name: "gdscat", db: "gdscat", region: "regionora",
     status: ready.
       Instance "dbpoolora%11", name: "gdscat2", db: "gdscat2", region: "regionora",
     status: ready.
    Service "sales_report1.dbpoolora.oradbcloud" has 2 instance(s). Affinity:
     LOCALONLY
       Instance "dbpoolora%1", name: "gdscat", db: "gdscat", region: "regionora",
     status: ready.
       Instance "dbpoolora%11", name: "gdscat2", db: "gdscat2", region: "regionora",
     status: ready.
    Service "sales_report2.dbpoolora.oradbcloud" has 2 instance(s). Affinity: ANYWHERE
       Instance "dbpoolora%1", name: "gdscat", db: "gdscat", region: "regionora",
     status: ready.
       Instance "dbpoolora%11", name: "gdscat2", db: "gdscat2", region: "regionora",
     status: ready.

**Note:**

Affinity values can be `LOCALONLY` when the service locality is defined as `local_only`, `LOCALPREF` when the service locality is defined as `local_only` with the `region_failover` option enabled, and `ANYWHERE` when the service locality is defined as `anywhere`.

Display the status of `mthly_report` service:

    GDSCTL>services -service mthly_report.sales.oradbcloud

Returns output similar to the following:

    Service "mthly_report.sales.oradbcloud" has 1 instance(s). Affinity:
    ANYWHERE
        Instance "sales%1", name: "debug", db: "debug", region: "eastcoast",
    status: ready.

### set gsm

Sets the global service manager for the current session.

This command establishes to which global service manager the successive commands apply. The specified global service manager name is resolved in the `gsm.ora` configuration file.

#### Syntax

    set gsm -gsm gsm_name

#### Options

Table C-74 GDSCTL set gsm Options

| Syntax            | Description                                                                                                                                                                                                        |
|:------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-gsm ``gsm_name` | Specify the name of the global service manager to work with in the current session. If you do not specify a specific global service manager, then GDSCTL uses the default global service manager name of `GSMORA`. |

#### Usage Notes

You must run this command on the host where the global service manager that you want to set for the current session resides.

You must have the privileges of the user who started the global service manager to run this command.

#### Example

Set the global service manager for the current session to `gsm1`.

    GDSCTL> set gsm -gsm gsm1

### set inbound_connect_level

Sets the `INBOUND_CONNECT_LEVEL` listener parameter.

#### Syntax

    set inbound_connect_level [-gsm gsm_name]
                           timeout_value

#### Options

Table C-75 GDSCTL set inbound_connect_level Options

| Option            | Description                                                                                                                                                                                                                                    |
|:------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-gsm ``gsm_name` | Specify the name of the global service manager that you want to start. If you do not specify a specific global service manager, then GDSCTL uses the current global service manager name for the session (specified with the command set gsm). |
| `timeout_value`   | Specify in seconds the connection timeout value.                                                                                                                                                                                               |

#### Usage Notes

- You must run this command on the host where the global service manager for which you want to set the `INBOUND_CONNECT_LEVEL` listener parameter resides

- You must have the privileges of the user who started the global service manager to run this command

#### Example

Set the `INBOUND_CONNECT_LEVEL` listener parameter for `mygsm` to time out in 60 seconds:

    GDSCLTL> set inbound_connect_level -gsm mygsm 60

### set inbound_connect_timeout

Sets the `INBOUND_CONNECT_TIMEOUT` listener parameter.

#### Syntax

    set inbound_connect_timeout timeout_value
                                [-gsm gsm_name]
                                [-save_config | -config_only]

#### Options

Table C-76 GDSCTL set inbound_connect_timeout Options

| Option            | Description                                                                                                                                                                                                                                    |
|:------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-config_only`    | Update GSM.ORA only, without trying to connect to a running global service manager instance.                                                                                                                                                   |
| `-gsm ``gsm_name` | Specify the name of the global service manager that you want to start. If you do not specify a specific global service manager, then GDSCTL uses the current global service manager name for the session (specified with the command set gsm). |
| `-save_config`    | Store configuration changes to GSM.ORA.                                                                                                                                                                                                        |
| `timeout_value`   | Specify in seconds the connection timeout value.                                                                                                                                                                                               |

#### Usage Notes

- You must run this command on the host where the global service manager for which you want to set the `INBOUND_CONNECT_TIMEOUT` listener parameter resides

- You must have the privileges of the user who started the global service manager to run this command

- By default, parameter values changes remain in effect until the global service manager is shut down.

#### Example

Set the `INBOUND_CONNECT_TIMEOUT` listener parameter for `mygsm` to time out in 60 seconds:

    GDSCLTL> set inbound_connect_timeout -gsm mygsm 60

### set log_level

Sets the log level for the listener associated with a specific global service manager.

#### Syntax

    set log_level [-gsm gsm_name]
                  log_level

#### Options

Table C-77 GDSCTL set log_level Options

| Option            | Description                                                                  |
|:------------------|:-----------------------------------------------------------------------------|
| `-gsm ``gsm_name` | Specify the name of the global service manager.                              |
| `log_level`       | Specify the level of detail to write to the log. Valid values are ON or OFF. |

#### Usage Notes

- You must run this command on the host where the global service manager for which you want to set the listener log level resides

- You must have the privileges of the user who started the global service manager to run this command

#### Example

Set logging on for global service manager `mygsm`:

    GDSCTL> set log_level -gsm mygsm ON

### set log_status

Sets the `LOG_STATUS` listener parameter.

#### Syntax

    set log_status ON|OFF
                   [-gsm gsm_name]
                   [-save_config | -config_only]

#### Options

Table C-78 GDSCTL set log_status Options

| Option            | Description                                                                                                                                                                                                                                    |
|:------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ON|OFF`          | Turns listener logging on or off.                                                                                                                                                                                                              |
| `-config_only`    | Update GSM.ORA only, without trying to connect to a running global service manager instance.                                                                                                                                                   |
| `-gsm ``gsm_name` | Specify the name of the global service manager that you want to start. If you do not specify a specific global service manager, then GDSCTL uses the current global service manager name for the session (specified with the command set gsm). |
| `-save_config`    | Store configuration changes to GSM.ORA.                                                                                                                                                                                                        |

#### Usage Notes

- You must run this command on the host where the global service manager for which you want to set the `LOG_STATUS` listener parameter resides

- You must have the privileges of the user who started the global service manager to run this command

- By default, parameter values changes remain in effect until the global service manager is shut down.

#### Example

Set the `LOG_STATUS` listener parameter to ON.

    GDSCLTL> set log_status on -save_config

### set outbound_connect_level

Sets the timeout value for the outbound connections for the listener associated with a specific global service manager.

#### Syntax

    set outbound_connect_level [-gsm gsm_name]
                               timeout_value

#### Options

Table C-79 GDSCTL set outbound_connect_level Options

| Option            | Description                                    |
|:------------------|:-----------------------------------------------|
| `-gsm ``gsm_name` | Specify the name of the global service manager |
| `timeout_value`   | Specify the connection timeout value           |

#### Usage Notes

- You must run this command on the host where the global service manager for which you want to set the timeout value of outbound connections for the listener resides.

- You must have the privileges of the user who started the global service manager to run this command.

#### Example

Set timeout value for all outbound connections:

    GDSCTL> set outbound_connect_level 60

### set outbound_connect_timeout

Sets the `OUTBOUND_CONNECT_TIMEOUT` listener parameter.

#### Syntax

    set outbound_connect_timeout timeout_value
                                [-gsm gsm_name]
                                [-save_config | -config_only]

#### Options

Table C-80 GDSCTL set outbound_connect_timeout Options

| Option            | Description                                                                                                                                                                                                                                    |
|:------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `timeout_value`   | Specify in seconds the connection timeout value.                                                                                                                                                                                               |
| `-config_only`    | Update GSM.ORA only, without trying to connect to a running global service manager instance.                                                                                                                                                   |
| `-gsm ``gsm_name` | Specify the name of the global service manager that you want to start. If you do not specify a specific global service manager, then GDSCTL uses the current global service manager name for the session (specified with the command set gsm). |
| `-save_config`    | Store configuration changes to GSM.ORA.                                                                                                                                                                                                        |

#### Usage Notes

- You must run this command on the host where the global service manager for which you want to set the `OUTBOUND_CONNECT_TIMEOUT` listener parameter resides

- You must have the privileges of the user who started the global service manager to run this command

- By default, parameter values changes remain in effect until the global service manager is shut down.

#### Example

Set the `OUTBOUND_CONNECT_TIMEOUT` listener parameter for `mygsm` to time out in 60 seconds:

    GDSCLTL> set outbound_connect_timeout -gsm mygsm 60

### set trace_level

Sets the trace level for the listener associated with the specified global service manager.

#### Syntax

    set trace_level [-gsm gsm_name]
                    trace_level

#### Options

Table C-81 GDSCTL set trace_level Options

| Option            | Description                                                                                                                                                                                                                                                                                                                                               |
|:------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-gsm ``gsm_name` | Specify the name of the global service manager. If the name is not specified, then GDSCTL uses the current global service manager name for the session (specified with the GDSCTL `set gsm` command).                                                                                                                                                     |
| `trace_level`     | Specify the trace level for the global service manager listener. Valid values are<br>`USER` - provides traces to identify user-induced error conditions<br>`ADMIN` - provides traces to identify installation-specific problems<br>`SUPPORT` - provides trace with troubleshooting information for Oracle Support Services<br>`OFF` - provides no tracing |

#### Usage Notes

- You must run this command on the host where the global service manager for which you want to set the listener trace level resides.

- You must have the privileges of the user who started the global service manager to run this command.

#### Example

Set the trace level for all listeners associated with `mygsm` to ADMIN

    GDSCTL> set trace_level -gsm mygsm ADMIN

### set trc_level

Sets the `TRC_LEVEL` listener parameter.

#### Syntax

    set trc_level trace_level
                  [-gsm gsm_name]
                  [-save_config | -config_only]

#### Options

Table C-82 GDSCTL set trc_level Options

| Option            | Description                                                                                                                                                                                                                                                                                                                               |
|:------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `trace_level`     | Specify the trace level for the global service manager listener. Valid values are<br>USER provides traces to identify user-induced error conditions<br>ADMIN provides traces to identify installation-specific problems<br>SUPPORT provides trace with troubleshooting information for Oracle Support Services<br>OFF provides no tracing |
| `-config_only`    | Update GSM.ORA only, without trying to connect to a running global service manager instance.                                                                                                                                                                                                                                              |
| `-gsm ``gsm_name` | Specify the name of the global service manager that you want to start. If you do not specify a specific global service manager, then GDSCTL uses the current global service manager name for the session (specified with the command set gsm).                                                                                            |
| `-save_config`    | Store configuration changes to GSM.ORA.                                                                                                                                                                                                                                                                                                   |

#### Usage Notes

- You must run this command on the host where the global service manager for which you want to set the `LOG_STATUS` listener parameter resides

- You must have the privileges of the user who started the global service manager to run this command

- By default, parameter values changes remain in effect until the global service manager is shut down.

#### Example

Set the `TRC_LEVEL` listener parameter to SUPPORT.

    GDSCLTL> set trc_level support

### show ddl

Shows DDL statements execution status.

#### Syntax

    show ddl {[-ddl ddl_id] [-count cnt] | [-failed_only]}
              [-support]

#### Options

Table C-83 GDSCTL show ddl Options

| Option          | Description                                                          |
|:----------------|:---------------------------------------------------------------------|
| `-count ``cnt`  | The maximum number of entries to display.                            |
| `-ddl ``ddl_id` | DDL numeric identifier.                                              |
| `-failed_only`  | Use this option to display only errored out statements.              |
| `-support`      | If specified, GDSCTL output displays additional support information. |

#### Usage Notes

If `-DDL` and `-COUNT` are both unspecified, the command returns only the last 10 DDL statements.

If `-DDL` is specified but `-COUNT` is not, the command returns detailed information about the DDL statement. The `-COUNT` option defines the maximum number of DDLs to display.

#### Examples

    GDSCTL> show ddl -count 20

**Note:**

The `show dll` command output might be truncated. You can run `SELECT ddl_text FROM gsmadmin_internal.ddl_requests` on the catalog to see the full text of the statements.

### split chunk

Splits each of the specified chunks into two chunks with an equal number of records. After the split, the chunks remain in the same shard.

#### Syntax

    split chunk -chunk chunk_id_list
               [-shardspace shard_space_list]

#### Options

Table C-84 GDSCTL split chunk Options

| Option                           | Description                                                                |
|:---------------------------------|:---------------------------------------------------------------------------|
| `-chunk ``chunk_id_list`         | Specify a comma-separated list of numeric chunk identifiers.               |
| `-shardspace ``shard_space_list` | Specify a list of shardspace names in which to split the specified chunks. |

#### Usage Notes

This command can only be used with system-managed sharding. For user-defined sharding, `ALTER TABLE` is used to split a partition of the root (parent) table.

Merging of chunks is not supported.

#### Examples

Split chunks 3, 4, and 5.

    GDSCTL> split chunk -chunk 3,4,5

### sql

Executes a SQL statement or a PL/SQL stored procedure against a sharded database.

#### Syntax

    sql "sql_statement"

#### Options

Table C-85 GDSCTL sql Options

| Option          | Description                                                                                                                                |
|:----------------|:-------------------------------------------------------------------------------------------------------------------------------------------|
| `sql_statement` | Enter the SQL statement or PL/SQL stored procedure to be executed. Do not include a semi-colon (;) after the SQL statement to be executed. |

#### Usage Notes

This command can only be executed against a sharded GDS pool. The statements are executed in the GDS catalog database and are then broadcast to all shards in the pool. Since there can be only one sharded pool in a GDS configuration, all SQL statements executed on the catalog database are applied to this pool, if it exists.

Database objects created by this command in the catalog database are used as a schema of the sharded database and are not intended to store user data. The only exception is tables duplicated on all shards (reference tables) – they are populated with data in the catalog database.

SELECT statements are not allowed as the parameter.

The SQL statement or PL/SQL stored procedure to be executed must be enclosed in double quotation marks.

If the string that GDSCTL passes to PL/SQL contains a filename, then the filename must be enclosed in single quotation marks.

Do not include a semi-colon (;) after the SQL statement to be executed.

#### Examples

Using the `gdsctl sql` command.

    GDSCTL> sql “CREATE TABLESPACE SET ts1 IN SHARDGROUP sgr1"

### start gsm

Starts a specific global service manager.

#### Syntax

    start gsm [-gsm gsm_name]

#### Options

Table C-86 GDSCTL start gsm Options

| Option            | Description                                                                                                                                                                                                                                    |
|:------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-gsm ``gsm_name` | Specify the name of the global service manager that you want to start. If you do not specify a specific global service manager, then GDSCTL uses the current global service manager name for the session (specified with the command set gsm). |

#### Usage Notes

- You must run GDSCTL on the same host where the global service manager you want to start is located.

- You must have operating system privileges on the computer where you want to start the global service manager to run this command.

#### Example

Start the global service manager `gsm1` on the local host.

    GDSCTL> start gsm -gsm gsm1

### start observer

Starts specific services.

#### Syntax

    start observer -database db_name
                  [-timeout seconds]

#### Options

Table C-87 GDSCTL start observer Options

| Option                | Description                                             |
|:----------------------|:--------------------------------------------------------|
| `-database ``db_name` | The name of the database.                               |
| `-timeout ``seconds`  | The global service manager requests timeout in seconds. |

#### Usage Notes

`TIMEOUT` (default 15) represents the time between when the shard director/global service manager receives requests and starts the observer. See [Using Oracle Sharding](../shard/sharding-overview.md) for the automatic rules for choosing the right region for the shard director (global service manager) server to start the observer. If shard director servers are not running in this region, the observer is not started.

#### Example

    GDSCTL> start observer -database mydb

### start service

Starts specific services.

#### Syntax

    start service [-gdspool gdspool_name]
                   -service service_name
                 [{-database db_name |
                     -override [-pwd password] -connect connect_identifier}]

#### Options

Table C-88 GDSCTL start service Options

| Option                          | Description                                                                                                                                                                                                              |
|:--------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-database ``db_name`           | Specify the name of the database on which you want to start the service. If you do not specify this option, then GDSCTL starts the services on all preferred databases.                                                  |
| `-connect ``connect_identifier` | Specify an Oracle Net connect descriptor or net service name that resolves to a connect descriptor.                                                                                                                      |
| `-gdspool ``gdspool_name`       | Specify the name of the database pool in which the services that you want to start are located. If not specified and there is only one `gdspool` with access granted to the user, it is used as the default `gdspool`.   |
| `-override`                     | This option causes the command to run without updating the global service manager catalog. You can use this option when the catalog database is unavailable.<br>During normal operation, you should not use this option. |
| `-pwd ``password`               | Specify the password of the GSMUSER in the specified database.                                                                                                                                                           |
| `-service ``service_name`       | Specify a comma-delimited list of global service names. If you do not use this option, then GDSCTL starts all the services in the database pool.                                                                         |

#### Usage Notes

You must connect to the catalog database as a user with the pool administrator privileges, using the command connect before running this command.

Before starting services which run on administrator-managed databases, they must be modified for those databases to stipulate which instances should run the service. Please refer to the `-modify_instances` parameter of the `modify service` command.

#### Example

Start the service `SALES_REPORT`, located in the `READERFARM` database pool.

    GDSCTL> start service -gdspool readerfarm -service sales_report

**See Also:**

[Starting a Global Service](global-data-services-admin.md)

modify service

### status

Displays the running status and runtime information for the global service manager.

#### Syntax

    status [-gsm gsm_name] [-raw|-verbose|-support]

#### Options

Table C-89 GDSCTL status Options

| Option            | Description                                                                                                                                                                                                  |
|:------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-gsm ``gsm_name` | Specify the name of a global service manager to check. If the name is not specified, then GDSCTL uses the current global service manager name for the session (specified with the GDSCTL `set gsm` command). |
| `-raw`            | If specified, GDSCTL output is presented in a raw non-parsed format.                                                                                                                                         |
| `-support`        | If specified, GDSCTL output displays additional information.                                                                                                                                                 |
| `-verbose`        | Enable verbose mode.                                                                                                                                                                                         |

#### Example

    GDSCTL> status

The command returns output similar to the following.

    Alias MYGSM
    Version 19.3.0.0.0
    Start Date 03-JUL-2020 16:48:54
    Trace Level support
    Listener Log File /u01/ORACLE/mygsm/alert/log.xml
    Listener Trace File /u01/ORACLE/mygsm/trace/ora_14816_47568108067776.trc
    Endpoint summary (ADDRESS=(HOST=mymv.us.hq.com)(PORT=1523)(PROTOCOL=tcp))
    GSMOCI Version 0.1.8
    Mastership Y
    Connected to GDS catalog Y
    Process Id 14818
    Number of reconnections 0
    Pending tasks. Total 0
    Tasks in process. Total 0
    Regional Mastership TRUE
    Total messages published 28599
    Time Zone -07:00
    Orphaned Buddy Regions:
    None
    GDS region regionora

### status database

Displays the runtime status of databases, such as registration information, services, and so on.

#### Syntax

    {status database | databases} [-gsm gsm_name]
                                  [-database db_name]
                                  [-gdspool gdspool_name]
                                  [-raw | -support | -verbose]

#### Options

Table C-90 GDSCTL status database Options

| Option                    | Description                                                                                                                                                                                                  |
|:--------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-database ``db_name`     | Specify the name of the database on which to check status                                                                                                                                                    |
| `-gdspool ``gdspool_name` | Specify the name of the database pool. If not specified and there is only one gdspool with access granted to the user, it is used as the default gdspool.                                                    |
| `-gsm ``gsm_name`         | Specify the name of a global service manager to check. If the name is not specified, then GDSCTL uses the current global service manager name for the session (specified with the GDSCTL `set gsm` command). |
| `-raw`                    | If specified, GDSCTL output is presented in a raw, non-parsed format.                                                                                                                                        |
| `-support`                | If specified, GDSCTL output displays additional support information.                                                                                                                                         |
| `-verbose`                | Enable verbose output mode.                                                                                                                                                                                  |

#### Usage Notes

You must connect to the catalog database as a user with the pool administrator privileges, using the command connect before running this command.

This command requires a locally started global service manager. If `-gsm` is not specified for `STATUS DATABASE`, then the currently connected global service manager name is used by default.

#### Example

Display the status of all databases:

    GDSCTL> status database

The `gdsctl status database` command returns output similar to the following:

    Database: "dbcat1" Registered: Y State: Ok ONS: N. Role: PRIMARY Instances: 1
     Region: east

       Service: "sales_svc2" Globally started: N Started: N
                Scan: Y Enabled: Y Preferred: Y
       Service: "sales_svc1" Globally started: Y Started: Y
                Scan: N Enabled: Y Preferred: Y
       Registered instances:
         sales%11
    Database: "dbcat2" Registered: Y State: Ok ONS: N. Role: PRIMARY Instances: 1
     Region: east
       Service: "sales_svc2" Globally started: N Started: N
                Scan: Y Enabled: Y Preferred: Y
       Service: "sales_svc1" Globally started: Y Started: Y
                Scan: N Enabled: Y Preferred: Y
       Registered instances:
         sales%1

### status gsm

Displays the status of a specific global service manager.

#### Syntax

    status (gsm)? [-gsm gsm_name]
                  [-raw | -verbose | -support]

#### Options

Table C-91 GDSCTL status gsm Options

| Option            | Description                                                                                                                                                                                                  |
|:------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-gsm ``gsm_name` | Specify the name of a global service manager to check. If the name is not specified, then GDSCTL uses the current global service manager name for the session (specified with the GDSCTL `set gsm` command). |
| `-raw`            | If specified, GDSCTL output is presented in a raw, non-parsed format.                                                                                                                                        |
| `-support`        | If specified, GDSCTL output displays additional support information.                                                                                                                                         |
| `-verbose`        | Enable verbose output mode.                                                                                                                                                                                  |

#### Usage Notes

You must run GDSCTL on the same host where the global service manager for which you want to display the status is located.

You must have operating system privileges on the computer where you want to display the global service manager status to run this command.

#### Example

Display status of `mygsm`:

    GDSCTL> status gsm -gsm mygsm

The `gdsctl status gsm` command returns output similar to the following:

    Alias MYGSM
    Version 19.3.0.0.0
    Start Date 03-JUL-2020 16:48:54
    Trace Level support
    Listener Log File /u01/ORACLE/mygsm/alert/log.xml
    Listener Trace File /u01/ORACLE/mygsm/trace/ora_14816_47568108067776.trc
    Endpoint summary (ADDRESS=(HOST=mymv.us.hq.com)(PORT=1523)(PROTOCOL=tcp))
    GSMOCI Version 0.1.8
    Mastership Y
    Connected to GDS catalog Y
    Process Id 14818
    Number of reconnections 0
    Pending tasks. Total 0
    Tasks in process. Total 0
    Regional Mastership TRUE
    Total messages published 28599
    Time Zone -07:00
    Orphaned Buddy Regions:
    None
    GDS region regionora

### status service

Displays the status of a specific service.

#### Syntax

    {status service | services} [-gsm gsm_name]
                                [-service service_name]
                                [{-raw|-verbose|-support}]

#### Options

Table C-92 GDSCTL status service Options

| Option                    | Description                                                                                                                                                                                         |
|:--------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-gsm ``gsm_name`         | Specify the name of a global service manager. If the name is not specified, then GDSCTL uses the current global service manager name for the session (specified with the GDSCTL `set gsm` command). |
| `-raw`                    | Used by oracle internal components.                                                                                                                                                                 |
| `-service ``service_name` | Specify a comma-delimited list of global service names. If you do not specify any services, then GDSCTL displays the status of all services in the database pool.                                   |
| `-support`                | Display more detailed information concerning load balancing.                                                                                                                                        |
| `-verbose`                | Display extra information related to load balancing.                                                                                                                                                |

#### Usage Notes

- You must connect to the catalog database as a user with the pool administrator privileges, using the command connect before running this command.

- This command is similar to services.

#### Example

Display the status of service `sales_report1.sales.oradbcloud`:

    GDSCTL> status service -service sales_report1.sales.oradbcloud

The `gdsctl status service` command returns output similar to the following:

    Service "sales_report1.sales.oradbcloud" has 3 instance(s). Affinity: ANYWHERE
       Instance "sales%1", name: "dbcat2", db: "dbcat2", region: "east",
     status: ready.
       Instance "sales%11", name: "dbcat1", db: "dbcat1", region: "west",
     status: ready.
       Instance "sales%31", name: "dbcat3", db: "dbcat3", region: "east",
     status: ready.

### stop gsm

Stops a specific global service manager.

#### Syntax

    stop gsm [-gsm gsm_name]

#### Options

Table C-93 GDSCTL stop gsm Options

| Option            | Description                                                                                                                                                                                                                            |
|:------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-gsm ``gsm_name` | Specify the name of a global service manager you want to stop. If you do not specify a specific global service manager, then GDSCTL uses the current global service manager name for the session (specified with the command set gsm). |

#### Usage Notes

- You must run GDSCTL on the same host where the global service manager that you want to stop is located.

- You must have operating system privileges on the computer where you want to start the global service manager to run this command.

#### Example

Stop the global service manager `gsm1` on the local host.

    GDSCTL> stop gsm -gsm gsm1

### stop service

Stops the specified global services.

#### Syntax

    stop service [-gdspool gdspool_name]
                 [-service service_name_list]
                 [{-database db_name |
                     -override -connect connect_identifier [-pwd password]}]
                 [-force]
                 [-drain_timeout time]
                 [-stop_option {NONE|IMMEDIATE|TRANSACTIONAL}]

#### Options

Table C-94 GDSCTL stop service Options

| Option                          | Description                                                                                                                                                                                                                                                                                                                                                             |
|:--------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-connect ``connect_identifier` | Specify an Oracle Net connect descriptor or net service name that resolves to a connect descriptor for the database (or shard).                                                                                                                                                                                                                                         |
| `-database ``db_name`           | Specify the name of the database on which you want to stop the service. If you do not specify this option, then GDSCTL stops the services on all databases on which the service is currently running.                                                                                                                                                                   |
| `—drain_timeout`                | Set drain time in seconds.                                                                                                                                                                                                                                                                                                                                              |
| `-force`                        | If you use this option, then GDSCTL disconnects all sessions when the service is stopped, requiring the sessions using the service to reconnect (potentially to a different instance).<br>If you do not use this option, then the sessions that are connected to a database using this service remain connected, but new sessions cannot be established to the service. |
| `-gdspool ``gdspool_name`       | Specify the name of the GDS pool in which the service that you want to stop is located. If not specified and there is only one GDS pool with access granted to user, that GDS pool is used as the default GDS pool.                                                                                                                                                     |
| `-override`                     | This option causes the command to execute without updating the global service manager catalog. You can use this option when the catalog database is unavailable.<br>During normal operation, you should not use this option.                                                                                                                                            |
| `-pwd ``password`               | Specify the password of the GSMUSER in the specified database.                                                                                                                                                                                                                                                                                                          |
| `-service ``service_name`       | Specify a comma-delimited list of global service names you want to stop. If you do not use this option, then GDSCTL stops all the services in the database pool.                                                                                                                                                                                                        |
| `—stop_option`                  | Set the default stop option to `NONE`, `IMMEDIATE`, or `TRANSACTIONAL`                                                                                                                                                                                                                                                                                                  |

#### Usage Notes

You must connect to the catalog database as a user with the pool administrator privileges, using the command connect before running this command.

If `-service` is not specified, all global services of GDS pool are stopped.

If `-database` is not specified, the global services are stopped on all of the databases.

If `-force` is specified, all sessions are disconnected, requiring the session using the global service to reconnect (potentially to another instance). If `-force` is not specified, then sessions already connected to this global service stay connected, but new sessions cannot be established to the global service.

If `-override` is specified, the command is executed without connecting to the GDS catalog. Use this option when the GDS catalog is unavailable. It is not recommended for use under normal operation.

#### Example

Stop the service `SALES_REPORT`, on all databases in the database pool `READERFARM`.

    GDSCTL> stop service -gdspool readerfarm -service sales_report

**See Also:**

[Stopping a Global Service](global-data-services-admin.md)

### sync brokerconfig (synchronize brokerconfig)

Synchronizes the Oracle Data Guard broker configuration in the global service manager with the configuration in the database pool. The `synchronize brokerconfig` command has the same options and usage.

#### Syntax

    sync[hronize] brokerconfig [-gdspool gdspool_name]
                               [-database db_name]

#### Options

Table C-95 GDSCTL sync brokerconfig Options

| Option                    | Description                                                                                                                                                                                                                                                                                                                                                                                           |
|:--------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-database ``db_name`     | Specify the name of a database in the database pool to use as a referential database, from which the configuration is queried.<br>If you do not use this option, then GDSCTL uses the primary database as the referential database. If a primary database does not exist in the Oracle Data Guard broker configuration, then GDSCTL uses a random database from the pool as the referential database. |
| `-gdspool ``gdspool_name` | Specify the database pool to which the Oracle Data Guard broker configuration belongs. If not specified and there is only one `gdspool` with access granted to user, that gdspool is used as the default `gdspool`.<br>If the specified database pool does not contain an Oracle Data Guard broker configuration, then GDSCTL returns an error.                                                       |

#### Usage Notes

You must connect to the catalog database as a user with the pool administrator privileges, using the command connect before running this command.

#### Example

Synchronize the Oracle Data Guard broker configuration in the database pool `MYREADERFARM` with the configuration stored in the Global Data Services catalog.

    GDSCTL> sync brokerconfig -gdspool myreaderfarm

### sync database (synchronize database)

Synchronizes attributes of global services and GDS related parameters of a GDS pool database with the contents of the GDS catalog. The `synchronize database` command has the same options and usage.

#### Syntax

    sync[hronize] database [-gdspool gdspool_name]
                           [-database database_name]

#### Options

Table C-96 GDSCTL sync database Options

| Option                      | Description                                                                                                                                                          |
|:----------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-database ``database_name` | Specify the name of a database in the database pool to use as a referential database, from which the configuration is queried.                                       |
| `-gdspool ``gdspool_name`   | Specify the GDS pool to which the database belongs. If not specified and there is only one GDS pool with access granted to user, it is used as the default GDS pool. |

#### Usage Notes

- If database has no GDS region assigned, an error is returned.

- If a GDS pool is specified and the database option is not specified, then each database in the pool is synchronized.

#### Example

Synchronize a database in the default database pool with the database `mydb`.

    GDSCTL> sync database -database mydb

### validate catalog

Cross checks the Global Data Services catalog, global service manager run-time status, and pool databases, and reports inconsistencies and errors.

#### Syntax

    validate [catalog]
             [-gsm gsm_name]
             [ {-config | -database db_name} ]
             [-catpwd cpwd]
             [-dbpwd dpwd]

#### Options

Table C-97 GDSCTL validate catalog Options

| Option                | Description                                                                                                                                                                           |
|:----------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-catpwd ``cpwd`      | Provides the GSMCATUSER password, otherwise it is read from the local wallet file by default.                                                                                         |
| `-config`             | Indicates that the validation should be performed on the Global Data Services catalog configuration only.                                                                             |
| `-database` `db_name` | Indicates the name of the database for which the cross-check validation should be performed.                                                                                          |
| `-dbpwd ``dpwd`       | Provides the pool database password directly if there is only one database in the pool, or if multiple databases in the pool share the same password.                                 |
| `-gsm` `gsm_name`     | Specify the global service manager name. If the name is not specified, then GDSCTL uses the current global service manager name for the session (specified with the command set gsm). |

#### Usage Notes

Because the execution of this command involves accessing all databases in a Global Data Services configuration, the GSMCATUSER password is required run it. The password is stored in the wallet of any global service manager that is part of the Global Data Services configuration. Therefore, if you run the command from the ORACLE_HOME of any of the global service managers, the password is automatically extracted from the wallet and does not have to be provided. Otherwise, you must provide the GSMCATUSER password using the `-catpwd` command option. Alternatively, if all databases in the Global Data Services configuration have the same GSMUSER password, you can specify the password instead of the GSMCATUSER password by using the `-dbpwd` option.

#### Example

Validate the catalog:

    GDSCTL> validate

The output should be similar to the following:

    Validation results:
    VLD2: Region "regionora" does not have buddy region
    VLD11: GDS pool "marketing" does not contain any databases
    VLD12: GDS pool "marketing" does not contain any global services
    VLD11: GDS pool "sales" does not contain any databases
    VLD12: GDS pool "sales" does not contain any global services
    VLD11: GDS pool "mkt" does not contain any databases
    VLD12: GDS pool "mkt" does not contain any global services

### validate

Cross checks the GDS catalog, global service manager run-time status, and databases from the GDS pool and reports any inconsistencies and errors.

#### Syntax

    validate [catalog] [-gsm gsm]
                       [-config | -database db_name [-dbpwd sipwd]]
                       [-catpwd cpwd]

#### Options

Table C-98 GDSCTL validate Options

| Option                | Description                                                          |
|:----------------------|:---------------------------------------------------------------------|
| `-catpwd ``cpwd`      | GSMCATUSER password.                                                 |
| `-config`             | If specified, performs validation of GDS catalog configuration only. |
| `-database ``db_name` | Performs cross-check validation of the specified database.           |
| `-dbpwd ``sipwd`      | GSMUSER password.                                                    |
| `-gsm ``gsm`          | Global service manager name                                          |

#### Usage Notes

If no options are specified, cross-checks are performed on the GDS catalog, database, and local global service manager.

#### Example

    GDSCTL> validate catalog -catpwd cpwd -dbpwd sipwd
