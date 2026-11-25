This manual explains the architecture and tasks associated with the Oracle Database In-Memory feature set.

This preface contains the following topics:

### Audience

This document is intended for database administrators who manage an In-Memory Column Store (IM column store), and developers who optimize analytic queries that use Oracle Database In-Memory features.

### Documentation Accessibility

For information about Oracle's commitment to accessibility, visit the Oracle Accessibility Program website at [http://www.oracle.com/pls/topic/lookup?ctx=acc&id=docacc](https://docs.oracle.com/pls/topic/lookup?ctx=acc&id=docacc).

#### Access to Oracle Support

Oracle customers that have purchased support have access to electronic support through My Oracle Support. For information, visit [http://www.oracle.com/pls/topic/lookup?ctx=acc&id=info](https://docs.oracle.com/pls/topic/lookup?ctx=acc&id=info) or visit [http://www.oracle.com/pls/topic/lookup?ctx=acc&id=trs](https://docs.oracle.com/pls/topic/lookup?ctx=acc&id=trs) if you are hearing impaired.

### Related Documents

This manual assumes that you are familiar with [Oracle Database Concepts](../cncpt/introduction-to-oracle-database.md). The following books are frequently referenced:

- [Oracle Database Data Warehousing Guide](../dwhsg/introduction-data-warehouse-concepts.md)

- [Oracle Database VLDB and Partitioning Guide](../vldbg/partition-intro.md)

- [Oracle Database SQL Tuning Guide](../tgsql/introduction-to-sql-tuning.md)

- [Oracle Database SQL Language Reference](../sqlrf/Introduction-to-Oracle-SQL.md)

- [Oracle Database Reference](../refrn/initialization-parameters.md)

Many examples in this book use the sample schemas, which are installed by default when you select the Basic Installation option with an Oracle Database. See [Oracle Database Sample Schemas](../comsc/introduction-to-sample-schemas.md) for information on how these schemas were created and how you can use them.

### Conventions

The following text conventions are used in this document:

| Convention  | Meaning                                                                                                                                |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------|
| boldface    | Boldface type indicates graphical user interface elements associated with an action, or terms defined in text or the glossary.         |
| italic      | Italic type indicates book titles, emphasis, or placeholder variables for which you supply particular values.                          |
| `monospace` | Monospace type indicates commands within a paragraph, URLs, code in examples, text that appears on the screen, or text that you enter. |
