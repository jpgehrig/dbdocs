This guide provides a compilation of topics from the Oracle Database user assistance documentation that are collected to help you complete a specific use case scenario.

- Use Case Scenario for this Document
- Documentation Accessibility

### Use Case Scenario for this Document

Use this scenario document to assist you to migrate Oracle Database to new hardware by duplicating an active database to a remote server using RMAN.

While you duplicate the database on your physical standby Oracle Database instance, you do not need to shut down your primary Oracle Database instance. The database remains fully accessible to users while you are performing duplication.

#### Prerequisites for this Scenario

- Ensure that the operating system release and the file system are identical on both the source and destination servers.

- Ensure that you have installed the same release Oracle Database software on the destination server, and that it is updated to the same release update and release revision.

- Ensure that the source and duplicate database files use the same directory structure.

#### Outline for this Scenario

1.  Preparing the Servers and Network for Database duplication. Use RMAN to prepare the servers and network for duplication.

2.  Preparing the Primary Instance on the Source host. Use RMAN to prepare your primary database.

3.  Preparing the Auxiliary Instance on the Destination Host. Complete these procedures to prepare your auxiliary instance for switchover.

4.  Duplicating the Primary Oracle Database Instance. Use `RMAN DUPLICATE`.

5.  Refresh and switchover to the Physical Standby Oracle Database. Complete these procedures to switch over to your auxiliary instance.

These steps correspond to the chapters in this document.

**Parent topic:** Preface

### Documentation Accessibility

For information about Oracle's commitment to accessibility, visit the Oracle Accessibility Program website at <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=docacc>.

#### Access to Oracle Support

Oracle customers that have purchased support have access to electronic support through My Oracle Support. For information, visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=info> or visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=trs> if you are hearing impaired.

**Parent topic:** Preface
