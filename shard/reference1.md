## 13 Oracle Sharding Reference

The following topics provide you with reference information to help you plan, configure, deploy, and manage your Oracle Sharding sharded database configuration.

### Using GDSCTL with Oracle Sharding

Several of the Global Data Services GDSCTL commands are used for setting up and deploying an Oracle Sharding configuration. Learn how to use the GDSCTL command-line tool and the Oracle Sharding-related GDSCTL commands in the following topics.

#### Starting GDSCTL

To start GDSCTL, enter `gdsctl` at the operating system prompt.

    $ gdsctl

GDSCTL starts and displays the GDSCTL command prompt.

    GDSCTL>

#### Running GDSCTL Commands Interactively

You can run GDSCTL commands interactively at either the operating system prompt or the GDSCTL command prompt.

Run a GDSCTL command at the system prompt.

    $ gdsctl add gsm -gsm gsm1 -catalog 127.0.0.1:1521:db1

Run a GDSCTL command at the GDSCTL command prompt.

    GDSCTL> add gsm -gsm gsm1 -catalog 127.0.0.1:1521:db1

Both of these methods achieve the same result. The command syntax examples in this document use the GDSCTL command prompt.

#### Running GDSCTL Batch Operations

You can gather all the GDSCTL commands in one file and run them as a batch with GDSCTL.

The following command starts GDSCTL and runs the commands contained in the specified script file.

    $ gdsctl @script_file_name

#### GDSCTL Help Text

You can display help for GDSCTL and GDSCTL commands.

The GDSCTL `HELP` command displays a summary of all GDSCTL commands.

    GDSCTL> help

If you specify a command name after `HELP`, then the help text for that command is shown.

    GDSCTL> help start gsm

You can also use the `-h` option with any GDSCTL command to show the help text for the specified command.

    GDSCTL> start gsm -h

#### GDSCTL Connections

Some GDSCTL commands require a connection to the shard catalog, and for ceratin operations, GDSCTL must connect to a shard director.

##### GDSCTL Shard Catalog Connections

If you run GDSCTL commands that require a connection to the shard catalog, then you must run the GDSCTL `CONNECT` command before the first command that requires the connection.

The `CONNECT` command only needs to be run once in a GDSCTL session.

GDSCTL uses Oracle Net Services to connect to the shard catalog database or another database in the Oracle Sharding configuration. For these connections you can run GDSCTL from any client or host that has the necessary network configuration.

Unless specified, GDSCTL resolves connect strings with the current name resolution methods (such as TNSNAMES).

The GDSCTL operations that require a connection to a shard catalog are noted in the usage notes for each command.

##### GDSCTL Shard Director Connections

For certain operations, GDSCTL must connect to a shard director, also known as global service manager.

Unless specified, GDSCTL resolves connect strings with the current name resolution methods (such as TNSNAMES). However, to resolve the shard director name, GDSCTL queries the `gsm.ora` file.

To connect to a shard director, GDSCTL must be running on the same host as the shard director. When connecting to a shard director, GDSCTL looks for the `gsm.ora` file associated with the local shard director.

The following are the GDSCTL operations that require a connection to a shard director.

- `ADD GSM` adds a shard director.

- `START GSM` starts the shard director.

- `STOP GSM` stops the shard director.

- `MODIFY GSM` modifies the configuration parameters of the shard director.

- `STATUS GSM` returns the status of a shard director.

- `SET INBOUND_CONNECT_LEVEL` sets the `INBOUND_CONNECT_LEVEL` listener parameter.

- `SET TRACE_LEVEL` sets the trace level for the listener associated with the specified shard director.

- `SET OUTBOUND_CONNECT_LEVEL` sets the timeout value for the outbound connections for the listener associated with a specific shard director.

- `SET LOG_LEVEL` sets the log level for the listener associated with a specific shard director.

#### GDSCTL Commands Used with Oracle Sharding

A subset of GDSCTL commands is used with Oracle Sharding.

- [add cdb](../gsmug/gdsctl-reference.md)

- [add credential](../gsmug/gdsctl-reference.md)

- [add file](../gsmug/gdsctl-reference.md)

- [add gsm](../gsmug/gdsctl-reference.md)

