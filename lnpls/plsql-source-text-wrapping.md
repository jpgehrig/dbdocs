## A PL/SQL Source Text Wrapping

You can wrap the PL/SQL source text for any of these stored PL/SQL units, thereby preventing anyone from displaying that text with the static data dictionary views `*_SOURCE`:

- Package specification

- Package body

- Type specification

- Type body

- Function

- Procedure

**Note:**

Wrapping text is low-assurance security. For high-assurance security, use Oracle Database Vault, described in [Oracle Database Vault Administrator's Guide](../dvadm/introduction-to-oracle-database-vault.md).

A file containing wrapped PL/SQL source text is called a wrapped file. A wrapped file can be moved, backed up, or processed by SQL\*Plus or the Import and Export utilities.

To produce a wrapped file, use either the PL/SQL Wrapper utility or a `DBMS_DDL` subprogram. The PL/SQL Wrapper utility wraps the source text of every wrappable PL/SQL unit created by a specified SQL file. The `DBMS_DDL` subprograms wrap the source text of single dynamically generated wrappable PL/SQL units.

Both the PL/SQL Wrapper utility and `DBMS_DDL` subprograms detect tokenization errors (for example, runaway strings), but not syntax or semantic errors (for example, nonexistent tables or views).

By default, the 12.2 PL/SQL compiler can use wrapped packages that were compiled with the 9.2 PL/SQL compiler. To prevent the 12.2 PL/SQL compiler from using wrapped packages that were compiled with the 9.2 PL/SQL compiler, set the PL/SQL compilation parameter `PERMIT_92_WRAP_FORMAT` to `FALSE`. For more information about `PERMIT_92_WRAP_FORMAT`, see [Oracle Database Reference](../refrn/PERMIT_92_WRAP_FORMAT.md). For more information about PL/SQL compilation parameters, see "[PL/SQL Units and Compilation Parameters](architecture-pl-sql.md)".

### Topics

- [PL/SQL Source Text Wrapping Limitations](pl-sql-source-text-wrapping-limitations.md)

- [PL/SQL Source Text Wrapping Guidelines](pl-sql-source-text-wrapping-guidelines.md)

- [Wrapping PL/SQL Source Text with PL/SQL Wrapper Utility](wrapping-pl-sql-source-text-pl-sql-wrapper-utility.md)

- [Wrapping PL/SQL Source Text with DBMS_DDL Subprograms](wrapping-pl-sql-source-text-dbms_ddl-subprograms.md)
