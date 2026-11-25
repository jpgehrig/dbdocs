This guide provides a compilation of topics from the Oracle Database user assistance documentation that are collected to help you complete a specific use case scenario.

- Use Case Scenario for this Document
- Documentation Accessibility

### Use Case Scenario for this Document

Use this scenario document to assist you to migrate Oracle Database to a different endian operating system using transportable tablespaces with RMAN.

#### Prerequisites for this Scenario

- Ensure that the source and target databases have identical character sets, or at least that the destination database's character set is a superset of the source database.

- You place the tablespaces to transport in read-only mode until you complete the transporting process.

- You run the `RMAN CONVERT` command to convert data before you run Data Pump import on the destination server.

- Run the migration procedures as the `oracle` user.

#### Outline for this Scenario

1.  Migrating Data Using Transportable Tablespaces.

2.  Preparing the Target Server. Create your target database in preparation for migrating the database.

3.  Converting Data to the Endian Format of the Target Server.

4.  Connect to the Database with SQL\*Plus.

5.  Migrating the Oracle Database. Migrate your database, and perform postmigration tasks.

These steps correspond to the chapters in this document.

**Parent topic:** Preface

### Documentation Accessibility

For information about Oracle's commitment to accessibility, visit the Oracle Accessibility Program website at <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=docacc>.

#### Access to Oracle Support

Oracle customers that have purchased support have access to electronic support through My Oracle Support. For information, visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=info> or visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=trs> if you are hearing impaired.

**Parent topic:** Preface