- [add invitednode (add invitedsubnet)](../gsmug/gdsctl-reference.md)

- [add region](../gsmug/gdsctl-reference.md)

- [add service](../gsmug/gdsctl-reference.md)

- [add shard](../gsmug/gdsctl-reference.md)

- [add shardgroup](../gsmug/gdsctl-reference.md)

- [add shardspace](../gsmug/gdsctl-reference.md)

- [config](../gsmug/gdsctl-reference.md)

- [config cdb](../gsmug/gdsctl-reference.md)

- [config chunks](../gsmug/gdsctl-reference.md)

- [config credential](../gsmug/gdsctl-reference.md)

- [config file](../gsmug/gdsctl-reference.md)

- [config gsm](../gsmug/gdsctl-reference.md)

- [config region](../gsmug/gdsctl-reference.md)

- [config sdb](../gsmug/gdsctl-reference.md)

- [config service](../gsmug/gdsctl-reference.md)

- [config shard](../gsmug/gdsctl-reference.md)

- [config shardgroup](../gsmug/gdsctl-reference.md)

- [config shardspace](../gsmug/gdsctl-reference.md)

- [config table family](../gsmug/gdsctl-reference.md)

- [config vncr](../gsmug/gdsctl-reference.md)

- [configure](../gsmug/gdsctl-reference.md)

- [connect](../gsmug/gdsctl-reference.md)

- [create shard](../gsmug/gdsctl-reference.md)

- [create shardcatalog](../gsmug/gdsctl-reference.md)

- [delete catalog](../gsmug/gdsctl-reference.md)

- [deploy](../gsmug/gdsctl-reference.md)

- [disable service](../gsmug/gdsctl-reference.md)

- [enable service](../gsmug/gdsctl-reference.md)

- [modify catalog](../gsmug/gdsctl-reference.md)

- [modify cdb](../gsmug/gdsctl-reference.md)

- [modify credential](../gsmug/gdsctl-reference.md)

- [modify file](../gsmug/gdsctl-reference.md)

- [modify gsm](../gsmug/gdsctl-reference.md)

- [modify region](../gsmug/gdsctl-reference.md)

- [modify service](../gsmug/gdsctl-reference.md)

- [modify shard](../gsmug/gdsctl-reference.md)

- [modify shardgroup](../gsmug/gdsctl-reference.md)

- [modify shardspace](../gsmug/gdsctl-reference.md)

- [move chunk](../gsmug/gdsctl-reference.md)

- [relocate service](../gsmug/gdsctl-reference.md)

- [remove cdb](../gsmug/gdsctl-reference.md)

- [remove credential](../gsmug/gdsctl-reference.md)

- [remove file](../gsmug/gdsctl-reference.md)

- [remove gsm](../gsmug/gdsctl-reference.md)

- [remove invitednode (remove invitedsubnet)](../gsmug/gdsctl-reference.md)

- [remove region](../gsmug/gdsctl-reference.md)

- [remove service](../gsmug/gdsctl-reference.md)

- [remove shard](../gsmug/gdsctl-reference.md)

- [remove shardgroup](../gsmug/gdsctl-reference.md)

- [remove shardspace](../gsmug/gdsctl-reference.md)

- [services](../gsmug/gdsctl-reference.md)

- [set gsm](../gsmug/gdsctl-reference.md)

- [set inbound_connect_level](../gsmug/gdsctl-reference.md)

- [set log_level](../gsmug/gdsctl-reference.md)

- [set outbound_connect_level](../gsmug/gdsctl-reference.md)

- [set trace_level](../gsmug/gdsctl-reference.md)

- [split chunk](../gsmug/gdsctl-reference.md)

- [sql](../gsmug/gdsctl-reference.md)

- [start gsm](../gsmug/gdsctl-reference.md)

- [start service](../gsmug/gdsctl-reference.md)

- [status gsm](../gsmug/gdsctl-reference.md)

- [status service](../gsmug/gdsctl-reference.md)

- [stop gsm](../gsmug/gdsctl-reference.md)

- [stop service](../gsmug/gdsctl-reference.md)

- [validate catalog](../gsmug/gdsctl-reference.md)
