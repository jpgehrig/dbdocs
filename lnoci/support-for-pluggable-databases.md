The multitenant architecture enables an Oracle database to contain a portable collection of schemas, schema objects, and nonschema objects that appear to an Oracle client as a separate database.

A multitenant container database (CDB) is an Oracle database that includes one or more pluggable databases (PDBs).

OCI clients can connect to a PDB using a service whose pluggable database property has been set to the relevant PDB.

In general, OCI calls behave the same way whether connected to a pluggable database or a normal database. OCI calls and features that require special consideration with a CDB are described in the sections that follow:

- Enhancements on OCI API Calls with Multitenant Container Databases (CDB) in General

- OCI Enhancements for ALTER SESSION SET CONTAINER

- Restrictions on OCI API Calls with Multitenant Container Databases (CDB) in General

- Restrictions on OCI Calls with ALTER SESSION SET CONTAINER

- Restrictions on OCI Calls with ALTER SESSION SWITCH CONTAINER SWITCH SERVICE

**See Also:**

[Oracle Database Administrator’s Guide](../multi/administering-pdbs-with-sql-plus.md) for more information about PDBs and for more details about configuring the services to connect to various PDBs

### 17.1 Enhancements on OCI API Calls with Multitenant Container Databases (CDB) in General

These enhancements are the result of restrictions that are now removed for Oracle Database 12c Release 2 (12.2) and later.

The following enhancements are the result of restrictions that are now removed for Oracle Database 12c Release 2 (12.2) and later.

- Client result cache works with connections to Pluggable Databases.

### 17.2 OCI Enhancements for ALTER SESSION SET CONTAINER

Some OCI restrictions about using the `ALTER SESSION SET CONTAINER` statement are removed.

The client must be Oracle Database Release 12c Release 2 (12.2) to perform these operations. Lower version clients are returned an error if any of the following operations is attempted.

- The `ALTER SESSION SET CONTAINER` statement supports applications that use `TIMESTAMP WITH TIMEZONE` or `TIMESTAMP WITH LOCAL TIMEZONE` data types in OCI. The semantics of these types are preserved when the application switches between pluggable databases having different database time zone settings or different database time zone file version settings.

- The `ALTER SESSION SET CONTAINER` statement supports the use of this command to switch an OCI connection between any two pluggable databases whose character sets are different.

### 17.3 Restrictions on OCI API Calls with Multitenant Container Databases (CDB) in General

Descriptions general restrictions.

- An attempt to logon in `OCI_PRELIM_AUTH` mode when connected to any container other than `CDB$ROOT` will result in an `ORA-24542` error.

- An attempt to issue `OCIDBStartup()` when connected to any container other than `CDB$ROOT` results in an `ORA-24543` error.

- An attempt to issue `OCIDBShutdown()` when connected to any container other than `CDB$ROOT` results in an `ORA-24543` error. When `OCIDBShutdown()` is issued connected to `CDB$ROOT`, it brings down the whole instance.

- OCI Continuous Query Notification (CQN) is not supported with CDB.

- OCI applications linked against a client library older than release 12.1 or higher and connecting to a pluggable database will not be able to utilize Fast Application Notification (FAN) High Availability (HA) functionality when connected as a normal (non-common) user. As a workaround, such applications should connect as a common user. This restriction does not exist for release 12.1 or higher OCI clients.

**See Also:**

- [OCIDBStartup()](connect-authorize-and-initialize-functions.md)

- [OCIDBShutdown()](connect-authorize-and-initialize-functions.md)

### 17.4 Restrictions on OCI Calls with ALTER SESSION SET CONTAINER

Describes specific restrictions.

The `ALTER SESSION SET CONTAINER` statement can be used to switch an OCI connection from one pluggable database to another. However, applications that use the `ALTER SESSION SET CONTAINER` statement to switch between pluggable databases need to ensure that their usage is consistent with the OCI restrictions described as follows.

- The `ALTER SESSION SET CONTAINER` statement is disallowed for OCI migratable sessions (such as sessions created with `OCI_MIGRATE` mode during logon) and the combination results in an `ORA-65135` error.

- The `ALTER SESSION SET CONTAINER` statement is not supported with OCI connection pool (which is the old OCI connection pool API) and the combination results in an `ORA-65135` error.

- The `ALTER SESSION SET CONTAINER` statement is not supported in conjunction with OCI session switching (wherein multiple OCI user handles share the same OCI server handle).

- If the client initially connects to a container with a `EXTENDED MAX_STRING_SIZE` setting, and then within the same session switches to a container (using an `ALTER SESSION SET CONTAINER` statement) with an `STANDARD MAX_STRING_SIZE` setting, then a subsequent `OCIStmtExecute()` call will result in an `ORA-14697` error if an attempt is made to use any bind variables of size greater than 4000 bytes.

