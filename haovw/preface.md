## Preface

This book introduces you to Oracle best practices for deploying a highly available database environment, and provides best practices for configuring the Oracle MAA reference architectures.

Part 1 provides an overview of high availability and helps you to determine your high availability requirements. It describes the Oracle Database products and features that are designed to support high availability and describes the primary database architectures that can help your business achieve high availability.

Part 2 describes the best practices for configuring a highly available Oracle database, using features provided with Oracle Database, which lets you achieve MAA Bronze reference architecture service levels

Part 3 describes the best practices for configuring a highly available Oracle database using Oracle Data Guard for replication and data protection, which lets you achieve MAA Gold reference architecture service levels.

This preface contains these topics:

- Audience

- Documentation Accessibility

- Related Documents

- Conventions

### Audience

This book is intended for chief technology officers, information technology architects, database administrators, system administrators, network administrators, and application administrators who perform the following tasks:

- Plan data centers

- Implement data center policies

- Maintain high availability systems

- Plan and build high availability solutions

### Documentation Accessibility

For information about Oracle's commitment to accessibility, visit the Oracle Accessibility Program website at [http://www.oracle.com/pls/topic/lookup?ctx=acc&id=docacc](https://docs.oracle.com/pls/topic/lookup?ctx=acc&id=docacc).

#### Access to Oracle Support

Oracle customer access to and use of Oracle support services will be pursuant to the terms and conditions specified in their Oracle order for the applicable services.

### Related Documents

Knowledge of Oracle Database, Oracle RAC, and Data Guard concepts and terminology is required to understand the configuration and implementation details described in this book. For more information, see the Oracle Database documentation set. These books may be of particular interest:

- [Oracle Database Administrator’s Guide](../admin/index.md)

- [Oracle Clusterware Administration and Deployment Guide](../cwadd/index.md)

- [Oracle Real Application Clusters Administration and Deployment Guide](../racad/index.md)

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/index.md)

- [Oracle Data Guard Concepts and Administration](../sbydb/introduction-to-oracle-data-guard-concepts.md)

- [Oracle Database Backup and Recovery User's Guide](../bradv/introduction-backup-recovery.md)

Many books in the documentation set use the sample schemas of the seed database, which is installed by default when you install Oracle Database. See [Oracle Database Sample Schemas](../comsc/index.md) for information about using these schemas.

Also, you can download the Oracle MAA best practice technical briefs at <http://www.oracle.com/goto/maa>.

### Conventions

The following text conventions are used in this document:

| Convention  | Meaning                                                                                                                                |
|:------------|:---------------------------------------------------------------------------------------------------------------------------------------|
| boldface    | Boldface type indicates graphical user interface elements associated with an action, or terms defined in text or the glossary.         |
| italic      | Italic type indicates book titles, emphasis, or placeholder variables for which you supply particular values.                          |
| `monospace` | Monospace type indicates commands within a paragraph, URLs, code in examples, text that appears on the screen, or text that you enter. |
