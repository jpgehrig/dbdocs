This guide provides a compilation of topics from the Oracle Database user assistance documentation that are collected to help you complete a specific use case scenario.

- Use Case Scenario for this Document
- Documentation Accessibility

### Use Case Scenario for this Document

Use this scenario document to assist you to convert an earlier release non-CDB to a PDB, running on a different endian operating system. After that conversion, you can then plug that PDB into Oracle Database 19c.

This scenario applies to the following non-CDBs:

- Oracle Database 11g Release 2 (11.2.0.3)

- Oracle Database 11g Release 2 (11.2.0.4)

- Oracle Database 12c Release 1 (12.1.0.1)

- Oracle Database 12c Release 1 (12.1.0.2)

- Oracle Database 12c Release 2 (12.2.0.1)

#### Prerequisites for this Scenario

- The source non-CDB and the target CDB host must use compatible character sets and national character sets.

- You have created and configured Oracle Database 19c on the target CDB host, using the multitenant architecture as your configuration option, so that you have a CDB and a default PDB.

- You are prepared to place your user-defined tablespaces on the source non-CDB into read-only mode.

#### Outline for this Scenario

1.  Transporting Databases. Transport your database to the new platform

2.  Converting Data to the Endian Format of the Target Operating System. Convert your endian format, and then convert data to the new platform.

3.  Connecting to Oracle Database

4.  Migrating Oracle Database. Migrate the database to the PDB on the target multitenant architecture host.

These steps correspond to the chapters in this document.

**Parent topic:** Preface

### Documentation Accessibility

For information about Oracle's commitment to accessibility, visit the Oracle Accessibility Program website at <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=docacc>.

#### Access to Oracle Support

Oracle customers that have purchased support have access to electronic support through My Oracle Support. For information, visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=info> or visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=trs> if you are hearing impaired.

**Parent topic:** Preface
