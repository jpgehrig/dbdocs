Several restrictions exist in this Oracle Label Security release.

These restrictions are as follows:

- `CREATE TABLE AS SELECT` restriction

  If you attempt to perform `CREATE` `TABLE` `AS` `SELECT` in a schema that is protected by an Oracle Label Security policy, then the statement will fail.

- Label tag restriction

  Label tags must be unique across the policies in the database. When you use multiple policies in a database, you cannot use the same numeric label tag in different policies.

- Export restriction

  Before Oracle Database 12c release 1 (12.1), the `LBACSYS` schema could not be exported due to the use of opaque types in Oracle Label Security. An export of the entire database (parameter `FULL``=Y`) with Oracle Label Security installed can be done, except that the `LBACSYS` schema would not be exported.

  From Oracle Database release 12c on, this restriction has been removed. See [Full Database Export](performing-dba-functions-under-oracle-label-security.md) for additional details on the database versions that the export can be supported from.

- Oracle Label Security removal restriction

  You cannot remove Oracle Label Security, but you can disable it. See [Disabling Oracle Label Security](disabling-and-enabling-oracle-label-security.md).

- Shared schema support restriction

  User accounts defined in the Oracle Internet Directory cannot be given individual Oracle Label Security authorizations. However, authorizations can be given to the shared schema to which the directory users are mapped.

  The Oracle Label Security function `SET_ACCESS_PROFILE` can be used programmatically to set the label authorization profile to use after a user has been authenticated and mapped to a shared schema. Oracle Label Security does not enforce a mapping between users who are given label authorizations in Oracle Label Security and actual database users.

- Hidden columns restriction

  PL/SQL does not recognize references to hidden columns in tables. A compiler error will be generated.

**Parent topic:** [Appendixes](part4.md)
