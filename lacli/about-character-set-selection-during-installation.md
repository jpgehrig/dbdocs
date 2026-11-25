## About Character Set Selection During Installation

Before you create the database, decide the character set that you want to use.

After a database is created, changing its character set is usually very expensive in terms of time and resources. Such operations may require converting all character data by exporting the whole database and importing it back. Therefore, it is important that you carefully select the database character set at installation time.

Oracle Database uses character sets for the following:

- Data stored in SQL character data types (`CHAR`, `VARCHAR2`, `CLOB`, and `LONG`).

- Identifiers such as table names, column names, and PL/SQL variables.

- Stored SQL and PL/SQL source code, including text literals embedded in this code.

Starting with Oracle Database 12c Release 2 (12.2), the default database character set of a database created from the General Purpose/Transaction Processing or the Data Warehousing template is Unicode `AL32UTF8`.

Unicode is the universal character set that supports most of the currently spoken languages of the world. It also supports many historical scripts (alphabets). Unicode is the native encoding of many technologies, including Java, XML, XHTML, ECMAScript, and LDAP. Unicode is ideally suited for databases supporting the Internet and the global economy.

Because `AL32UTF8` is a multibyte character set, database operations on character data may be slightly slower when compared to single-byte database character sets, such as `WE8ISO8859P1` or `WE8MSWIN1252`. Storage space requirements for text in most languages that use characters outside of the ASCII repertoire are higher in `AL32UTF8` compared to legacy character sets supporting the language. English data may require more space only if stored in `CLOB` (character large object) columns. Storage for non-character data types, such as `NUMBER` or `DATE`, does not depend on a character set. The universality and flexibility of Unicode usually outweighs these additional costs.

Consider legacy character sets only when the database needs to support a single group of languages and the use of a legacy character set is critical for fulfilling compatibility, storage, or performance requirements. The database character set to be selected in this case is the character set of most clients connecting to this database.

The database character set of a multitenant container database (CDB) determines which databases can be plugged in later. Ensure that the character set you choose for the CDB is compatible with the database character sets of the databases to be plugged into this CDB. If you use Unicode `AL32UTF8` as your CDB character set, then you can plug in a pluggable database (PDB) in any database character set supported by Oracle Database (with the exception of EBCDIC-based character sets).

**See Also:**

[Oracle Database Globalization Support Guide](../nlspg/choosing-character-set.md) for more information about choosing a database character set for a multitenant container database (CDB)

**Parent topic:** [Installing Oracle Database Client](installing-oracle-database-client.md)
