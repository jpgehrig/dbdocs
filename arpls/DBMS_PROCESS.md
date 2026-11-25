## 135 DBMS_PROCESS

The `DBMS_PROCESS` package provides an interface to manage the prespawned servers.

This chapter contains the following topics:

- DBMS_PROCESS Overview

- DBMS_PROCESS Security Model

- Summary of DBMS_PROCESS Subprograms

### 135.1 DBMS_PROCESS Overview

By default, Oracle Database can prespawn foreground processes to improve the performance of client connections.

A prespawned process refers to a process that has been spawned but does not have a session yet. When a user connects to the database or a service process is needed, the process performs further initialization as needed.

To manage foreground processes, use the `DBMS_PROCESS` package. The procedures in this package configure the number of foreground processes for a connection pool, start a connection pool, and stop a connection pool.

**See Also:**

- [Oracle Database Administrator’s Guide](../admin/managing-processes.md) for a detailed description of managing a pre-created processes

- [Oracle Database Reference](../refrn/USE_DEDICATED_BROKER.md) for information about the `USE_DEDICATED_BROKER` parameter, which determines how dedicated servers are spawned. `TRUE` enables the listener to send the connection to a dedicated connection broker that spawns the dedicated server. `FALSE` sets the listener to spawn a dedicated server directly.

### 135.2 DBMS_PROCESS Security Model

You must be granted the `SYSDBA` administrative privilege to use the `DBMS_PROCESS` package.

### 135.3 Summary of DBMS_PROCESS Subprograms

This table lists the `DBMS_PROCESS` subprograms and briefly describes them.

Table 135-1 DBMS_PROCESS Package Subprograms

| Subprogram               | Description                                                                                                                                                                            |
|:-------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| CONFIGURE_POOL Procedure | Configures the minimum number of prespawned processes, the number of prespawned processes in a batch, and the initial number of pre-spawned processes for a foreground connection pool |
| START_POOL Procedure     | Starts a prespawned foreground process pool.                                                                                                                                           |
| STOP_POOL Procediure     | Stops a prespawned foreground process pool.                                                                                                                                            |

#### 135.3.1 CONFIGURE_POOL Procedure

This procedure configures the minimum number of prespawned processes, the number of prespawned processes in a batch, and the initial number of pre-spawned processes for a foreground connection pool.

##### Syntax

    DBMS_PROCESS.CONFIGURE_POOL(
       pool_name       IN  VARCHAR2 DEFAULT "SYS_DEFAULT_FOREGROUND_POOL",
       min_count       IN  NUMBER DEFAULT 10,
       batch_count     IN  NUMBER DEFAULT 20,
       init_count      IN  NUMBER DEFAULT 0);

##### Parameters

Table 135-2 CONFIGURE_POOL Procedure Parameters

| Parameter     | Description                                                                                                                                                                    |
|:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `pool_name`   | Name of the foreground pool                                                                                                                                                    |
| `min_count`   | Count after which a batch of prespawned processes will be spawned in the pool (default 10; maximum number of processes 64,000)                                                 |
| `batch_count` | Batch of prespawned servers to be spawned in the pool (default 20). The total value of the `min_count` and `batch_count` values cannot exceed the `PROCESSES` parameter value. |
| `init_count`  | Set of prespawned servers to be spawned in startup, or before a storm of connections, spawned in batches (default 0). Do not exceed the `PROCESSES` parameter value.           |

##### Exceptions

Table 135-3 CONFIGURE_POOL Procedure Exceptions

| Error     | Description                                 |
|:----------|:--------------------------------------------|
| `ORA-456` | Prespawn not enabled                        |
| `ORA-457` | Prespawn pool not found                     |
| `ORA-458` | Prespawn pool already started               |
| `ORA-459` | Prespawn pool not started                   |
| `ORA-460` | Process pool invalid configuration value(s) |

##### Usage Notes

- To find information about foreground processes, query the `V$PROCESS_POOL` dynamic view.

##### Example

    BEGIN
      DBMS_PROCESS.CONFIGURE_POOL (
       pool_name   => 'hrdb_pool',
       min_count   => 40,
       batch_count => 20,
       init_count  => 10);
    END;
    /

#### 135.3.2 START_POOL Procedure

This procedure starts a prespawned foreground process pool.

##### Syntax

    DBMS_PROCESS.START_POOL(
       pool_name      IN  VARCHAR2 DEFAULT "SYS_DEFAULT_FOREGROUND_POOL");

##### Parameters

Table 135-4 START_POOL Procedure Parameters

| Parameter   | Description                                                                                                  |
|:------------|:-------------------------------------------------------------------------------------------------------------|
| `pool_name` | Name of prespawned foreground process pool. To find existing pools, query the `V$PROCESS_POOL` dynamic view. |

##### Exceptions

Table 135-5 START_POOL Procedure Exceptions

| Error      | Description                   |
|:-----------|:------------------------------|
| `ORA-457 ` | Prespawn pool not found       |
| `ORA-458 ` | Prespawn pool already started |
| `ORA-459 ` | Prespawn pool not started     |

##### Example

    BEGIN
      DBMS_PROCESS.START_POOL (
       pool_name   => 'hrdb_pool',
    END;

#### 135.3.3 STOP_POOL Procedure

This procedure stops a prespawned foreground process pool.

##### Syntax

    DBMS_PROCESS.STOP_POOL(
       pool_name      IN  VARCHAR2 DEFAULT "SYS_DEFAULT_FOREGROUND_POOL");

##### Parameters

Table 135-6 STOP_POOL Procedure Parameters

| Parameter   | Description                                                                                                      |
|:------------|:-----------------------------------------------------------------------------------------------------------------|
| `pool_name` | Name of the prespawned foreground process pool. To find existing pools, query the `V$PROCESS_POOL` dynamic view. |

##### Exceptions

Table 135-7 STOP_POOL Procedure Exceptions

| Error      | Description                   |
|:-----------|:------------------------------|
| `ORA-457 ` | Prespawn pool not found       |
| `ORA-458 ` | Prespawn pool already started |
| `ORA-459 ` | Prespawn pool not started     |

##### Example

    BEGIN
      DBMS_PROCESS.STOP_POOL (
       pool_name   => 'hrdb_pool',
    END;
