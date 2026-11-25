## Changes in This Release for Oracle Database Globalization Support Guide

This preface contains:

- Changes in Oracle Database 19c

- Changes in Oracle Database 18c

- Changes in Oracle Database 12c Release 2 (12.2)

- Changes in Oracle Database 12c Release 1 (12.1)

### Changes in Oracle Database 19c

There are no changes in Oracle Database Globalization Support Guide for Oracle Database 19c.

### Changes in Oracle Database 18c

The following are changes in Oracle Database Globalization Support Guide for Oracle Database 18c:

#### New Features

- Support for Unicode 9.0, a major version of the Unicode Standard that supersedes all its previous versions.

  See "[Unicode Support](overview-of-globalization-support.md)".

- You can now partition a table by range, list, or reference independently of the declared collation of the partitioning key column. Before Oracle Database 18c, only the collations `BINARY, USING_NLS_COMP, USING_NLS_SORT,` and `USING_NLS_SORT_CS` were allowed in partitioning keys. Thus, you can now partition a table by character values in a case-insensitive way by declaring a case-insensitive collation for the table partitioning key column.

  See "[Effect of Data-Bound Collation on Other Database Objects](linguistic-sorting-and-matching.md)".

- In Oracle Call Interface (OCI), you can now pass a collation for a bind variable in a query or a DML statement using the value of the `OCI_ATTR_COLLATION_ID` attribute. By setting a collation of a bind variable, you can control the collation used to compare the value of the bind variable in comparison conditions and other SQL operations to which the bind variable is an argument. Controlling the collation with the OCI attribute is preferable over inserting the COLLATE operator into a SQL statement text. The latter increases the risk of introducing a SQL injection issue.

  See "[Collation Derivation](appendix-C-collation-derivation-and-determination-rules-for-SQL-operations.md)".

- The new overloaded functions `VALIDATE_CHARACTER_ENCODING` are added to the PL/SQL package `UTL_I18N` to validate the character encoding of VARCHAR2, NVARCHAR2, CLOB, and NCLOB data.

  See "[GDK for PL/SQL Supplied Packages](oracle-globalization-development-kit.md)".

  See also [Oracle Database PL/SQL Packages and Types Reference](../arpls/UTL_I18N.md).

- Support for additional languages and territories.

  - Additional languages supported in this release:

    `BASQUE, TURKMEN,` and `URDU`.

    See "[Languages](appendix-A-locale-data.md)".

  - Additional territories supported in this release:

    `ANGOLA, ANTIGUA AND BARBUDA, ARUBA, BARBADOS, BOTSWANA, CAYMAN ISLANDS, CURACAO, DOMINICA, DOMINICAN REPUBLIC, GHANA, GRENADA, GUYANA, HAITI, JAMAICA, LIECHTENSTEIN, MACAO, MALAWI, MAURITIUS, MOLDOVA, MOZAMBIQUE, NAMIBIA, SAINT KITTS AND NEVIS, SAINT LUCIA, SIERRA LEONE, SOUTH SUDAN, SURINAME, SWAZILAND, TRINIDAD AND TOBAGO, TURKMENISTAN,` and `ZIMBABWE`.

    See "[Territories](appendix-A-locale-data.md)".

### Changes in Oracle Database 12c Release 2 (12.2)

The following are changes in Oracle Database Globalization Support Guide for Oracle Database 12c Release 2 (12.2).

#### New Features

- Support for Unicode 7.0, a major version of the Unicode Standard that supersedes all previous versions of the standard.

  See "[Unicode Support](overview-of-globalization-support.md)".

- Unicode character set `AL32UTF8` is now used as the default database character set when a database is created using Oracle Universal Installer (OUI) or Oracle Database Configuration Assistant (DBCA). The `AL32UTF8` character set is Oracle's implementation of the industry standard `UTF-8` encoding, which supports most of the written languages of the world. Making the `AL32UTF8` character set the default character set for new database deployments enables the database to support multilingual globalized applications out-of-the-box.

  See "[Enabling Multilingual Support for a Database](supporting-multilingual-databases-with-unicode.md)".

- Support for pluggable databases (PDBs) with different database character sets in a multitenant container database (CDB). In the earlier Oracle Database release, it was mandatory to have the same database character set for all the PDBs in a CDB.

  See "[Choosing a Database Character Set for a Multitenant Container Database](choosing-character-set.md)".

- The column-level collation feature allows you to declare character comparison rules on the column level. The collation declared for a column is automatically applied to all the collation-sensitive SQL operations referencing that column. This enables applications to consistently apply language-specific comparison rules to exactly the data that needs these rules. Implementing this feature simplifies application migration to Oracle Database from non-Oracle database systems that support column-level collation declaration.

  See "[Column-Level Collation and Case Sensitivity](linguistic-sorting-and-matching.md)".

  The column-level collation feature also allows you to declare a case-insensitive collation for a table or a schema, so that all the columns in a table or a schema can be always compared in a case-insensitive way. Thus, using this feature, you can now easily create the whole database as a case-insensitive database.

  See "[Case-Insensitive Database](linguistic-sorting-and-matching.md)".

#### Deprecated Features

- The Unicode Collation Algorithm (UCA) 6.1 collations (UCA0610\_\*) are deprecated in this release. They can be desupported and unavailable in a future release. Oracle recommends the use of UCA 7.0 collations (UCA0700\_\*) instead.

  See [Table A-17](appendix-A-locale-data.md) for the list of UCA collations supported in this release.

### Changes in Oracle Database 12c Release 1 (12.1)

The following are changes in Oracle Database Globalization Support Guide for Oracle Database 12c Release 1 (12.1).

#### New Features

- Support for Unicode 6.2, a major version of the Unicode Standard that supersedes all previous versions of the standard.

- Support for new locales.

  See "[Locale Data](appendix-A-locale-data.md)".

- Support for the Unicode Collation Algorithm

  See "[Linguistic Sorting and Matching](linguistic-sorting-and-matching.md)".

- The Database Migration Assistant for Unicode (DMU)

  The Database Migration Assistant for Unicode (DMU) is an intuitive and user-friendly GUI product that helps you streamline the migration process through an interface that minimizes the manual workload and ensures that the migration tasks are carried out correctly and efficiently. It replaces the `CSSCAN` and `CSALTER` utilities as the supported method for migrating databases to Unicode.

  See "[Migrating Character Data Using the Database Migration Assistant for Unicode](character-set-migration.md)" and [Oracle Database Migration Assistant for Unicode Guide ](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/nlspg&id=DUMAG-GUID-96C372DD-84BE-4DF6-8305-5F23F23396E1)for more details.

#### Desupported Features

Some features previously described in this document (the `CSSCAN` and `CSALTER` utilities) are desupported in Oracle Database 12c Release 1 (12.1). See [Oracle Database Upgrade Guide](../upgrd/index.md) for a list of desupported features.
