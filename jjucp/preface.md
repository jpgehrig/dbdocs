The Oracle Universal Connection Pool (UCP) is a full-featured connection pool for managing database connections. Java applications that are database-intensive, use the connection pool to improve performance and better utilize system resources.

The instructions in this guide detail how to use the UCP API and cover a wide range of use cases. The guide does not provide detailed information about using Oracle JDBC Drivers, Oracle Database, or SQL except as required to understand UCP.

### Audience

This guide is primarily written for Application Developers and System Architects who want to learn how to use UCP to create and manage database connections for their Java applications. Users must be familiar with Java and JDBC to use this guide. Knowledge of Oracle Database concepts (such as Oracle RAC and ONS) is required when using some UCP features.

### Documentation Accessibility

For information about Oracle's commitment to accessibility, visit the Oracle Accessibility Program website at <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=docacc>.

#### Access to Oracle Support

Oracle customers that have purchased support have access to electronic support through My Oracle Support. For information, visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=info> or visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=trs> if you are hearing impaired.

### Related Documents

For more information about using Java with the Oracle Database, see the following documents in the Oracle Database documentation set:

- [Oracle Database JDBC Developer's Guide](../jjdbc/index.md)

- [Oracle Database 2 Day + Java Developer's Guide](../tdpjd/index.md)

- [Oracle Database Java Developer's Guide](../jjdev/index.md)

### Conventions

The following text conventions are used in this document:

| Convention  | Meaning                                                                                                                                |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------|
| boldface    | Boldface type indicates graphical user interface elements associated with an action, or terms defined in text or the glossary.         |
| italic      | Italic type indicates book titles, emphasis, or placeholder variables for which you supply particular values.                          |
| `monospace` | Monospace type indicates commands within a paragraph, URLs, code in examples, text that appears on the screen, or text that you enter. |
