This guide provides a compilation of topics from the Oracle Database user assistance documentation that are collected to help you complete a specific use case scenario.

- Use Case Scenario for this Document
- Documentation Accessibility

### Use Case Scenario for this Document

Use this scenario document to assist you to unplug earlier release PDBs, plug them into a later release CDB, and then upgrade the PDBs.

#### Prerequisites for this Scenario

- You have installed the same release Oracle Database software on the destination server, and it is updated to the same release update and release update revision.

- You have completed preparation of the new Oracle home.

- You have run the Pre-Upgrade Information Tool on the PDB.

- The endian format of the source CDB and the target CDB are identical.

- The same set of options are installed on the source CDB and the target CDB.

- The source CDB and the target CDB have compatible character sets and national character sets.

The source CDB and the target CDB can be on the same or different server hardware.

#### Outline for this Scenario

1.  Upgrading Multitenant Architecture Sequentially Using Unplug-Plug. Learn about the unplug-plug method for carrying out PDB upgrades.

2.  Upgrading Pluggable Databases Sequentially. Use these procedures to complete your PDB upgrade:

    1.  Unplug earlier release PDBs from the earlier release CDB.

    2.  Plug in the earlier release PDB to the later release CDB.

    3.  Upgrade the earlier release PDB to the later release CDB.

    4.  Use inclusion or exclusion lists for PDB upgrades.

These steps correspond to the chapters in this document.

**Parent topic:** Preface

### Documentation Accessibility

For information about Oracle's commitment to accessibility, visit the Oracle Accessibility Program website at <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=docacc>.

#### Access to Oracle Support

Oracle customers that have purchased support have access to electronic support through My Oracle Support. For information, visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=info> or visit <http://www.oracle.com/pls/topic/lookup?ctx=acc&id=trs> if you are hearing impaired.

**Parent topic:** Preface