- An attempt to fetch from an OCI statement handle using `OCIStmtFetch()` or `OCIStmtFetch2()` in the context of a different container than the one in which it was executed will result in an `ORA-65108` error.

- OCI client result cache is disabled if an `ALTER SESSION SET CONTAINER` statement is done in OCI.

- Fast Application Notification (FAN) and Runtime Connection Load Balancing notifications are not supported for applications that switch connections between pluggable databases using an `ALTER SESSION SET CONTAINER` statement.

- The `ALTER SESSION SET CONTAINER` statement sets the current transaction, if any, to read only and any attempt to perform any of the OCI transaction calls (`OCITransStart()`, `OCITransDetach()`, `OCITransCommit()`, `OCITransRollback()`, `OCITransPrepare()`, `OCITransMultiPrepare()`, `OCITransForget()`) will return an error in the new container. In order to issue any of these calls, you need to switch back to the original container.

- If an `OCISubscriptionUnRegister()` call is attempted in the context of an incorrect container (different from the container on which the corresponding `OCISubscriptionRegister()` call was done), then an `ORA-24950` is returned.

- A `OCIDescribeAny()` call with `OCI_PTYPE_DATABASE` describes the database to which the connection is connected. After an `ALTER SESSION SET CONTAINER` statement is done, if the application wants to see the current database description, the `OCIDescribeAny()` call will need to be reissued.

- Calls to any OCI Any Data, collection, or object functions that are used to manipulate an object from a different container are not supported.

- An `OCIObjectFlush()` call is supported only in the container where the object instance was created with an `OCIObjectNew()` call.

- Oracle recommends that `OCIObjectFlush()` be called prior to switching containers with an `ALTER SESSION SET CONTAINER` statement. Note that an `OCIObjectFlush()` call will start a transaction if one is not already started.

- An `OCIObjectFlush()` call done after switching containers may return an error if a transaction was already started earlier on another container by the same session (either as a result of explicit DMLs or as a result of an `OCIObjectFlush()`call).

- An `OCIObjectFlush()` call only flushes objects dirtied in the context of the container in which the `OCIObjectFlush()` call is issued.

- Various session attributes may change on an `ALTER SESSION SET CONTAINER` statement. If an application caches these attributes, their settings may no longer be the same after an `ALTER SESSION SET CONTAINER` statement. Examples of attributes that can be obtained with an `OCIAttrGet()` call and which can change on an `ALTER SESSION SET CONTAINER` statement include the following:

  - [OCI_ATTR_CURRENT_SCHEMA](handle-and-descriptor-attributes.md)

  - [OCI_ATTR_INITIAL_CLIENT_ROLES](handle-and-descriptor-attributes.md)

  - [OCI_ATTR_EDITION](handle-and-descriptor-attributes.md)

  - [OCI_ATTR_MAX_OPEN_CURSORS](handle-and-descriptor-attributes.md)

**See Also:**

- [Oracle Database SQL Language Reference](../sqlrf/Data-Types.md) for more information about `MAX_STRING_SIZE`

- [OCIStmtExecute()](statement-functions.md)

- [OCIStmtFetch()](deprecated-oci-functions.md) or [OCIStmtFetch2()](statement-functions.md)

- [OCITransStart()](transaction-functions.md), [OCITransDetach()](transaction-functions.md), [OCITransCommit()](transaction-functions.md), [OCITransRollback()](transaction-functions.md), [OCITransPrepare()](transaction-functions.md), [OCITransMultiPrepare()](transaction-functions.md) , [OCITransForget()](transaction-functions.md)

- [OCISubscriptionUnRegister()](streams-advanced-queueing-and-publish-subscribe-functions.md) and [OCISubscriptionRegister()](streams-advanced-queueing-and-publish-subscribe-functions.md)

- [OCIDescribeAny()](bind-define-describe-functions.md)

- [OCIObjectFlush()](oci-flush-or-refresh-functions.md)

- [OCIObjectNew()](oci-miscellaneous-object-functions.md)

- [OCIAttrGet()](handle-and-descriptor-functions.md)

### 17.5 Restrictions on OCI Calls with ALTER SESSION SWITCH CONTAINER SWITCH SERVICE

Describes a restriction on OCI calls with the `ALTER SESSION SWITCH CONTAINER SWITCH SERVICE` statement.

Beginning with Oracle Database 12c Release 2 (12.2), the `ALTER SESSION SWITCH CONTAINER SWITCH SERVICE` statement is added, which may result in a change of service attributes if the new service is configured differently than when connected to the original service. However, OCI will not alter its processing based on the new settings with this statement; instead, it will continue to use the original settings as when connected to the original service. For example, FAN on/off, TAF on/off settings, and so forth will remain the same as when first connected to the original service. This is considered the desired behavior after the switch as the normal use case for the `ALTER SESSION SWITCH CONTAINER SWITCH SERVICE` statement is in a multitenant environment with the same application being in use after the switch.
