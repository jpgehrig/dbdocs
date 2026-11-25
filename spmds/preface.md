This guide provides a compilation of topics from the Oracle Database user assistance documentation that are collected to help you complete a specific use case scenario.

- Use Case Scenario for this Document
- Documentation Accessibility

### Use Case Scenario for this Document

Use this scenario document to assist you to migrate the same release Oracle Database to a different endian operating system using transportable tablespaces with RMAN.

#### Prerequisites for this Scenario

- Ensure that the source and target databases have identical character sets, or at least that the destination database character set is a superset of the source database.

- Before you run Oracle Data Pump import on the destination server, run the `RMAN CONVERT` command to convert data.

- Run the migration procedures as the `oracle` user.

#### Outline for this Scenario

1.  Migrating Data Using Transportable Tablespaces. Migrate data in preparation for the database migration.

2.  Preparing the Target Server. Create a target database in preparation for the migration.

3.  Converting Data to the Endian Format of the Target Operating System. Convert your tablespaces in preparation for the migration.

4.  Connecting to the Oracle Database with SQL\*Plus.

5.  Migrating Oracle Database. Migrate your database using transportable tablespaces, and complete postmigration tasks.

These steps correspond to the chapters in this document.

**Parent topic:** Preface

### Documentation Accessibility

For information about Oracle's commitment to accessibility, visit the Oracle Accessibility Program website at <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=docacc>.

#### Access to Oracle Support

Oracle customers that have purchased support have access to electronic support through My Oracle Support. For information, visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=info> or visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=trs> if you are hearing impaired.

**Parent topic:** Preface
