This guide provides a compilation of topics from the Oracle Database user assistance documentation that are collected to help you complete a specific use case scenario.

- Use Case Scenario for this Document
- Documentation Accessibility

### Use Case Scenario for this Document

Use this scenario document to assist you to migrate Oracle Database to new hardware by duplicating an active database to a remote server using RMAN. After duplicating the active database, you can then upgrade the database.

While you duplicate the database on your physical standby Oracle Database instance, you do not need to shut down your primary Oracle Database instance. The database remains fully accessible to users while you are performing duplication.

#### Prerequisites for this Scenario

- Ensure that the operating system and the file system are identical on both the source and destination servers.

- Ensure that you have installed the new release Oracle Database software on the destination server.

- Ensure that the source and duplicate database files use the same directory structure.

#### Outline for this Scenario

1.  Migrating and Upgrading Oracle Database. Review migration methods using active database duplication with backup sets.

2.  Preparing the Servers and Network for Database Duplication. Use RMAN to prepare the servers and network for duplication.

3.  Preparing the Primary Instance on the Source Host. Use RMAN to prepare your primary database.

4.  Preparing the Auxiliary Instance on the Destination Host. Complete these procedures to prepare your auxiliary instance for switchover.

5.  Duplicating the Primary Oracle Database Instance. Use `RMAN DUPLICATE`.

6.  Refresh and switchover to the Physical Standby Oracle Database. Complete these procedures to switch over to your auxiliary instance.

7.  Upgrading Oracle Database. Carry out the upgrade on the primary instance.

8.  Post-Upgrade Tasks for Oracle Database. Complete the post-upgrade tasks on the upgraded Oracle Database instance, including testing the upgraded instance in preparation for switching back.

These steps correspond to the chapters in this document.

**Parent topic:** Preface

### Documentation Accessibility

For information about Oracle's commitment to accessibility, visit the Oracle Accessibility Program website at <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=docacc>.

#### Access to Oracle Support

Oracle customers that have purchased support have access to electronic support through My Oracle Support. For information, visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=info> or visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=trs> if you are hearing impaired.

**Parent topic:** Preface
