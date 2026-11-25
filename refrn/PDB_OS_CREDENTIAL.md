## 1.281 PDB_OS_CREDENTIAL

`PDB_OS_CREDENTIAL` determines the identity of the operating system user (OS user) employed when interacting with the operating system from a PDB.

| Property            | Description                                     |
|:--------------------|:------------------------------------------------|
| Parameter type      | String                                          |
| Syntax              | `PDB_OS_CREDENTIAL = `credential                |
| Default value       | None                                            |
| Modifiable          | No                                              |
| Modifiable in a PDB | Yes                                             |
| Basic               | No                                              |
| Oracle RAC          | The same value should be used for all instances |

**Note:**

The Oracle OS user will continue to be used when interacting with the operating system from the root.

The Oracle OS user is usually a highly privileged user, and using the same user for operating system interactions for every PDB is not recommended. Also, using the same OS user for operating system interactions from different PDBs may compromise data belonging to a given PDB.

In contrast, using an OS user described by a credential whose name is specified as a value of the `PDB_OS_CREDENTIAL` parameter helps ensure that operating system interactions are performed as a less powerful user and provides the ability to protect data belonging to one PDB from being accessed by users connected to another PDB. A credential is an object that is created using the `CREATE_CREDENTIAL` procedure for the `DBMS_CREDENTIAL` package.

The operating system interactions that are done as the OS user name specified in the credential include:

- External jobs that do not already have an operating system credential specified

- External table pre-processors

- PL/SQL library executions

This parameter can be specified for all the PDBs in a CDB but the CDB-wide value can be overridden for a specific PDB and can be modified only by a common administrative user with the `EXECUTE` privilege for the `DBMS_CREDENTIAL` PL/SQL package and the `ALTER SYSTEM` system privilege.

If a value is not set for this parameter for a given PDB, the Oracle OS User will continue to be used when interacting with the operating system from that PDB.

**See Also:**

- [Oracle Database Security Guide](../dbseg/configuring-authentication.md) for an example of setting an OS user for a PDB using this parameter

- [Oracle Multitenant Administrator's Guide](../multi/introduction-to-the-multitenant-architecture.md) for conceptual information about CDBs and PDBs

- [Oracle Multitenant Administrator's Guide](../multi/managing-a-multitenant-environment.md) for information about managing CDBs and PDBs

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_CREDENTIAL.md) for information about creating a credential using the `DBMS_CREDENTIAL.CREATE_CREDENTIAL` procedure
